# Pipelines

Pipelines (`|>`) are an alternative syntax for function application:

``` cara title="Example"
"Hello there"
|> String.split(" ")
|> List.length
|> #(_ + 1)

// is the same as:

List.length(String.split(" ", "Hello there")) + 1
```

The general form is:

``` cara
value |> function // ==
function(value)

value |> function(initial, arguments) // ==
function(initial, arguments, value)
```

`|>` is left-associative:

``` cara
x |> f1 |> f2    // =
(x |> f1) |> f2  // =
f1(x) |> f2      // =
f2(f1(x))
```

In case you want to provide an argument to a function on a different position than the last, use the [hole shorthand](/reference/anonymous-fns-and-holes/):

``` cara
userInput
|> parseValue
|> #(Dict.member(_, allowedValues)) // pass as a first argument
```
