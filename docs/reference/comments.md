# Comments

There are three types of comments: line comments, block comments and shebangs.

## Line comments

Line comments start with `//` and continue until the end of the current line:

``` cara
x = 1 // Here's a comment!
      // Everything to the right of it is ignored: x = 2

IO.println!(x) // -> 1
```

## Block comments

Block comments start with `/*` and end with `*/`. They can span multiple lines
and be nested:

``` cara
/* A longer comment.
   Newlines are just fine!
*/

/* An example of a nested comment:
/* Second level! */
Back to first level. */
```

This nesting can ocassionally be useful for commenting out code, although it's
probably a better idea to use version control to hold your old code.

## Shebang

Cara supports shebangs to make scripting easier.
[Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) is a special type of
line comment starting with `#!`.

These comments are used by UNIX to find which interpreter to use to run a given
script (the current file) with.

``` cara
#!/usr/bin/env cara
IO.println!("I'm an executable Cara script!")
```

Executing `./script.cara` will now result in executing
`/usr/bin/env cara ./script.cara`, which will find the path of `cara` and run
`/your/path/to/cara ./script.cara`.

!!! note
    Shebangs can only be used at the very beginning of the script.
