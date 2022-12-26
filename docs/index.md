# Cara

Cara is a programming language aiming to be pleasant to use and maintain while
staying safe and dependable.

⚠️ _Cara is in development: [@janiczek](https://github.com/Janiczek) is still
figuring out the design, syntax and functionality. In the meantime, some code
snippets can be found in the compiler's [end-to-end test
suite](https://github.com/cara-lang/compiler/tree/main/end-to-end-tests) on
GitHub._

## Features

To put it shortly, Cara is a combination of [Elm](https://elm-lang.org),
[Haskell](https://www.haskell.org) and [Kotlin](https://kotlinlang.org).

Cara very much takes Elm as its starting point, but then adds some advanced
features like GADTs inspired by Haskell, and in syntax it comes closer to
Kotlin than to the ML family.

Here is an incomplete list of Cara's features:

* General-purpose
* Compiled to automatically parallel native code via [HVM](https://github.com/Kindelia/hvm)...
* ...or interpreted (handy for scripting)
* Immutable
* Purely functional
* Statically typed with automatic type inference

## Examples

```
quickSort(List[Int]): List[Int]
quickSort([]) = []
quickSort(x::xs) =
  (lt, gt) = List.partition(x >= _, xs)
  quickSort(lt) ++ x ++ quickSort(gt)

[3,1,2,5,4]
  |> quickSort
  |> IO.inspect!
```

```
fizzbuzz(n) =
  if n % 15 == 0 then "FizzBuzz"
  else if n % 3 == 0 then "Fizz"
  else if n % 5 == 0 then "Buzz"
  else String.fromInt(n)

1..20
  |> List.map(fizzbuzz)
  |> String.join ", "
  |> IO.println!
```

```
type Maybe[a] =
  | Nothing
  | Just[a]

traverse(fn: a -> Maybe[b], list: List[a]): Maybe[List[b]]
traverse(fn,list) = go(list,[])
  where
    go([],bs) = Just(List.reverse(bs))
    go(a::as,bs) = 
      case fn(a) of
        Nothing -> Nothing
        Just(b) -> go(as,b::bs)

xs = [1,2,3,4,5]
ys = [6,7,8,9,10]
f = \n -> if n == 3 then Nothing else Just(n)

IO.inspect!(xs.traverse(f)) // -> Nothing
IO.inspect!(ys.traverse(f)) // -> Just([6,7,8,9,10])
```

## Links

* [GitHub](https://github.com/cara-lang/)
    * [Compiler](https://github.com/cara-lang/compiler/)
    * [This website](https://github.com/cara-lang/website/)
