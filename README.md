# 01 Hello World

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

# 02 Coverting the program into the machine code
It is a three step process :
1. **Preprocess :** Before compilation, the source code file is passed to the preprocessor, whose job is to include the code written in header files (libraries) into the source file.

2. **Compiling :** The modified source code is then passed to the compiler, whose job is to check whether the code is syntactically correct. It also marks the places where program elements like functions, variables, etc., are used. Once the compiler finishes, it produces an object file (with .o or .obj extension). This object file contains machine code along with references to functions, variables, and other program elements that are yet to be resolved.

3. **Linking :** The object file is then passed to the linker, whose job is to locate and connect the referenced functions, variables, and other program elements to their actual definitions.

> It’s like the compiler leaves blank spaces in place of functions and variables, and then the linker fills those spaces with the correct addresses or definitions of those elements. 

# 03 Conversion Specification in C

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

# 04 `printf()` and `scanf()`
- Both `printf()` and `scanf()` functions accept **formated string** as well as **conversion specifications**.
- The `printf()` function is used for **output formatting**, while `scanf()` is used for **input formatting**.
- `scanf()` is essentially a **pattern matching** function that tries to match the user’s input characters against the given conversion specifications.

**Example :** Reading a Fraction Input
```c
scanf("%d/%d", &x, &y);
```
If the user inputs a fraction in the form of `x/y`, `scanf()` matches the pattern and assigns the values to the variables accordingly.

```c
User Input : 12/44
x = 12, y = 44
```

Here, the slash `/` acts as a literal character in the format string.
- `scanf()` expects the user to input the same character (i.e., `/`) at that position.
- If the input does not match this pattern (for example, `12 44` without a slash), `scanf()` will stop reading at the point where the mismatch occurs.

**Example :** Reading a single digit (Width Specifier)

```c
int x,y,z;

scanf("%1d %1d %1d",&x, &y, &z);
```
If the user enters something like `345` or `3 4 5` each digit will be stored in a separate variable.

```c
User input : 345
x = 3, y = 4, z = 5
```

**Explanation :** 
- The number `1` in `%1d` is a field width specifier.
- It tells `scanf()` to read only one digit (or one character that fits the format) for each variable, even if more digits are available in the input buffer.
- Whitespace in the input (like spaces or newlines) is automatically ignored for numeric formats, so both `345` and `3 4 5` produce the same result.

>Note : Precision doesn't work with `scanf()`.

```c
scanf("%5.2d", &x);     // wrong
scanf("%5.2f", &y);     // wrong
```

# 05 Constants in C

In C constants are defined outside the `main()` function. 
```c
#include <stdio.h>
#define PI 3.14
#define INTEREST_RATE 10.25

int main(){
    printf("Interest rate is : %f", INTEREST_RATE);
}
```

# 06 Statements

- **Operators :** 

| Symbol    | Meaning                  |
| --------- | ------------------------ |
| **<**     | less than                |
| **>**     | greater than             |
| **>=**    | greater than or equal to |
| **<=**    | less than or equal to    |
| **==**    | equal to                 |
| **!=**    | not equal to             |
| **!**     | negation                 |
| **\|\|**  | logical or               |
| **&&**    | logical and              |


- **If statement :**

```c
if(condition){
    // statements
}else if(condition){
    // statements
}else{
    // statements
}
```

- **Ternary Operator :**

```c
condition ? runs_if_true : runs_if_false
``` 

- **Boolean values in C :** 
There is no built-in `boolean` data type in standard C (prior to C99). When we use logical operators for comparison, the result is an integer—`0` for `false` and `1` for `true`. To make conditional expressions more readable, we can create our own `BOOLEAN` “type” or include the `<stdbool.h>` header file. In either case, the underlying type is still an integer.

```c
#define BOOLEAN int
#define TRUE 1
#define FALSE 0

// example 
BOOLEAN isAdmin = TRUE;
```

- **Switch Statement :**

```c
switch (expression) {
    case constant_expression1 : 
        // statements
        break;
    case constant_expression2 :
        // statements
        break;
    default :
        // statements
        break;
}
```

# 07 Loops
- **While loop :**

```c
while(condition){
    // statements 
}
```

- **Do-While loop :**

```c
do {
    // statements
} while(condition);


// Example :
i = 10;
do {
    printf("%d", i);
    i--;
} while (i > 10);
```

