
# 5 Input

## Old, C-Style

```c++
#include <cstdio>
```

### Read Character: getchar

```c++
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

```c++
char buffer[100];

// Read a string from the console
if (fgets(buffer, sizeof(buffer), stdin) != nullptr) {
    // Remove the newline character at the end, if present
    size_t length = strlen(buffer);
    if (length > 0 && buffer[length - 1] == '\n') {
        buffer[length - 1] = '\0';
    }

    printf("You entered: %s\n", buffer);
} else {
    // Error handling if fgets fails
    printf("Error reading input.\n");
}
```

### Read Format: scanf_s

#### Simple

```c++
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
        int result = scanf_s("%d, %d", &num1, &num2);
	
        printf("The average is %d.\n", (num1+num2)/2);
    }
}
```

#### With Error Handling

```c++
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
        int result = scanf_s("%d, %d", &num1, &num2);
        
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

## New, C++ Style

### Simple

```c++
#include <iostream>
using namespace std;
```

```c++
cout << "Do you want to continue? y/n");
char c ;
cin >> c;
switch(c){
	/*...*/
}
```

### With Error-Handling

```c++
int main() {
tryagain:
    cout << "\nGive me two numbers Separated by Comma. Like -2,5\n";
    int firstNumber;
    int secondNumber;


    if (cin >> firstNumber >> ws && cin.peek() == ',' && cin.ignore() >> secondNumber) {
        cout << "success!";
    }
    else {
        cout << "nope!";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
        goto tryagain;
    }
    cout << "Higher Number is : " << (firstNumber > secondNumber ? firstNumber : secondNumber) << "\n";
}
```

## EXERCISE
Ask the user for his age, then return the next year.
```
Output: What's your age?
Input:32
Output: Next year, you'll be 33!
```

## EXERCISE
Ask the user for a character, then return the character before that.
```
Output: Give me a character.
Input:E
Output: Before that comes D.
Output: Give me a character.
Input:Z
Output: Before that comes Y.
Output: Give me a character.
Input:A
Output: Before that comes Z.
```

## EXERCISE
Ask the user for a time in seconds. Print the time in Hours Minutes and Seconds.
```
Output: How many Seconds have passed?
Input:4567
Output: 01:16:07
```

## EXERCISE
Ask the user for their name. Greet the user.
```
Output: Hi, what's your name?
Input:Marc
Output: Hello, Marc!
```
