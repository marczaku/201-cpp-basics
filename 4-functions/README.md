# 4 Functions

Logical units inside the source code. Goal: Reusable Code.
- saves time
- reduces complexity, error-proneness

## IPO Principle
- Input (Parameters)
- Processing (Function Body)
- Output (Return Value)

## Definition

```cpp
void printHello() {
  printf("Hello!\n");
}
```

## Invocation

```cpp
int main() {
  printHello();
}
```

## Parameters

```cpp
void printSum(int a, int b){
  printf("%d", a+b);
}
```

## Invocation with Parameters

```cpp
printSum(3, 5); // 8
```

## Return Type

```cpp
int addNumbers(int a, int b) {
	return a + b; // need to return a value matching the return type!
}
```

## Return (void)

You can use `return` in `void`-type functions as well
- this will end the function execution instantly
- and execute none of the remaining lines of code

```cpp
void buyAlcohol(int age){
  if(age < 18){
    return;
  }
  printf("Bought alcohol!\n");
}
```

## Using Return Value

```cpp
int result = addNumbers(3, 5); // 8
printf(result);

// or:
printf(addNumbers(4, 6)); // 10
```

## Fun Fact: Void Parameter

In the early days, you had to explicitly express if your function had no parameters:
- by using `void` as parameter list

You can still do that today!
- but you should not

```cpp
void sayHello(void){
  printf("Hello!\n");
}
```

## Call Stack

Remember, how the Call Stack works!

```cpp
void bar(int number){
  printf("bar %d\n", number);
}

void foo(){
  printf("before bar\n");
  bar(1);
  printf("after bar\n");
}

int main(){
  printf("before foo\n");
  foo();
  printf("after foo\n");
  bar(2);
}
```

## Order Matters
This won't compile because `bar` is not defined when `foo` is defined:
```cpp
void foo(){
  bar();
}
void bar(){}
```

### Inefficient Solution: Reorder
You can reorder the code to ensure that the needed functions always comes first
```cpp
void bar(){}
void foo(){
  bar();
}
```

This also wouldn't work for this example:

```cpp
void bar(){
  foo();
}
void foo(){
  bar();
}
```

### Better Solution: Forward-Declaration
You can declare functions before defining them. This makes sure that the order won't matter
```cpp
// declare the functions before defining them:
void bar();
void foo();

// now, define them. The order doesn't matter anymore.
void bar(){
  foo();
}
void foo(){
  bar();
}
```