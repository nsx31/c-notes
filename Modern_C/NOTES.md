# Compiling & Linking
Source code is first given to the `preprocessor` then to the `compiler` then to the `assembler` and in the end it is passed to the `linker`. 
- **Preprocessor** processes the source file before compilation. It handles preprocessor directives such as `#include`, `#define`, and `#if`. When it encounters a header file via `#include`, it textually substitutes the contents of that header file into the source file.
- After preprocessing, the edited source file is passed to the **compiler**, which translates the high-level, human-readable code into **assembly language**. The generated assembly code is then passed to the **assembler**, which converts it into **machine language (binary)** and produces an **object file**.
- After compilation, the generated object files are passed to the **linker**. A program may be split across multiple source files and may also use functions and variables declared in header files but defined elsewhere. The compiler compiles each source file independently into an object file(.o). The linker then combines multiple object files into a single executable and links required libraries. The final output of the linker is a single executable that can be loaded and run by the operating system.

# Defining a name for Constants
When a program contains constants, it's often a good idea to give them names.

```c
//example 1
#define INCHES_PER_POUND 166

//example 2
#define PI 3.14
```
# Conversion Specification
A conversion specification can have a form : `%m.pX` or `%-m.pX`. Where `m` and `p` are integer constants and `X` is a letter. 
- **m :** specifies the minimum field width, i.e, the minimum number of characters to print. If the value to be printed requires fewer than *m* characters, extra spaces precede the value. For example, the specification %4d would display the number 123 as •123 ( used • to represent the space character).  If the value to be printed requires more than *m* characters, the field width automatically expands to the necessary size. %4d would display the number 12345 as 12345—no digits are lost. Putting a minus sign in front of m causes left justification; the specification %-4d would display 123 as 123•
- **p :** stands for precision and it depends on the choice of `X`. For `X`,
    - **d :** p indicates the minimum number of digits to display (extra zero are added to the beginning of the number if necessary).
    - **e :** p indicates how many digits should appear after the decimal point.
    - **f :** p indicates how many digits should appear after the decimal point.
    - **g :** p indicates the maximum number of significant digits.

```c
//example 1
printf("|%5d|", 123)        // |  123|

//example 2
printf("|%-5d|", 123)       // |123  |

//example 3
printf("%.2d", 2)           // 02

//example 4
printf("%2f", 544.6543)     // 544.65  
```

# *printf* and *scanf* function
**printf** displays formatted string while **scanf** reads input according to a particular format. A **scanf** format string may contain both ordinary characters and conversion specifications. In many cases, a **scanf** format string will contain only conversion specifications. It is essentially a pattern matching function that tries to match up groups of inputs characters with conversion specifications. 

```c
//example 1
scanf("%d%d%f%f", &i, &j, &x, &y);          // Input: 1 -5 3.0 4.21 

// example 2
scanf("%d/%d/%d", &day, &month, &year);     // Input: 12/02/1995

//example 3 
scanf("%2d", &num);                         // Input: 3242      Output: 32
```

- Example 1 is a basic use of the **scanf** function where only conversion specifiers are used. **scanf** reads the input values sequentially and assigns them to the corresponding variables, skipping any whitespace between inputs.
- In Example 2, both conversion specifiers and literal characters (/) are used in the format string. Here, input is successfully read only if the input exactly matches the format—that is, the numbers must be separated by /. If the / characters are missing or placed differently, scanf will stop reading input at that point.
- Example 3 demonstrates how we can limit the number of digits being stored in a variable using conversion specification.

# Boolean values in C
C does not have a built-in Boolean type. The header file `<stdbool.h>` allows programmers to use Boolean-like values by defining the `_Bool` type along with `true` and `false`. Internally, `_Bool` is an integer: `false` is represented by `0`, and `true` is represented by a non-zero value.

```c
//example 
_Bool flag = true;
```
# Switch statement
General form :
```c
// general form
switch (expression){
    case constant-expression-1 :
        //statements
        break;
    case constant-expression-2 :
        //statements 
        break;
    default :
        //statement
        break;
}
```

Imagine a situation where multiple **switch** cases return the same result. Instead of copy-pasting the same code repeatedly, we can group those cases together like this:

```c
switch (expression){
    case constant-expression-1 :
    case constant-expression-2 :
    case constant-expression-3 :
        //statements
        break;
    case constant-expression-4 :
        //statements 
        break;
    default :
        //statements 
        break;
}
```

- **Break :** To transfer the control out of statements or loops **break** is used.
- **Continue :** It can be used where we want to skip iteration of a loop.
- **Goto :** The target of a **break** is a point just beyond the end of the enclosing loop, while the target of a **continue** is a point just before the end of the loop. The **goto** statement, on the other hand, is capable of jumping to any statement in a function, provided that the statement has a label.

```c
for (d = 2; d < n; d++){
    if (n % d == 0){
        goto done;
    }
}

done:
if (d < n){
    printf("%d is divisible by %d\n", n, d);
}else{
    printf("%d is prime\n", n);
}
```