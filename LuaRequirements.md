# Lua Requirements

While C++ will be used for the core rendering and physics of the game, Lua will be used to handle high level game logic and possibly networking in the future.

Lua will interact with the C level through structs/classes/functions exposed to it.

# Entities

All entities (Keys, Diamonds, Icemen, etc) are exposed to Lua, allowing it to program logic for these entities.
C++ would handle the rendering of their models and general graphics behaviour.

All entities will contain these functions that are called on the C-side and act as a programmable hook on the Lua side.

* Init

Called on C-side when the entity is created, this is where Lua can run initialisation code for the entity.

* Update

Called every frame, this is mostly utilised by Lua for handling behaviour.

# Entity Properties

Entities will have all its properties exposed to Lua to allow behaviour control.

Common properties present in almost all entities are:

* Vector3 Position
 
Represents the position of the entity.
 
* Vector3 Rotation

Represents the rotation of the entity.

* Vector3 Velocity

Represents the velocity of the entity, writing to this property will allow Lua to create dynamic moving objects.

# Physics API

* Physics.OnCollision(ENTITY,FUNC)

Fires given FUNC when ENTITY collides with another entity.

# World API

* World.GetEntities(TYPE)

Returns a Lua table of all entities of TYPE in the game, if TYPE is nil, it returns all entities.
