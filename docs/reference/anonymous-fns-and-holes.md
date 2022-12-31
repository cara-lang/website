# Anonymous functions and holes

Anonymous functions (sometimes called _lambdas_) are a way to create one-off [functions](/reference/fns/).

## Syntax

``` cara title="Anonymous functions (lambdas)"
\x -> 1 + x
\m,v,r -> m * v^2 / r

// Pattern matching
type Name = Name(String)
lowerName = \Name(x) -> String.lower(x)
lowerName(Name("Martin")) // -> "martin"

// Functions as values
isBig = \{size} -> size > 10
isBig({hasBorder: True, size: 5}) // -> False

```

There is also a more concise shorthand syntax that uses _holes_, which can be numbered:

``` cara title="Shorthand"
#(1 + _)       // same as \x -> 1 + x
#(myFn(_3,_1)) // ignores 2nd argument

// Usage in pipelines
1..50
  |> Seq.filter(#(_ % 2 == 0))
  |> Seq.sum
  |> #(Dict.member(_, knownSums))

// Functions as values
inc    = #(_ + 1)
double = #(_ * 2)
val = inc(double(5)) // -> 11
```

!!! tip
    Use the shorthand in situations where:

    * dropping the argument names doesn't hurt the code readability
    * pattern matching is not needed

    Pipelines and higher-order functions like `Seq.filter` are usually a great
    place for it.

## Thunks

It is possible to create 0-argument functions, called _thunks_, with the above syntax:

``` cara title="Thunks"
lambdaThunk    = \ -> isPrime(1111111111111111111)
shorthandThunk = #(someExpensiveComputation(9000))
```

The computation inside will only run once you call the function:

``` cara title="Evaluating a thunk"
result1 = lambdaThunk()    // -> True
result2 = shorthandThunk() // -> whatever someExpensiveComputation returns
```

This is useful for delaying expensive computations: this ocassionally comes up when using functions like `Maybe.withDefault`:

``` cara title="Usage"
/* Imagine we have two ways of arriving at an answer:
   a fast way that doesn't always work, and a slow way that always works.

   findAnswerEasily(Int): Maybe[String]
   fallback(Int):         String
*/

findAnswerEasily(123)
  |> Maybe.withDefault(#(fallback(123)))

/* This now uses the fast path whenever possible but will default to the slow
   path if needed.
*/
```
