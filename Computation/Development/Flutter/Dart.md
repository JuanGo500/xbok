# Dart Core Syntax

## Basics
- All that goes into a variable is an object
- Every object is an instance of a class
- Functions are objects

## Types
Seven primitive types
- int
- double
- bool
- dynamic
- String
- List
- Map

## String interpolation
$ symbol allows to insert numbers in a string.

```dart
var x = 10;
  print('número de veces: ${x+x}');
```



## Collections
### Lists
```dart

final aSetOfStrings = {'one', 'two', 'three'};
final aMapOfStringsToInts = {
  'one': 1,
  'two': 2,
  'three': 3,
};

List aList = [1, 2, 3];
List<String> ls=["uno","dos","tres"];
ls[0] // this returns "uno"
```

### Maps

```dart
Map<String,int> aMap={
  'A':10,
  'B':20,
  'C':30,
}
```
aMap['A'] \\this returns 10

## Variables
Variables can be declared:
- var casa; //inferred type
- int casa; //explicit type

## Functions
- Types are not necessary but recommended.

```dart
add(a,b){
  return a*b;
}

int add(int a,int b){
  return a*b;
}
```
- A function can be assigned to other function
```dart
Function fun
fun=add
var result= fun(10,20) //result is 200
```
- A function can be sent to another function

```dart
add(x,y){return x*y;}
int anotherFunction(Function op, x,y){return op(x,y);};
print(anotherFunction(add,10,30));
```
- Another signature without curly brackets/return
  
int add(int x, int y)=>x+y
int sub(int x, int y)=>x-y

- A function can return another function

```dart
int add(int x, int y)=>x+y;
int sub(int x, int y)=>x-y;

choose(int a){
  if(a>10){return add;}
  else{return sub;}
}
Function funcionFinal=choose(51);
print(funcionFinal(10,20));
```
- A function can be a member of a list

List aList=[add,sub];
print(aList[0](10,20)); //prints 30 

- Closures are anonymous functions

(a,b)=> print(a+b); //with arrow
(a,b){print(a+b)};  //with curly braces


# References

## Specification
https://dart.dev/guides/language/specifications/DartLangSpec-v2.2.pdf


## Core libraries
https://api.dart.dev/stable/2.12.1/index.html

## Basic types and functions
https://www.youtube.com/watch?v=8F2uemqLwvE
