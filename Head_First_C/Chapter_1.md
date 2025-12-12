```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    char card[3];
    int val=0;

    puts("pull a cad:");
    scanf("%2s", card);

    if(card[0]=='k'){
        val=10;
    }else if(card[0]=='q'){
        val=10;
    }else if(card[0]=='j'){
        val=10;
    }else if(card[0]=='a'){
        val=11;
    }else{
        val=atoi(card);
    }

    printf("val: %d\n", val);

    return 0;
}
```

## What did I learnt?
- How to take/store **string** input and how to display **string** as output.
- String is basically a charcter array:
    ```c
    char name[7] = "nikhil";  //{'n', 'i', 'k', 'h', 'i', 'l', '\0'};
    ```
- Always make your character array one byte larger than the string you want to store, because the final byte is used for the \0 terminator.
- We can write above code using **switch** statement as well : 

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    char card[3];
    int val=0;

    puts("pull a cad:");
    scanf("%2s", card);

    switch(card[0]){
        case 'k': 
        case 'q': 
        case 'j': 
            val=10;
            break;
        case 'a':
            val=11;
            break;
        default :
            val=atoi(card);
            break;
    }

    printf("val: %d\n", val);

    return 0;
}
```
