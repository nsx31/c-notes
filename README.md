# Hello World

```c
#include <stdio.h>

int main(){
    printf("Hello World \n");
    return 0;
}
```

- `stdio.h` is a header file.
- `#include` or `#define` is a directives. Directives are commands that begins with `#` and which are meant for pre-processor.
- when a program compiles, compiler always looks for `main()` function. `main()` function can either return 0 or 1. 0 means everything worked fine and 1 means there is some problem in code.

# Coverting the program into the machine code
It is a three step process :
1. **Preprocess :** Before compilation, the source code file is passed to the preprocessor, whose job is to include the code written in header files (libraries) into the source file.

2. **Compiling :** The modified source code is then passed to the compiler, whose job is to check whether the code is syntactically correct. It also marks the places where program elements like functions, variables, etc., are used. Once the compiler finishes, it produces an object file (with .o or .obj extension). This object file contains machine code along with references to functions, variables, and other program elements that are yet to be resolved.

3. **Linking :** The object file is then passed to the linker, whose job is to locate and connect the referenced functions, variables, and other program elements to their actual definitions.

> It’s like the compiler leaves blank spaces in place of functions and variables, and then the linker fills those spaces with the correct addresses or definitions of those elements. 

# Conversion Specification in C

The general form of conversion specification in C is : 
```c
%m.pX
```
where : 
- `m` : **Minimum field width** (optional)
- `p` : **Precision** (optional)
- `X` : *Conversion specifier (data type)*

**Example :** 

```c
12.4f       // Here, m = 12, p = 4 and X = f
``` 
### Minimum Field Width (m)
- Specifies minimum number of character to print.
- If number has fewer digits → space is added to fill the width.
- If number has more digits → field expands automatically.

```c
// number - 123

printf("%5d", 123)      // "  123"
printf("%2d", 123)      // "123"   (auto-expanded)
```

**Left alignment :**
Add `-` minus sign before `m` to left-align output(space after number).
```c
printf("%-6d", 123)     // "123   "
```

### Precision (p)
- Meaning of p depends on the data type:

| Type  | Meaning of `p`                                             |
| ----- | ---------------------------------------------------------- |
| **d** | Minimum digits to display (adds leading zeros if needed)   |
| **f** | Number of digits after decimal point                       |
| **e** | Number of digits after decimal point (in exponential form) |
| **g** | Maximum number of significant digits (total digits shown)  |

### Conversion Specifier (X)
| Specifier | Meaning                                                     |
| --------- | ----------------------------------------------------------- |
| **d**     | Integer (base 10)                                           |
| **f**     | Floating-point (decimal)                                    |
| **e**     | Floating-point (exponential form)                           |
| **g**     | Chooses **f** or **e** automatically (based on number size) |

>`%g` is useful when you don’t know in advance how large the number might be.

```c
printf("%.4d", 53);        // 0053
printf("%.3e", 123312.54); // 1.233e+05
printf("%.5g", 123312.54); // 1.2331e+05
```

# Constants in C

In C constants are defined outside the `main()` function. 
```c
#include <stdio.h>
#define PI 3.14
#define INTEREST_RATE 10.25

int main(){
    printf("Interest rate is : %f", INTEREST_RATE);
}
```

