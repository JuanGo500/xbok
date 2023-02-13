# Classes

## Create a class
```
class Cat:
    # class attributes 
    species = "Felis catus"
    color = "brown" 

    # class methods 
    def make_sound(self):
        print("Meow!")

    def chase_mouse(self):
        print("The cat is chasing the mouse.")
    
    pass
```

## Create a class with a constructor
```
class Person:
    def __init__(self, name):
        self.name = name
```

If is creates an object
```
class Person:
    def __new__(cls, name, age, gender):
        instance = super().__new__(cls)
        instance.name = name
        instance.age = age
        instance.gender = gender
        return instance
```
cls stands for class