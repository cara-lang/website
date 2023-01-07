# Numbers

``` cara
x: Int = 123
y: Float = 5.5
```

Cara supports the following number types on the language level:

<style>
svg { padding: 16px 0; }
svg text {
  font-family: Rubik, sans-serif;
  font-size: 40px;
  font-weight: 500;
  white-space: pre;
  fill: white;
}
svg text.legend { fill: black; }
</style>
<svg width="470" height="328" viewBox="0 0 940 656" fill="none" xmlns="http://www.w3.org/2000/svg">
<text class="legend"><tspan x="59.118" y="44.5455">Legend</tspan></text>
<rect x="316" y="435" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="347.174" y="489.545">Int64</tspan></text>
<rect x="316" y="290" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="347.819" y="344.545">Int32</tspan></text>
<rect x="316" y="145" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="350.807" y="199.545">Int16</tspan></text>
<rect x="316" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="359.898" y="54.5455">Int8</tspan></text>
<rect x="536" y="435" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="552.868" y="489.545">UInt64</tspan></text>
<rect x="536" y="290" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="553.513" y="344.545">UInt32</tspan></text>
<rect x="536" y="145" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="556.501" y="199.545">UInt16</tspan></text>
<rect x="536" width="160" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="565.592" y="54.5455">UInt8</tspan></text>
<path d="M397.5 374C397.5 373.172 396.828 372.5 396 372.5C395.172 372.5 394.5 373.172 394.5 374H397.5ZM394.939 432.061C395.525 432.646 396.475 432.646 397.061 432.061L406.607 422.515C407.192 421.929 407.192 420.979 406.607 420.393C406.021 419.808 405.071 419.808 404.485 420.393L396 428.879L387.515 420.393C386.929 419.808 385.979 419.808 385.393 420.393C384.808 420.979 384.808 421.929 385.393 422.515L394.939 432.061ZM394.5 374V431H397.5V374H394.5Z" fill="#B3B3B3"/>
<path d="M617.5 374C617.5 373.172 616.828 372.5 616 372.5C615.172 372.5 614.5 373.172 614.5 374H617.5ZM614.939 432.061C615.525 432.646 616.475 432.646 617.061 432.061L626.607 422.515C627.192 421.929 627.192 420.979 626.607 420.393C626.021 419.808 625.071 419.808 624.485 420.393L616 428.879L607.515 420.393C606.929 419.808 605.979 419.808 605.393 420.393C604.808 420.979 604.808 421.929 605.393 422.515L614.939 432.061ZM614.5 374V431H617.5V374H614.5Z" fill="#B3B3B3"/>
<path d="M617.5 229C617.5 228.172 616.828 227.5 616 227.5C615.172 227.5 614.5 228.172 614.5 229H617.5ZM614.939 287.061C615.525 287.646 616.475 287.646 617.061 287.061L626.607 277.515C627.192 276.929 627.192 275.979 626.607 275.393C626.021 274.808 625.071 274.808 624.485 275.393L616 283.879L607.515 275.393C606.929 274.808 605.979 274.808 605.393 275.393C604.808 275.979 604.808 276.929 605.393 277.515L614.939 287.061ZM614.5 229V286H617.5V229H614.5Z" fill="#B3B3B3"/>
<path d="M397.5 229C397.5 228.172 396.828 227.5 396 227.5C395.172 227.5 394.5 228.172 394.5 229H397.5ZM394.939 287.061C395.525 287.646 396.475 287.646 397.061 287.061L406.607 277.515C407.192 276.929 407.192 275.979 406.607 275.393C406.021 274.808 405.071 274.808 404.485 275.393L396 283.879L387.515 275.393C386.929 274.808 385.979 274.808 385.393 275.393C384.808 275.979 384.808 276.929 385.393 277.515L394.939 287.061ZM394.5 229V286H397.5V229H394.5Z" fill="#B3B3B3"/>
<path d="M397.5 84C397.5 83.1716 396.828 82.5 396 82.5C395.172 82.5 394.5 83.1716 394.5 84H397.5ZM394.939 142.061C395.525 142.646 396.475 142.646 397.061 142.061L406.607 132.515C407.192 131.929 407.192 130.979 406.607 130.393C406.021 129.808 405.071 129.808 404.485 130.393L396 138.879L387.515 130.393C386.929 129.808 385.979 129.808 385.393 130.393C384.808 130.979 384.808 131.929 385.393 132.515L394.939 142.061ZM394.5 84V141H397.5V84H394.5Z" fill="#B3B3B3"/>
<path d="M617.5 84C617.5 83.1716 616.828 82.5 616 82.5C615.172 82.5 614.5 83.1716 614.5 84H617.5ZM614.939 142.061C615.525 142.646 616.475 142.646 617.061 142.061L626.607 132.515C627.192 131.929 627.192 130.979 626.607 130.393C626.021 129.808 625.071 129.808 624.485 130.393L616 138.879L607.515 130.393C606.929 129.808 605.979 129.808 605.393 130.393C604.808 130.979 604.808 131.929 605.393 132.515L614.939 142.061ZM614.5 84V141H617.5V84H614.5Z" fill="#B3B3B3"/>
<rect x="756" y="290" width="184" height="80" rx="6" fill="#14AE5C"/>
<text><tspan x="777.906" y="344.545">Float32</tspan></text>
<rect x="756" y="435" width="184" height="80" rx="6" fill="#14AE5C"/>
<text><tspan x="777.261" y="489.545">Float64</tspan></text>
<path d="M849.5 374C849.5 373.172 848.828 372.5 848 372.5C847.172 372.5 846.5 373.172 846.5 374H849.5ZM846.939 432.061C847.525 432.646 848.475 432.646 849.061 432.061L858.607 422.515C859.192 421.929 859.192 420.979 858.607 420.393C858.021 419.808 857.071 419.808 856.485 420.393L848 428.879L839.515 420.393C838.929 419.808 837.979 419.808 837.393 420.393C836.808 420.979 836.808 421.929 837.393 422.515L846.939 432.061ZM846.5 374V431H849.5V374H846.5Z" fill="#B3B3B3"/>
<rect x="354" y="576" width="84" height="80" rx="6" fill="#9747FF"/>
<text><tspan x="372.095" y="630.545">Int</tspan></text>
<rect x="556" y="576" width="120" height="80" rx="6" fill="#9747FF"/>
<text><tspan x="577.789" y="630.545">UInt</tspan></text>
<path d="M396 572V519" stroke="#B3B3B3" stroke-width="3" stroke-miterlimit="0" stroke-linecap="round" stroke-linejoin="bevel"/>
<path d="M616 519V572" stroke="#B3B3B3" stroke-width="3" stroke-miterlimit="0" stroke-linecap="round" stroke-linejoin="bevel"/>
<rect x="784" y="576" width="128" height="80" rx="6" fill="#9747FF"/>
<text><tspan x="802.182" y="630.545">Float</tspan></text>
<path d="M848 572V519" stroke="#B3B3B3" stroke-width="3" stroke-miterlimit="0" stroke-linecap="round" stroke-linejoin="bevel"/>
<rect x="0.5" y="80.5" width="255" height="335" rx="11.5" fill="#F5FBFF"/>
<rect x="32" y="118" width="192" height="80" rx="6" fill="#0D99FF"/>
<text><tspan x="58.3847" y="172.545">Integral</tspan></text>
<rect x="32" y="210" width="192" height="80" rx="6" fill="#14AE5C"/>
<text><tspan x="54.097" y="264.545">Decimal</tspan></text>
<rect x="32" y="302" width="192" height="80" rx="6" fill="#9747FF"/>
<text><tspan x="51.6073" y="356.545">Defaults</tspan></text>
<rect x="0.5" y="80.5" width="255" height="335" rx="11.5" stroke="#BDE3FF"/>
</svg>

