# Conversions 🔮

- [Decimal → Binary][decimal_to_binary]
- [Decimal → Binary (Fractional)][decimal_to_binary_fractional]
- [Binary → Decimal][binary_to_decimal]
- [Decimal → Hexadecimal][decimal_to_hexadecimal]
- [Hexadecimal → Decimal][hexadecimal_to_decimal]
- [Decimal → IEEE754][decimal_to_ieee754]
- [Binary → IEEE754][binary_to_ieee754]
- [IEEE754 → Decimal][ieee754_to_decimal]
- [Binary IEEE754 → Hexadecimal IEEE754][binary_ieee_to_hexadecimal_ieee]
- [Big Endian → Little Endian][big_endian_to_little_endian]
- [Little Endian → Big Endian][little_endian_to_big_endian]
- [+∞ in Decimal][positive_infinity_in_decimal]

What is the point of IEEE?
This is how computers deal with negative numbers!

> 💡 Do not forget to check which version of IEEE you are converting with so you know which of these constant values to use.

| Version | Exponent | Bias Number | Mantissa |
| ------- | -------- | ----------- | -------- |
| 32-bit  | 6 bits   | 127         | 23 bits  |
| 64-bit  | 11 bits  | 1023        | 53 bits  |

## Decimal → Binary

[decimal_to_binary]: #decimal--binary

Convert `112` to its binary representation.

| Division       | Remainder |
| -------------- | --------- |
| `112 / 2 = 56` | 0         |
| `56 / 2 = 28`  | 0         |
| `28 / 2 = 14`  | 0         |
| `14 / 2 = 7`   | 0         |
| `7 / 2 = 3`    | 1         |
| `3 / 2 = 1`    | 1         |
| `1 / 2 = 0`    | 1         |

The binary representation of `112` is the reverse of the remainder column, `1110000`.

## Decimal → Binary (Fractional)

[decimal_to_binary_fractional]: #decimal--binary-fractional

Convert `13.75` to its binary notation.

First, convert `13` [to binary][decimal_to_binary].

| Division     | Remainder |
| ------------ | --------- |
| `13 / 2 = 6` | 1         |
| `6 / 2 = 3`  | 0         |
| `3 / 2 = 1`  | 1         |
| `1 / 2 = 0`  | 1         |

`13 = 1101`

Now, let's convert the fraction to binary.

| Multiplication | Binary Digit |
| -------------- | ------------ |
| .75 × 2 = 1.5  | 1            |
| .5 × 2 = 1     | 1            |
| .0 × 2 = 0     | 0            |

`0.75 = 0.110`

So finally, the answer is `1101.11`.

## Binary → Decimal

[binary_to_decimal]: #binary--decimal

Convert `1110000` to its decimal representation.

| Degree | Binary Digit | Decimal Value  |
| ------ | ------------ | -------------- |
| 0      | 0            | `0 × 2^0 = 0`  |
| 1      | 0            | `0 × 2^1 = 0`  |
| 2      | 0            | `0 × 2^2 = 0`  |
| 3      | 0            | `0 × 2^3 = 0`  |
| 4      | 1            | `1 × 2^4 = 16` |
| 5      | 1            | `1 × 2^5 = 32` |
| 6      | 1            | `1 × 2^6 = 64` |

`0 + 0 + 0 + 0 + 16 + 32 + 64 = 112`

Sum up the _decimal value_ column to get the decimal representation, `112`.

## Decimal → Hexadecimal

[decimal_to_hexadecimal]: #decimal--hexadecimal

Convert `540` to its hexadecimal representation.

| Division        | Remainder | Hexadecimal Digit |
| --------------- | --------- | ----------------- |
| `540 / 16 = 33` | 12        | C                 |
| `33 / 16 = 2`   | 1         | 1                 |
| `2 / 16 = 0`    | 2         | 2                 |
| `0 / 16 = 0`    | 0         | 0                 |

The hexadecimal representation of `540` is the reverse of the _hexadecimal digit_ column, `21C`.

## Hexadecimal → Decimal

[hexadecimal_to_decimal]: #hexadecimal--decimal

Convert `1110000` to its decimal representation.

| Degree | Binary Digit | Decimal Value  |
| ------ | ------------ | -------------- |
| 0      | 0            | `0 × 2^0 = 0`  |
| 1      | 0            | `0 × 2^1 = 0`  |
| 2      | 0            | `0 × 2^2 = 0`  |
| 3      | 0            | `0 × 2^3 = 0`  |
| 4      | 1            | `1 × 2^4 = 16` |
| 5      | 1            | `1 × 2^5 = 32` |
| 6      | 1            | `1 × 2^6 = 64` |

