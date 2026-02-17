// todo //
# Editing Vanilla Navmesh  
**When making edits to a vanilla navmesh it is important to remember that this is a poorly documented and complex task. I HIGHLY recommend you first familiarize yourself with the other guides, especially those who are new to Blender or CodeX.**  
As of right now, you cannot simply "delete" polygons out of an existing navmesh. Breaking any links/nodes will cause corruption, either to parts of the tile or the entire .ynv file.  
Notable signs of corruption:  
> 1. Crash when entering the area.  
> 2. Crash when NPC attempts to utilize navmesh.  
> 3. NPC refusing to enter navmesh tile area.  
> 4. Broken pathing - running in circles, taking "odd" routes to destinations.  


Files used in this tutorial can be found [here](BlackwaterTutorial)  
## 1. Locate and export .ynv files using CodeX  
For this guide, we will be editing the Blackwater Town Square tile. After setting our viewer to show Navmesh, select our tile to view the file path.  
![screenshot of CodeX viewer with a navmesh tile selected, filepath in properties]()  

Open this filepath in CodeX.Explorer  
```/path/to/ynv/rpf/ynv/rpf/etc```  
![Screenshot of CodeX.Explorer pointing to the /path/ of our .ynv]()  

and export the file.  

## 2. Import into Blender 
**IMPORTANT! Depending on the full scope of your edits, you may want to [update the material flags](UpdateYbnFlags.md) for the vanilla collision! If you are unsure, you can skip this.**  
File -> Import CodeX .xml  

## 3. Edit your navmesh  
This step can be the trickiest. There are a myriad of issues that can occur from improperly editing a navmesh, and once those are solved you may still not have the desired result.   

For starters here are a list of things to AVOID:  
- Deleting polygons, links, or nodes.  
- Splitting polygons from the mesh. (hotkey Y or Right Click -> Split)  


