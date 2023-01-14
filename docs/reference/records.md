# Records

Records are collections of data with named fields:

``` cara
user = {
  name: "Martin",
  country: "CZ",
  legs: 2,
}

user.legs // -> 2
```

## Updating a record

``` cara
renamed = {...user, name: "Marvin"}
// -> {name: "Marvin", country: "CZ", legs: 2}
// `user` is unchanged

withArms = {...user, arms: 2}
// -> {name: "Martin", country: "CZ", legs: 2, arms: 2}
```

## Getters

``` cara
record |> .name  // ==
.name(record)    // ==
record.name

getter = .name
getter(user)    // -> "Martin"
getter(renamed) // -> "Marvin"
```

## Pattern matching

``` cara
position = {x: 1, y: 5}
{x} = position
x // -> 1

{..} = position
// both x and y are now in scope
```

## Punning

``` cara
x = 1
y = 5
rec = {x,y}
// -> {x: 1, y: 5}
```

## Record types

``` cara
type alias XY = {
  x: Int,
  y: Int,
}

pos: XY = {x: 1, y: 5}
```
