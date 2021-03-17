# GDB (GNU Debugger)

> [GDB, the GNU Project debugger](https://www.gnu.org/software/gdb/), allows you to see what is going on `inside' another program while it executes -- or what another program was doing at the moment it crashed.

Convention: Use a different bash (`.sh`) file for the debugger.

Usage: `gdb program-name.out`

| Command                                     | Behavior                      |
| ------------------------------------------- | ----------------------------- |
| `r`                                         | Run program                   |
| `q`                                         | Quits debugger                |
| `b <function_name or line_number>`          | Sets breakpoint               |
| `i b`                                       | List all breakpoints          |
| `i r`                                       | List all registers            |
| `i r s`                                     | List all 16 `xmm` registers   |
| `n`                                         | Next line                     |
| `ni`                                        | Tells what the next line is   |
| `s`                                         | Step; use to enter function   |
| `c`                                         | Continue                      |
| `si`                                        | Tells what the next step is   |
| `ptype <variable_name>`                     | Get type of variable          |
| `p/<ptype> <variable_name>`                 | Print the value of a variable |

> Note: `<variable_name>`s can also be the names of x86 Assembly registers if prefixed with `$`. Example: `p/f $xmm0`.

| `ptype` | Definition       |
| ------- | ---------------- |
| x       | Hexadecimal      |
| d       | Decimal          |
| u       | Unsigned Integer |
| f       | Float            |
| t       | Binary           |
| a       | Address          |
| s       | String           |
| c       | Character (char) |
