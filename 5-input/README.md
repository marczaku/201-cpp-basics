
# 5 Input

## Old, C-Style

```cpp
#include <cstdio>
```

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

### Read Format: scanf_s

#### Simple

```cpp
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

```cpp
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

```cpp
#include <iostream>
```

```cpp
cout << "Do you want to continue? y/n");
char c ;
cin >> c;
switch(c){
	/*...*/
}
```

### With Error-Handling

```cpp
#include <iostream>

using namespace std;

int main() {
    for (int i = 0; i < 5; i++)
    {
        cout << "Give me a number." << endl;
        // declare variable to store the information in
        int num1;
        while (!(cin >> num1))
        {
            cin.clear();
            cin.ignore(1000000, '\n');
            cout << "That's not a valid input, try again." << endl;
        }

        // else, we can print the average of both provided numbers:
        printf("Half of that is %d.\n", (num1 ) / 2);
    }
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