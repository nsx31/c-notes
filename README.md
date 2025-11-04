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

# Format Specifier

```c
%d      // integer
%f      // float
%c      // character
%p      // pointer
%.2f    // float, print 2 digits after decimal (by default float prints 6 digits after decimal). 
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