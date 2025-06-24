
# Shortest Path
- Compare self vs opponent's shortest path to the end tile.
- Opponent has shorter path:
	- Block with walls
- We have shorter path:
	- Move/Copy enemy move?

Simple but fragile strategy
Shortest path can be easily altered by opponent's walls (Shortest path when blocked leads to a way longer path)
Automatically implement rules, since we can't put wall that causes enemy or player to have 0 paths available.
