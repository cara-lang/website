# Anonymous functions and holes

Anonymous functions (sometimes called _lambdas_) are a way to create one-off [functions](/reference/fns/).

``` cara title="Anonymous functions (lambdas)"
\x -> 1 + x
\m,v,r -> m * v^2 / r

// Pattern matching
type Name = Name(String)
\Name(x) -> String.lower(x)

// Functions as values
isBlue = \{color} -> color == Blue
isBlue({size: 5, color: Red})

```

There is also a more concise syntax called _holes_:

``` cara title="Holes"
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
    Use holes in situations where:

    * dropping the argument names doesn't hurt the code readability
    * pattern matching is not needed

    Pipelines and higher-order functions like `Seq.filter` are usually a great
    place for holes.

