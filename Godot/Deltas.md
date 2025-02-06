> The movement speed of our game is determined by how fast the game runs (How many frames are generated)

This conundrum can be bad, because people will better laptops will run the game "faster", as in objects in game will move faster, which of course will be problematic, we want the game to run exactly the same despite the device used

![[{053FE8E4-3ED1-4E5C-93C1-2D33F7EA9C9A}.png]]

This will cause the game to run inconsistently on different systems.


So for this, we have a delta time

**Delta** -> Delta time measures how long it took to create on frame

For example, if the framerate is 60fps, then delta time is 1s/60 = 0.0167, or about 17 millisecond

We can use this information to keep the same constant speed regardless of framerate, we essentially multiply any movement with the delta time

![[{7D213EB3-3EE3-4EC0-9656-167C680720C2}.png]]

