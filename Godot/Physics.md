
# Area2D

an area that can check if another body entered the hitbox. This can be moved by changing the position. Basically an empty hitbox, useful for a lot of things. 


# StaticBody2D

A static body that other bodies collide with, this node is not supposed to be moved. Example: Walls, beds, obstacles, etc.


# RigidBody2D

Moving body that moves via physics (Like a projectile), we have to set an initial velocity. Ex: Grenade, cannonball, etc

# CharacterBody2D

Moving body controlled by code, has inbuilt methods. Ex: Any entity controlled by code (The player, enemies, bosses, etc)


# Collision

Every CollisionObject has a collision layer
We can place objects on layers to make them interact with objects on other layers

This is done via a layer and a mask

"Layer" determines on which the layer the object exists in
"Mask" determines which layer it can interact with

We can have multiple layers for:
- Player
- Enemies
- Objects
- Projectiles
- Items & Zones

So for example, the player can exist on a player layer, and the mask can interact with all other layers

Each enemy will be on the enemies layer, and the mask will be for the player, the objects, and the projectiles