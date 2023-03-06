
## 5 Input

### Read Character: getchar

```cpp
printf("Do you want to continue? y/n");
char c = getchar();
{ // clear unparsed characters from the buffer
	char _c;
	while ((_c = getchar()) != '\n' && _c != EOF);
}
switch(c){
	/*...*/
}
```

### Read String: fgets

Later (Requires Pointer Knowledge)

### Read Format: scanf

```cpp
// required to allow using scanf on Windows
#define _CRT_SECURE_NO_WARNINGS
#include <cstdio>

int main() {
    for(int i = 0; i < 5; i++)
    {
        AskAgain:
        // ask for input
        printf("Give me two numbers. e.g. 3, 7\n");
        // declare variable to store the information in
        int num1, num2;
        // read input from the console. Returns the number of successfully parsed arguments 
        int result = scanf("%d, %d", &num1, &num2);
        
        { // clear unparsed characters from the buffer
            char c;
            while ((c = getchar()) != '\n' && c != EOF);
        }

        // if not both numbers were provided, we go back to asking again
        if(result != 2) goto AskAgain;
        // else, we can print the average of both provided numbers:
        printf("The average is %d.\n", (num1+num2)/2);
    }
}
```