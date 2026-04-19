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
┌────────────────────────────────────────────────────────┐
│  ft_printf("%s is %d", "age", 42)                      │
└────────────────────────────────────────────────────────┘
                        │
                        ▼
        ┌─────────────────────────────┐
        │  va_start — open arg list   │
        └─────────────────────────────┘
                        │
                        ▼
   parse format string character by character
                        │
          ┌─────────────┴─────────────┐
          │                           │
      regular char                 '%' found
          │                           │
          ▼                           ▼
     write(1, c)              dispatch to handler
                                      │
                           ┌──────────┴──────────┐
                           │                     │
                      ft_putstr             ft_print_base10
                      ft_putchar            ft_print_base16
                                            ft_print_ptr
                                      │
                                      ▼
                           count += chars written
                        │
                        ▼
        ┌─────────────────────────────┐
        │   va_end — close arg list   │
        └─────────────────────────────┘
                        │
                        ▼
              return total count
```

---

## 🛠️ Build

```bash
# Clone
git clone https://github.com/Vavongg/ft_printf.git
cd ft_printf

# Build the static library
make

# Cleanup
make clean    # remove .o files
make fclean   # remove .o files + libftprintf.a
make re       # full rebuild
```

Output: **`libftprintf.a`** — a static library ready to be linked.

---

## 🚀 Usage

Include the header and link the library when compiling your project:

```c
#include "ft_printf.h"

int main(void)
{
    int printed;

    printed = ft_printf("Hello, %s! You are %d years old.\n", "42", 3);
    ft_printf("Total characters written: %d\n", printed);
    ft_printf("Pointer: %p\n", &printed);
    ft_printf("Hex: %x / %X\n", 255, 255);
    return (0);
}
```

```bash
cc main.c -L. -lftprintf -I. -o my_program
./my_program
```

Expected output:
```
Hello, 42! You are 3 years old.
Total characters written: 32
Pointer: 0x7ffeea1b2c30
Hex: ff / FF
```

---

## 📁 Structure

```
ft_printf/
├── Makefile
├── ft_printf.h            # Public header
├── ft_printf.c            # Entry point + format dispatcher
├── ft_printf_utils.c      # ft_putchar, ft_putstr, ft_itoa_base
├── ft_print_base10.c      # %d %i %u handler
├── ft_print_base16.c      # %x %X handler
└── ft_print_ptr.c         # %p handler
```

---

## 🧪 Key concepts learned

- **Variadic functions** — `va_list`, `va_start`, `va_arg`, `va_end`
- **Static libraries** — `ar -rsc` archive creation
- **Base conversion** — implementing `itoa` for bases 10, 16, and pointer-sized values
- **Edge cases** — handling `NULL` strings, `(nil)` pointers, unsigned overflows

---

<div align="center">

Built with ☕ at **42 School** · [github.com/Vavongg](https://github.com/Vavongg)

</div>