- **For loop :**
 
```c
for (exp1; condition; exp2){
    // statements
}
```

# 08 Types in C

- **Integer Type :**
    - Integer type are divided into two categories : `signed` and `unsigned` (by default integer values are signed in C). 
    - `Signed` integer represents both `negative` and `positive` intgers (if MSB is `0` it suggests that number is a `positive` integer and when MSB is `1` it means that number is a `negative` number) while `unsigned` only represents `positive` integers. 
    - Size of integer type is usually 32 bits, but it can be 16 bits in older CPUs.
    - To construct a variable that meets our needs, we can specify that a variable is `long` or `short`, `signed` or `unsigned`.

    ```c
    short int a;
    unsigned short int a;

    long int a;
    unsigned long int a;

    long long int a;
    long long unsigned int a;

    int a;
    unsigned int a;
    ```

- **Integer Constant :**
    - **Decimal :** Contians digits from `0` to `9`, but must not begin with a `0`. For example, `12`, `467`, `8471` 
    - **Octal :** contians only digits between `0` to `7` and must begin with a `0`. For example, `017`, `099`, `037777`.
    - **Hexadecimal :** contains digits between `0` and `9` and letter between `a` and `f` and always begin with `0x`. For example, `0xf`, `0xff`, `0x7fff`. 
    - To represent a `long` integer  constant use `L or l` at the end of the digit and to represent an `unsigned` integer constant use `U or u`. 

    ```c
    // long integer constants
    15L     0377L       0x7777FL

    // long long integer constant
    0x4323DLL

    // unsigned integer constants
    15U     0377U       0x7777FU

    // we can use both U and L to show that constant is long and unsigned. Order of U and L
    // does not matter.
    0x777ffffffUL
    ```

>Octal and hexadecimal are nothing more than an alternate way of writing numbers. If we want we can use them with each other and it will work perfectly fine. `10 + 015 + 0x7fff` is a perfectly fine expression.

>General rule for determining the `type` of integer constant when no suffix(`u`, `l`, `ll`) is used : for decimal its `int`, `long int`, or `long long int` and for octal and hexadecimal its `int`, `unsigned int`, `long`, `unsigned long`, `long long int`, `unsigned long long int`. C compiler will automcatically chose the type to better represent the value of that constant. Compiler will search in this order. 

    ```c
    // for decimal :
    // int --> long int --> long long int

    // for hexadecimal and octal :
    // int --> unsigned int --> long --> unsigned long --> long long int --> unsigned long long int
    ```

- **Reading and Writing Integer :**
    - The format string `%d` only works for `int` type. Reading or writing and **unsigned**, **short**, **long** integer needs new conversion specifiers.
    - **Reading and writing unsiged integer :**
    ```c
    unsigned int a;

    scanf("%u", &a);    // reads unsigned int "a" in base 10
    printf("%u", a);    // writes unsigned int "a" in base 10

    scanf("%o", &a);    // reads unsigned int "a" in base 8
    printf("%o", a)     // writes unsigned int "a" in base 8

    scanf("%x", &a);    // reads unsigned int "a" in base 16
    printf("%x", a);    // writes unsigned int "a" in base 16
    ```
    - **Reading and writing short integer :**
    ```c
    // put letter "h" in front of conversion specifier
    short int a;

    scanf("%hd", &a);   // reads short signed int "a" in base 10 
    printf("%hd", a);   // writes short signed int "a" in base 10

    scanf("%hu", &a);   // reads short unsigned int "a" in base 10
    printf("%hu", a);   // writes short unsigned int "a" in base 10

    scanf("%ho", &a);   // reads short unsigned int "a" in base 8
    printf("%ho", a);   // writes short unsigned int "a" in base 8

    scanf("%hx", &a);   // reads short unsigned int "a" in base 16
    printf("%hx", a);   // writes short unsigned int "a" in base 16
    ```
    - **Reading and writing long integer :**
    ```c
    // put letter "l" in front of conversion specifier
    long int a;

    scanf("%ld", &a);   // reads long signed int "a" in base 10 
    printf("%ld", a);   // writes long signed int "a" in base 10

    scanf("%lu", &a);   // reads long unsigned int "a" in base 10
    printf("%lu", a);   // writes long unsigned int "a" in base 10

    scanf("%lo", &a);   // reads long unsigned int "a" in base 8
    printf("%lo", a);   // writes long unsigned int "a" in base 8

    scanf("%lx", &a);   // reads long unsigned int "a" in base 16
    printf("%lx", a);   // writes long unsigned int "a" in base 16
    ```
    - **Readind and writing long long integer :**
    ```c
    // put letter "ll" in front of conversion specifier
    long long int a;

    scanf("%lld", &a);   // reads long long signed int "a" in base 10 
    printf("%lld", a);   // writes long long signed int "a" in base 10

    scanf("%llu", &a);   // reads long long unsigned int "a" in base 10
    printf("%llu", a);   // writes long long unsigned int "a" in base 10

    scanf("%llo", &a);   // reads long long unsigned int "a" in base 8
    printf("%llo", a);   // writes long long unsigned int "a" in base 8

    scanf("%llx", &a);   // reads long long unsigned int "a" in base 16
    printf("%llx", a);   // writes long long unsigned int "a" in base 16
    ```
    - To conclude : `d` represents signed integer. `u` represents unsigned integer. `o` represents integer in octal form. `x` represents integer in hexadecimal form. `l` represents long. `ll` represents long long. `h` represents short.

