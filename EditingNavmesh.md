This tutorial is extremely basic and will be updated with time.

### 1. Start with a fresh navmesh using the tutorial
![screenshot of freshly generated navmesh](/ButterBridgeTutorial/assets/newmesh.png)

### 2. Hide or delete the collisions.
![screenshot of hiding ybn collisions](/ButterBridgeTutorial/assets/hideterrain.png)

-- View of navmesh properties tab under object properties --  
![screenshot of navmesh properties](/ButterBridgeTutorial/assets/properties-attributes-flags.png)

-- View of navmesh polygon render flags --  
![screenshot of render flags](/ButterBridgeTutorial/assets/render-flags.png)

-- View of navmesh without collisions --  
![screenshot of ](/ButterBridgeTutorial/assets/newnav-full.png)

### 3. Enter Edit mode - select faces
![screenshot of edit mode](/ButterBridgeTutorial/assets/edit-mode.png)

### 4. Decimate mesh faces (optional - fill mesh `F` and merge vertices on distance?) Then highlight faces for un-navagable terrain to delete.
![screenshot of decimate](/ButterBridgeTutorial/assets/decimate-and-delete.png)

### 5. DELETE -> Dissolve Vertices -> DELETE -> Vertices THEN Select new dissolved Face -> DELETE -> Vertices 
![screenshot of dissolve vertices in delete menu](/ButterBridgeTutorial/assets/dissolve-vertices.png)

-- View of deleted faces for un-navagable terrain --  
![screenshot of post dissolve + delete](/ButterBridgeTutorial/assets/dissolved-deleted.png)

### 6. Select polygons that require flags, "Update Poly Flags" In this example it's a river, so we use the "Water" polygon attribute with the "Water" polygon render where the navmesh meets the riverbed.
![screenshot of riverbed editing](/ButterBridgeTutorial/assets/face-edit-flags.png)

-- View of the "Update Poly Flags" button --  
![screenshot of update flags button](/ButterBridgeTutorial/assets/update-flags.png)

### 6a. Add the necessary flags to other polygons, or delete polygons where there is no navmesh needed. In this example, I add "Danger Keep Away 2" and "Steep Slope" attributes to the cliff faces, then add "Danger Keep Away 2" polygon render.
![screenshot of cliff face](/ButterBridgeTutorial/assets/cliff-face-flags.png)

### 7. File -> Export XML | Open CodeX.Explorer -> Import XML | Grab newly minted .ynv and view in the CodeX 3D Viewer. Your navmesh should be ready for the /stream/ folder and have a "properly" defined navmesh.
![screenshot of the "final" product](/ButterBridgeTutorial/assets/'final'-product.png)

### Final Notes:
Any navmesh that intersects or replaces vanilla navmesh (as shown in this example) will have alignment issues. You *will* need to fix those by aligning your navmesh tile edges correctly in Blender, or deal with improper alignment which affects NPC pathing. 

I do not currently have the knowledge on editing existing navmeshes, you can however generate new navmeshes, then replace vanilla ones using this method. Replacing vanilla navmeshes with a newly generated one (as opposed to a direct edit) will also require a setup of roads, interiors, and other polygon/edge flags for proper NPC pathing.

