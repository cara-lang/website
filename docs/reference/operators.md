# Operators

There is a fixed set of operators in Cara:

``` cara title="Unary operators"
// ! - ~

!True      // -> False    | bool negation
-(-123)    // -> 123      | number negation
~0b100011  // -> 0b011100 | binary negation
```

``` cara title="Binary operators"
// + - * / % **
// <= < == != > >=
// || &&
// ++ 
// .. ...
// | & ^ << >> >>>

1 + 2  // -> 3 | addition
3 - 2  // -> 1 | subtraction
2 * 4  // -> 8 | multiplication
4 / 2  // -> 2 | division
5 % 2  // -> 1 | modulo
2 ** 3 // -> 8 | exponentiation

1 <= 3 // -> True  | less than or equal
5 < 2  // -> False | less than
3 == 1 // -> False | equals
3 != 1 // -> True  | not equal
5 > 2  // -> True  | greater than
1 >= 3 // -> False | greater than or equal

True || False // -> True  | logical OR
True && False // -> False | logical AND

   1  ++ [2,3] // -> [1,2,3]   | append
[1,2] ++ [3,4] // -> [1,2,3,4] |
[1,2] ++  3    // -> [1,2,3]   |

1..5  // -> [1,2,3,4,5] | range (inclusive)
1...5 // -> [1,2,3,4]   | range (exclusive)

0b1001 | 0b0010 // -> 0b1011   | bitwise OR
0b1001 & 0b0011 // -> 0b0001   | bitwise AND
0b1001 ^ 0b1010 // -> 0b0011   | bitwise XOR
0b1001 << 2     // -> 0b100100 | bitwise shift left
0b1001 >> 2     // -> 0b10     | bitwise shift right (sign-preserving, arithmetic)
0b1001 >>> 2    //             | bitwise shift right (unsigned, logical)
```

## Functions

Operators are just functions under the hood, and you can access them with
backticks (`` ` ``):

``` cara
plus = `+`
plus(1,2) // -> 3

0
  |> plus(1)
  |> `+`(2)
  |> #(_ + 3)
// -> 6
```

## Overloading

All these operators can be overloaded to provide nicer APIs and build DSLs:

``` cara title="Overloading example: XY pair"
type alias XY = (Int, Int)

`+`((ax,ay): XY, (bx,by): XY): XY = (ax+bx, ay+by)
`*`((ax,ay): XY, (bx,by): XY): XY = (ax*bx, ay*by)
`*`(k: Int,      (x,y): XY):   XY = (k*x,   k*y)

(1,2) + (3,4) // -> (4,6)
(1,2) * (3,4) // -> (3,8)
3 * (3,4)     // -> (9,12)
```

``` cara title="Overloading example: Routing DSL"
type Route
  = Root
  | Nest(Route,String)

`/`(r: Route, s: String): Route = Nest(r,s)

Root / "api" / "v1" / "workspaces"
// -> Nest(Nest(Nest(Root,"api"),"v1"),"workspaces")
```