`0 + 0 + 0 + 0 + 16 + 32 + 64 = 112`

Sum up the _decimal value_ column to get the decimal representation, `112`.

## Decimal → IEEE754

[decimal_to_ieee754]: #decimal--ieee754

Convert `45.45` to IEEE754 (32-bit).

First convert 45 [to binary][decimal_to_binary].

`45 = 101101`

Now convert 0.45 to [to binary][decimal_to_binary_fractional].

`0.45 = 0.011100(1100 repeating)`

Finally, convert the binary value, `101101.011100(1100 repeating)`, [to IEEE754][binary_to_ieee754].

## Binary → IEEE754

[binary_to_ieee754]: #binary--ieee754

What is `101101.011100(1100 repeating)` (`45.45` in decimal) in IEEE754 (32-bit)?

First, let's move the decimal up to the first number and put everything in scientific notation.

`1.01101011100 x 2^5`

Let's find S, the sign.
If the number is negative, S = 1, otherwise S = 0.

`S = 0`

Let's find E, the exponent.
The exponent is 5, based on the scientific notation representation.
Add the exponent to the bias number.
In this case, the bias number is 127 because we are using 32-bit version IEEE.

```
E = 5 + bias_number
  = 5 + 127
  = 132
```

Then convert the decimal value [to binary][decimal_to_binary]: `132 → 10000100`.

`E = 10000100`

Now let's find M, the mantissa.
Let's get the decimal from the scientific notation.

`01101011100`

There are only 11 digits here when there needs to be 23.
Fill the remaining digits with the repeating decimal point.

`M = 01101011100110011001100`

The ultimate value is the concatenation of S, E, and M.

| S   | E          | M                         |
| --- | ---------- | ------------------------- |
| `0` | `10000100` | `01101011100110011001100` |

The answer is `0 10000100 01101011100110011001100`.

## IEEE754 → Decimal

[ieee754_to_decimal]: #ieee754--decimal

| S     | E      | M       |
| ----- | ------ | ------- |
| 1 bit | 8 bits | 23 bits |

Convert `0 10000100 11010100000000000000000` (32-bit) to decimal.

Determine the sign, S.
The sign is positive because the first bit is zero.
If the sign were negative, the value would be `-1` instead of `1`.

`S = 0`

Determine the exponent, E.
The next 8 bits, `10000100`, represent the exponent.
Then convert the exponent it [to decimal][binary_to_decimal].

`10000100 → 132`

Then subtract the bias number from the exponent value to get the value of E.

`E = 132 - 127 = 5`

Next, convert mantissa to its dectimal (power of 2) sum equivalent.
The mantissa is `110101000...`.

| Degree | Binary Digit | Decimal Value                    |
| ------ | ------------ | -------------------------------- |
| -1     | 1            | `1 × 2^(-1) = 1 / 2 = 0.50`      |
| -2     | 1            | `1 × 2^(-2) = 1 / 4 = 0.25`      |
| -3     | 0            | `0 × 2^(-3) = 0`                 |
| -4     | 1            | `1 × 2^(-4) = 1 / 16 = 0.0625`   |
| -5     | 0            | `0 × 2^(-5) = 0`                 |
| -6     | 1            | `1 × 2^(-6) = 1 / 64 = 0.015625` |

Sum the right-most column to get the value of the mantissa.

`M = 0.828125`

Next, combine S, E, and M using the following formula.

```
answer = -1^(E) × (1 + M) × 2^(E)
       = -1^(5) × (1.828125) × 2^(5)
       = 1 × 1.828125 × 32
       = 58.5
```

The answer is `58.5`!

## Binary IEEE754 → Hexadecimal IEEE754

[binary_ieee_to_hexadecimal_ieee]: #binary-ieee754--hexadecimal-ieee754

_todo_

## Big Endian → Little Endian

[big_endian_to_little_endian]: #big-endian--little-endian

_todo_

## Little Endian → Big Endian

[little_endian_to_big_endian]: #little-endian--big-endian

_todo_

## +∞ in Decimal

[positive_infinity_in_decimal]: #-in-decimal

The largest value possible in a quadword register is `0x7FF0 0000 0000 0000` in hexadecimal.
So, `+∞ = 0x7FF0 0000 0000 0000`.

```
  0x7FF
- 0x3FF
---------
  0x400

0x400 → 0100 0000 0000
0100 0000 0000 → 1024
1024 = true exponent

ans = 1.0000.. × 2^1024
      ^ hidden bit
    = 2^1024      
```