- **Floating type :**
    - C provides three floating types : `float`, `double` and `long double`.
    ```c
    float a;
    double a;
    long double a;
    ```

- **Floating Constants :**
    - Floating constants can be written in variety of ways.
    ```c
    57.0    57.     57.0e0      57E0        5.7e1       5.7e+1      .57e2       570.e-1  
    ```
    - By default floating constants are stored as `double`.
    - To force compiler to store floating constant as `float` or `long double` use suffix `f or F` and `l or L` respectively. For example : `57.0F` represents float. `57.0L` represents long double.

- **Reading and Writing floating point numbers :**
    ```c
    printf("%f", a);     // writes float "a" 
    printf("%f", a);     // writes double "a"
    printf("%LF", a);    // writes long double "a"


    scanf("%f", &a);      // reads float "a"
    scanf("%lf", &a);     // reads double "a"
    scanf("%Lf", &a);     // reads long double "a"
    ``` 

- **Character type :**
    - Character are treated as small integer in C and they are enclosed in single quote.
    ```c
    char ch = 'a';
    ```
    - Characters can be **signed** or **unsigned** just like integers.
- **Reading and Writing Characters :**
    - `%c` specifier is used to read and write characters.
    ```c
    char ch;

    scanf("%c" , &ch);      // reads a single character.
    scanf(" %c", &ch);      // skips the white space then reads the character.

    printf("%c", ch);       // writes a single character.
    ```
    - C provides alternate way of reading and writing character : `getchar()` and `putchar()`. `getchar()` functions returns an integer thats why you might see some people using int type to store character value.
    
    ```c
    char ch = 'a';

    // write character
    putchar(ch);

    // read character
    ch = getchar();
    int chh = getchar();    // using int to store character.
    ```
- **Type Definiation :**
    - Earlier we used `#define` directive to create a `Boolean` type. There's a better way to do the same thing using `typedef`.

    ```c
    typedef int Bool;

    Bool isAdmin;
    ``` 
    - Using `typedef` to define `Bool` cause the compiler to add `Bool` to the list of type names that it recognizes. `Bool` now can be used in same way as built-in type.
    - Type defination can make program more understandable.
    ```c
    typedef float Dollars;
    Dollars cash_in, cash_out;

    // above case is more informative then writing 
    float cash_in, cash_out;
    ```

# Array
- Array is a data structure which stores data of same type. 
- One dimensional array is a simplest type of array. Conceptually elements of 1D array are arranged one after another in a single row (or column, if you prefer).
- To declare an array, array type and number of elements its going to have is declared beforehand.

```c
int arr[10];
```

```c
// array initialization 

int arr[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

- Initializing few elements of an array explicitely.
```c
int arr[10] = {[2] = 29, [9] = 7, [14] = 48};
```

- Multi dimensional array :

```c
int arr [3][4];
```

```c
int arr[2][2] = {
    {1, 2},
    {3, 4}
};
```

```c
// explicit declaration

int arr[2][2] = {[0][0] = 1, [1][1] = 1};
```