Each of the numbered types denotes how wide it is: eg. `UInt64` is 64 bits
wide.

`UInt` types mean "unsigned int": a number without the sign bit.

Floats implement the [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754) spec
and specifically the `binary32` and `binary64` formats.

The types `Int`, `UInt` and `Float` are convenience
[aliases](/reference/type-aliases/) for `Int64`, `UInt64` and `Float64`
respectively.

Numbers of different types are automatically promoted to the larger one when
used together:

``` cara title="Promotion"
x: Int   = -125
y: Float = 0.5
z = x * y       // -> z: Float = -62.5
```

You can use underscore separators:

``` cara title="Separators"
x = 12_345_678
y = 1.250_025

z = 1_23_456_7 // no need to keep them 3 digits apart
```

Integers can be written in the binary (`0b`), octal (`0o`) and hexadecimal
(`0x`) bases:

``` cara title="Other bases"
bin = 0b0000_1111_1000_0010 // = 3970 in base 10
oct = 0o777                 // =  511 in base 10
hex = 0x11F8                // = 4600 in base 10

canBeNegative = -0b1101     // =  -13 in base 10
```

Floats can be written in the [scientific notation](https://en.wikipedia.org/wiki/Scientific_notation):

``` cara title="Scientific notation"
x =  123.45e5  //  123.45 * 10^5    = 12_345_000
y = -123.45e-5 // -123.45 * 10^(-5) = -0.0012345
```

## Standard library number types

There are more number types in the [standard library](/reference/stdlib/):

* `Complex` numbers (TODO)
* `BigInteger` (TODO)
* `BigDecimal` (TODO)
* `Fraction` (TODO)
