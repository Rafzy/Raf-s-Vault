> GDScript is the most used scripting language in godot, but godot also provides other scripting languages like C# and C++. GDScript is widely used because of it's similarity to python and javascript, which are generally considered easier to understand compared to C# and C++


**GDScript**
If python and javascript had a child


# DataTypes

Basic datatypes like usual, you have strings, int, float, bool, and <u>dicts</u>

**Variables**

``` typescript
var current_speed = 200 
const max_speed = 300
```

We can also implicitly declare the datatype of a variable like typescript

```typescript
var a_string : String = "test"
var a_number : int = 123
var switch: bool = true
var some_numbers: Array[int] = [1,2,3,4]
```


# Functions

We create functions with func, other than that it's very similar to python's function structure

```typescript
func test_function(param_a : int, param_b: String) -> bool :
	return true
```

in the function above, we declare that it takes in param_a as an integer, param_b as a string, and it returns a boolean. If we don't specify a return value, void is returned like in Python.

There are a lot of in built funcitons, all of them starts with an _ , examples like:
- _ ready() is run when a node is added to the node tree
- \__ process() is run on every frame of the game

we can target other nodes from our current node, we can do this in two ways:
- get_node("node path")
- $node path <- more commonly used
# Classes

A script is always added to a node. The node will act like a class and have default methods and attributes. Adding a script to a Node2D creates an object with attributes of position, rotation, scale, etc.

