<div align="center">

# 🖨️ ft_printf

_Because ft_putnbr and ft_putstr aren't enough._

[![42 School](https://img.shields.io/badge/42-School-000000?style=for-the-badge&logo=42&logoColor=white)](https://42.fr/)
[![Grade](https://img.shields.io/badge/Grade-100%2F100-success?style=for-the-badge)]()
[![Language](https://img.shields.io/badge/Language-C-blue?style=for-the-badge&logo=c&logoColor=white)]()
[![Norminette](https://img.shields.io/badge/Norminette-Passing-brightgreen?style=for-the-badge)]()

</div>

---

## 📖 About

**ft_printf** is the second project of the 42 cursus. The goal is to recode the standard C `printf` function, learning how to handle a **variable number of arguments** using `<stdarg.h>` along the way.

The resulting static library `libftprintf.a` mimics the original `printf` behavior for the most commonly used conversions, and returns the total number of characters printed — just like the original.

---

## 🎯 Project scope

- ✅ **Mandatory** — 9 conversions fully supported
- ⬜ **Bonus** — flags `-`, `0`, `.`, `#`, ` `, `+`, field width (not implemented)

---

## 🔤 Supported conversions

| Specifier | Description                                    | Example input            | Output            |
|:---------:|------------------------------------------------|--------------------------|-------------------|
|   `%c`    | Single character                               | `'A'`                    | `A`               |
|   `%s`    | Null-terminated string (`(null)` if `NULL`)    | `"42"`                   | `42`              |
|   `%d`    | Signed decimal integer                         | `-42`                    | `-42`             |
|   `%i`    | Signed decimal integer (alias of `%d`)         | `42`                     | `42`              |
|   `%u`    | Unsigned decimal integer                       | `4294967295`             | `4294967295`      |
|   `%x`    | Unsigned hexadecimal (lowercase)               | `255`                    | `ff`              |
|   `%X`    | Unsigned hexadecimal (uppercase)               | `255`                    | `FF`              |
|   `%p`    | Pointer address (`(nil)` if `NULL`)            | `&var`                   | `0x7ffeea1b2c30`  |
|   `%%`    | Literal percent sign                           | —                        | `%`               |

---

## 🧠 How it works

```
