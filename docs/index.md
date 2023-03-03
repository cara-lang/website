---
hide:
  - navigation
---

# Cara

:city_sunset: Cara is a programming language aiming to be pleasant to use and maintain while
staying safe and dependable.

!!! warning
    Cara is in development: [@janiczek](https://github.com/Janiczek) is still
    figuring out the design, syntax and functionality. In the meantime, some code
    snippets can be found in the compiler's [end-to-end test
    suite](https://github.com/cara-lang/compiler/tree/main/end-to-end-tests) on
    GitHub.

## Features

To put it shortly, Cara combines:

<div class="grid" markdown>

:simple-elm: __[Elm](https://elm-lang.org)__ and its safety, maintainability and friendliness
{ .card }

:simple-haskell: __[Haskell](https://www.haskell.org)__ and its brevity and power (in moderation)
{ .card }

:simple-kotlin: __[Kotlin](https://kotlinlang.org)__ and its familiarity and syntax sugar
{ .card }

> :material-robot-confused-outline: __[INTERCAL](https://en.wikipedia.org/wiki/INTERCAL)__ and its... just kidding!

</div>

Here is an incomplete list of Cara's features:

* General-purpose
* Compiled to automatically parallel native code via [HVM](https://github.com/Kindelia/hvm)...
* ...or interpreted (handy for scripting)
* Immutable
* Purely functional
* Familiar ALGOL-like syntax
* Statically typed with automatic type inference
* ADTs with exhaustive pattern matching

## Examples

!!! tip
    There is a large sampling of Cara programs in the [end-to-end test
    suite](https://github.com/cara-lang/compiler/tree/main/end-to-end-tests).

``` cara title="quicksort.cara"
quickSort(List[Int]): List[Int]
quickSort([]) = []
quickSort([x,...xs]) = {
  (lt, gt) = List.partition(#(x >= _), xs)
  quickSort(lt) ++ x ++ quickSort(gt)
}

[5,1,3,2,4]
  |> quickSort
  |> IO.println!
```

``` cara title="fs_script.cara"
#!/usr/bin/env cara

dst = IO.ask!("Enter destination filename: ")
dstHandle = FS.open!(src, FS.Write)

timestampFmt = "hh:mm:ss.fff"

1..10 |> IO.forEach!(\i -> IO {
  time = Time.now!()
  dstHandle |> FS.write!("[${Time.format(timestampFmt, time)}] Hello number $i\n")
})
```

``` cara title="fizzbuzz.cara"
fizzbuzz(n) =
  if n % 15 == 0 then "FizzBuzz"
  else if n % 3 == 0 then "Fizz"
  else if n % 5 == 0 then "Buzz"
  else "$n"

1..20
  |> List.map(fizzbuzz)
  |> String.join(", ")
  |> IO.println!
```

``` cara title="maybe_traverse.cara"
type Maybe[a] =
  | Nothing
  | Just(a)

traverse(fn: a -> Maybe[b], list: List[a]): Maybe[List[b]]
traverse(fn,list) = go(list,[])
  where
    go([],bs) = Just(List.reverse(bs))
    go([a,...as],bs) = 
      case fn(a) of
        Nothing -> Nothing
        Just(b) -> go(as,b++bs)

xs = [1,2,3,4,5]
ys = [6,7,8,9,10]
f = \n -> if n == 3 then Nothing else Just(n)

IO.println!(xs |> traverse(f)) // -> Nothing
IO.println!(ys |> traverse(f)) // -> Just([6,7,8,9,10])
```

## Installation

Right now the language tooling is very rough around the edges: if you want to
try the language out, you'll need to `git clone` the compiler repository.

You'll need [Deno](https://deno.land/) to run the compiler.

``` shell title="Running the compiler"
git clone https://github.com/cara-lang/compiler cara-compiler
cd cara-compiler

./run.ts end-to-end-tests/int/main.cara
./debug.ts end-to-end-tests/int/main.cara
./test.ts
```

!!! tip
    The `.ok` files across the Cara repositories are generally a good way to
    get an idea of how to work with the repositories. (Shout out to
    [@secretGeek](https://twitter.com/secretGeek)'s
    [`ok`](https://secretgeek.net/ok) tool!)

## Contribute

As of Q1 2023, I (1) am still largely trying to design how the language will
look and behave rather than implementing it.
{ .annotate }

1. [@janiczek](https://github.com/Janiczek)

If you'd like to discuss it, feel free to open a GitHub
[issue](https://github.com/cara-lang/compiler/issues) or send me a message on
[Twitter](https://twitter.com/janiczek) or
[Mastodon](https://functional.cafe/@janiczek). I do want to keep some creative
freedom so I won't promise this will be "design by commitee" nor any kind of
democracy, but I would be very happy to hear your opinions, experience and
tales from the trenches! (1)
{ .annotate }

1. _"This will be impossible to parse because XYZ!"_

If you instead want to contribute to the documentation (this website), feel
free to head over to the [website repo](https://github.com/cara-lang/website)
and make a PR or an issue!
