# Navigate

## Basics
```
() => Navigator.push(context, MaterialPageRoute(builder: (context) => NewView()))
```
You navigate by using an anonymous function that pushes a route into Navigator.

Navigator manages a stack of routes.

A route is created using another anonymous function as a parameter. This function takes context as a parameter and creates an object of the target view class.

It is possible to send objects through the initialization method of the target page.

## Pass a parameter
It is possible to pass information to the new page through a named parameter.
```
//Source class
() => Navigator.push(context, MaterialPageRoute(builder: (context) => NewView(message:"A message")))

//Target class
String message
class AClass {
AClass (this.message)
}
```

## References
https://flutter.dev/docs/cookbook/navigation/navigation-basics
