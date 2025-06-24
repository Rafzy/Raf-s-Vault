
# Games and AI

**Tripe A** industry -> Fewer games, bigger budget (Up to 500 million dollars).
**Indie** industry -> More games, varying budget

**Millington's AI Model**
AI gets given processor time -> Execution management
AI may get it's information from world interface, which affects the character AI (Influences their decision making and movement), or in a more advanced system, may affect the group AI of enemies (May affect multiple enemy's strategy)

**Search vs Knowledge**
Knowledge based systems were the most common approach to building an AI system in the early days, but this system were proved to be fragile.

Deep learing represents the pinnacle of computationally intensive search.
AlphaGo Zero was provided with limited knowledge of the game's rules but was granted extensive processing time to explore various strategies

Compared to explicitly instructed AI characters, for example:
`IF injured THEN use health pack`

The only way for algorithms to outperform another is to either consume more processing power, or the algorithm must be optimized for specific problems.

Games are intended to be run on customer hardware, but most of the processing power in games are mostly dedicated to **graphics** nowadays.

So, AI designed to operate on games, low computation/high knowledge approach emerges as the most successful

**Complexity Fallacy**
It's common to think that complex AI = better character behavior, but this is not true

Example:
In black and white (2001), players ended up teaching NPCs bad habits

Some characters or enemy might only appear to the player for a short amount of time, not necessary for the player to understand it's AI.

It's important:
- Make sure a characte's AI matches it's purpose in the game
- A change in behavior is far more noticeable than the behavior itself

Layers of game AI (Academically speaking):
- Operational level, eg: Pathfinding of a single soldier
- Tactical level, eg: decision to move the units to attack the opponent
- Strategic, eg: long-term planning of the moment to attack in order to win the game

Adaptive game AI:
- Offline learning -> Takes place before the game is released, making the AI play a certain number of games to optimize it's strategies
- Supervised learning -> While the game is being played by a human, it receives immediate feedback
- Online learning

The AI learns the player's choices to make better suggestions by using machine learning methods. The designer must understand how AI is making a decision, avoiding a "black box"

This is why, neural networks are avoided in games, typically **probabilistic reasoning** is used.

The AI must meet requirements:
- Computationally fast
- Stronger than manually programmed AI
- Robust to randomness
- Efficient in learning


Different types of AI in games:
- "Good AI" -> Beat player's
- "Fun AI" -> Focus on player's experience

Types of games:
- Symmetrical games -> AI is forced to play the same games as humans
- Asymmetrical games -> The AI can be tuned to optimize the player's difficulty level


# Game Design

**Components in games**
- Concept
- Graphics
- Sound
- Story
- Interface
- Game Mechanics
- Database 
- AI
- Networking
- Security


# PCG

PCG (Procedural Content Generation) -> Set of techniques that can potentially make games more replayable

