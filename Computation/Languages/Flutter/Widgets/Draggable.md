# Draggables

## Multiple draggables
```
final List<Draggable> draggables = <Draggable>[
  Draggable(
    data: 1, 
    child: Container(width: 100.0, height: 100.0, color: Colors.blue,), 
    feedback: Container(width: 120.0, height: 120.0, color: Colors.teal,) 
  ),
  Draggable( 
    data: 2, 
    child: Container(width: 80.0, height: 80.0, color: Colors.orange,), 
    feedback: Container
```
## Can many draggables share the same feedback?
AI: Yes, multiple Draggables can share the same feedback. The feedback widget is a constructor argument which is shared across all Draggables, so you just need to declare it once for all. Here's an example of how to do it: 
```
final widget feedback = Container(width: 120.0, height: 120.0, color: Colors.teal);

final List<Draggable> draggables = <Draggable>[
  Draggable(
    data: 1, 
    child: Container(width: 100.0, height: 100.0, color: Colors.blue,), 
    feedback: feedback
  ),
  Draggable( 
```

## Arguments
**data** is a generic type to assign a value to the Draggable, while the argument 

**child** is the widget that will be dragged. 

**feedback** is the widget that will be shown as the Draggable is dragged. Finally, the argument 'affinity' is an optional parameter to set the axis on which the Draggable will move.

## What 'data' means?
It is a generic type so you can use any data type you need.

It is used to set an identifier for the Draggable so you can use it in your code to determine which Draggable was dragged.

## How can I use a photo as a draggable?
 
```
final widget myDraggablePhoto = Draggable(
  data: 1, 
  child: Image.asset('assets/img.jpg'), 
  feedback: Container(width: 120.0, height: 120.0), 
);
```