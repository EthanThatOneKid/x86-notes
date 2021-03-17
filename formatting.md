# Formatting Text in x86 Assembly

Text can be formatted in x86 assembly by defining a string with specific codes to represent the values to be filled in.
Here are some examples of the possible codes used for formatting text:

| Code    | Format Expected                       |
| ------- | ------------------------------------- |
| `%s`    | String                                |
| `%d`    | Integer                               |
| `%ld`   | Long Integer                          |
| `%f`    | Float                                 |
| `%lf`   | Double                                |
| `%.3f`  | Float (to 3rd decimal place)          |
| `%10s`  | String (length of 10)                 |
| `%-10s` | String (length of 10) (right-aligned) |
