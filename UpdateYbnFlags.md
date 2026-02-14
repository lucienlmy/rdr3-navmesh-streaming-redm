# Intro
When using a custom navmesh, it is important to update the collision (.ybn) flags and re-stream the updated .ybn in order to properly support the new navmesh.  
This is important in the case of a navmesh tile being placed on the edge of the world or outside the vanilla playable area (i.e. Nuevo Paraiso, "Canada", etc.) to ensure your navmesh works as intended.

Here are some important flags to consider. Flags can be viewed inside Blender (Object Mode -> Select Collision Tile -> Material Properties -> Sollumz -> Collision Flags) or a full list found [here](here). 
Keep in mind most are untested and are assumed usage. Feel free to document these flags to confirm usage:

- NO NAVMESH
Disable support for navmesh.

- NOT CLIMBABLE
Untested, disables support for climable surfaces.

- TOO STEEP FOR PLAYER
Untested, enables "sliding" when getting close to cliff/map edges.

- STAIRS
Untested. Stairs?

