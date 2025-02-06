
# Nodes


> Nodes are basic elements in godot, it can be an image, sound, timer, etc

Nodes are building blocks in godot, it can represent anything in the game, and we combine nodes to make various parts of our game. For example, there is one node for an enemy, and several children nodes inside of the scout to create a full fledged enemy for the game

![[{5D9CFACB-8043-45E1-AD8B-4BEDBDBD3A56}.png]]


There are tons of nodes available in godot, we can utilize those nodes to create parts of our game. We can also edit the properties of a node with the inspector located in the right

as we know, we can target nodes in 2 ways:
- get_node("node path")
- $node_path -> Most used one

Nodes also act like classes where it has properties, and built in methods

we should also give nodes unique names so it's easier to identify the different nodes, this is useful when we have lots of nested nodes, and it's getting hard to access those nodes using paths like `$node/node1/node2/target`. We can assign a node a unique name by right clicking, and select "access as unique name". So next time, we can just access that node directly by using a percentage sign `%target`.

A major aspect of Godot is to make nodes communicate with each other. Especially later on when we will be working on multiple scenes together

# Scenes

A scene:
- Organizes nodes
- Displays nodes

The scene is located in the middle of the screen, and it displays whatever nodes we have selected.
We can also place scenes inside of scenes. There can be more than one instance of a scene.


So far, we created scenes in the editor, but doing that isn't always possible in the game. For example, when we want to create a laser that shoots from a gun, but the lasers are dynamically generated. So for this, we can use a code to instantiate a scene.

Steps:
1. Create a scene
2. Create an instance of the scene
3. We need to add the scene to the node tree


