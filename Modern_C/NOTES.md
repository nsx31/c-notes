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

# Integer Type
Values of integer type are whole numbers. The integer type is divided into two categories: **signed** and **unsigned**. By default integer type is **signed**. The size of integer type can be 16 bit, 32 bit or 64 bit depending upon the machine and compiler the program is running on. Depending upong the value of number, i.e, how big or small a number is we can choose from **short**, **int**, **long** and **long long**. 

```c
//example 1
int num
unsigned int num

//example 2
short num
unsigned short num

//example 3
long num
unsigned long num

//example 4
long long num
unsigned long long num
```
Abbreviation and their meaning :
| Symbol | Meaning              |
| ------ | -------------------- |
| **d**  | signed decimal       |
| **u**  | unsigned decimal     |
| **o**  | unsigned octal       |
| **x**  | unsigned hexadecimal |
| **h**  | short                |
| **l**  | long                 |
| **ll** | long long            |

```c
//example 1
unsigned int num;

//when input is given in base 10
printf("%u", num);  
scanf("%u", &num);

//when input is given in octal
printf("%o", num);
scanf("%o", &num);

//when input is given in hexadecimal
printf("%x", num);
scanf("%x", &num);
```

# Integer Constants
Ineger constants are the numbers that appears in the text of a program, not numbers that are read, written or computed. C allows integer constants to be written in decimal, octal or hexadecimal.
- **Decimal constants:** must not begin with `0`.
- **Octal constants:** must begin with `0`.
- **Hexadecimal constants:** always begin with `0x`

```c
//example 1 : Integer constant's decimal representation
15

//example 2 : Integer constant's octal representation
017

//example 3 : Integer constant's hexadecimal representation
0xf
```

By default intger constants are of **int** type. However if the value of the constant is too large to store in int then **long**, **unsigned long**, **long long** or **unsigned long long** can be used.

```c
//example 1 : long integer constant
15L or 15l

//example 2 : long long integer constant
15LL or 15ll

//example 3 : unsigned long integer constant
15LU or 15lu

//example 4 : unsigned long long integer constant
15LLU or 15llu

//example 5 : unsigned integer constant
15U or 15u
```

# Floating Type
It used to store numbers having digits after decimal point. C provides three floating type: **float**, **double**, **long double**. By default floating type is **double**.

```c
// example 1
double num;

scanf("%lf", &num); //When reading a value of type double, put the letter l in fron
printf("%f", num);

// example 2
long double num;

scanf("%lf", &num);
printf("%lf", num);

// example 3
float num;

scanf("%f", &num);
printf("%f", num);
```

# Floating Constants
By default floating constants are **double**. 

```c
//example 1 : float constant
14.5f

//example 2 : double floating point constant 
14.5

//example 3 : long double floating point constant
14.5l
```

# Character Type
C treats character as small integer. The connection between character and integer in C is so strong that character constants are of **int** type rather than **char** type. When a character appears in computation, C simply uses its integer value. Characters can be compared just as numbers can. Like integer type character type can also be signed or unsigned. 

```c
//example
char ch = 'a';
```

```c
//example 1
printf("%c", ch);

//example 2
scanf("%c", &ch);
```

# Type Defination
```c
#define BOOL int
```
There is a better way to setup boolean type using type defination. 

```c
#typedef int Bool;
```
Usinf **typedef** to define **Bool** causes the compiler to add **Bool** to the list of type names that it recognizes. **Bool** can now be used in the same way as the buit-in types.