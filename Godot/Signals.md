

in [[Physics]], we have learned the different collision body 2D's one of them being Area2D. To recap, Area2D checks if another body has entered. But as of now, using a plain Area2D is pointlesss, we just have an empty invisible area.

We need to add functionality so that this area actually does something, and for that, we need 
<u>signals</u>


**Signals**
when a certain action happens to a node: Like a body entering an area, a timer running out, 2 bodies colliding

We can tell the affected node to send a signal, basically ask a script to execute, this can be a powerful way to make nodes communicate with each other


## Create custom signals

We can create our own signals, because the major limitations of signals right now is that they only work between nodes in the same scene, and triggering custom signals can help communicate between scenes.

The custom signal will be located in the root node of where we want our signal to be. Then we connect our signal to that root node first. Then, we create a custom signal in the root node using the `signal` keyword

Keep in mind we also have to put the logic of <u>when</u> we want to emit the signal in the root node of the source signal.