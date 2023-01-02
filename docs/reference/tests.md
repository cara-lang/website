# Tests

Tests are a way to check your code behaves in the ways you expect.

Cara supports unit tests, parameterized tests and property tests (more below).

Tests run during `cara test` invocation; they are skipped during the `cara build`
and `cara run` modes.

Regardless of the test type, each test can optionally be named and needs to
return either `Bool` or `IO[Bool]`. This means you can use the `{...}` and
`IO {...}` [effect blocks](/reference/effect-blocks-and-bang).

The test expression or the last statement needs to return a `Bool`.

You can put your tests next to your definitions or in an extra file: [both
testing
schools](https://softwareengineering.stackexchange.com/questions/166409/tdd-outside-in-vs-inside-out)
are supported.

``` cara title="Anonymous vs named"
test: List.isEmpty([])

test "Unit test": 1 == 2
```

``` cara title="Newlines welcome"
test:
  List.range(1,10)
    |> List.filter(#(_ % 2 == 0))
    |> List.length
    |> #(_ == 5)
```

``` cara title="Statements"
// Statements need a {...} or IO {...} block

test: {
  x = 1..10
  y = 10..1
  x == Seq.reverse(y)
}

test: IO {
  x = 1..10
  IO.println!("I have access to IO!")
  List.max(x) == Just(10)
}
```

## Unit tests

Unit tests run your functions with predefined inputs.

The syntax is `test [NAME]: EXPRESSION`

``` cara
test: 1 == 2
test: List.isEmpty([])
```

## Parameterized tests

Parameterized tests run code against a table of inputs and outputs (a list of
tuples).

The size of the tuples in the table dictates how many arguments the function
will receive:

The syntax is `test [NAME] with TABLE: FUNCTION`:

``` cara
test "Not" with [
  (True, False),
  (False, True),
]:
  \input,output -> !input == output

// Table can be extracted out
additionExamples = [
  (1,0,1),
  (1,1,2),
  (1,5,6),
]
test "Addition" with additionExamples:
  \a,b,sum -> a + b == sum

// Shorthand can be used
test "Addition 2" with additionExamples:
  #(_1 + _2 == _3)
```

## Property tests

Property tests run code against randomized inputs (using the `Gen` type).

The syntax is `test [NAME] with GENERATORS: FUNCTION`, where `GENERATORS` can
be one of the following:

* a tuple of generators (or a single generator)
* a tuple _type_ of the generated types (or just a single type)

With the first one you have control over exactly which generator gets used;
the second one will attempt to use a generator automatically based on the type
name (`Gen.foo` for type `Foo`).

As with parameterized tests, the length of the tuple determines the number of
arguments to the test function.

``` cara
// Single generator (implicit)
test "List length is non-negative" with List[Int]:
  #(List.length(_) >= 0) // will use Gen.list(Gen.int)

// Single generator (explicit)
evenIntGen = Gen.int |> Gen.map(#(_ * 2))
evenIntSetGen = Gen.set(evenIntGen)
test "Mapping a set ~= mapping a list" with evenIntSetGen:
  \set -> {
    fn = #(_ + 1)
    direct = Set.map(fn,set)
    viaList =
      set
        |> Set.toList
        |> List.map(fn)
        |> Set.fromList
    direct == viaList
  }

// Multiple generators (implicit)
test "cons is not empty" with (Int,List[Int]):
  \x,xs -> !List.isEmpty(List.cons(x,xs))

// Multiple generators (explicit)
nonzeroIntGen = Gen.int |> Gen.map(#(if _ == 0 then 1 else _))
test "* and / are inverses" with (Gen.int, nonzeroIntGen):
  \a,b -> a * b / b == a
```
