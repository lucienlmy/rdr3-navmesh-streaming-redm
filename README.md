# rdr3-navmesh-streaming-tutorial
*  **Prerequisites:** A RedM server, [CodeX](https://www.patreon.com/c/dexyfex/posts), [RDR2SollumzNavmesh](https://github.com/Foxxyyy/RDR2SollumzNavmesh) and Blender 4.0+ (Tested on 4.5)
# Tutorial: Streaming Custom .ynv Navmesh Files in RedM
>   **Author:** [charlie](https://github.com/charlietonygene)
# **Special Thanks:** 
*  [Mr. Steve](https://github.com/sly2791/) for the information! 
                    [Jannings](https://github.com/BurntJannings/) for testing and finding out more!

## Overview
Navmesh files (.ynv) can be generated using existing collisions extracted with CodeX (tested with 0.28 & 0.29) using the [RDR2SollumzNavmesh](https://github.com/Foxxyyy/RDR2SollumzNavmesh) plugin in Blender. 
This tutorial will guide you on how to extract collisions, import them to Blender, generate a new navmesh, export/import the files through CodeX and finally stream the resulting Navmesh inside your RedM server.

Please note that this is only generates "blank" navmeshes that do not automatically have the polygon flags relevant to the base game. See [Editing Navmeshes](EditingNavmesh.md) for more information on adding those flags before exporting from Blender.

## Notes:
> Navmesh will only generate if the collision provided has an area of at least 150x150.
>   
>  There is a lot of info missing from this tutorial that I will add over time!  
---

## 1. File Structure & Preparation
Create a new RedM resource with any name. We will be calling it "navmesh". Create an fxmanifest.lua and an empty folder named "stream"
*  `MyRedMServer/resources/navmesh` is our main directory
*  `MyRedMServer/resources/navmesh/stream` where we will put the resulting .ynv
*  `MyRedMServer/resources/navmesh/fxmanifest.lua` defines our resource. An example is provided below:

```fxmanifest.lua
fx_version 'adamant'
games { 'rdr3' }
rdr3_warning 'I acknowledge that this is a prerelease build of RedM, and I am aware my resources *will* become incompatible once RedM ships.'
this_is_a_map 'yes'
lua54 'yes'

  files {    
  'stream/*.ynv'
  }
```
`ensure navmesh` in the server.cfg

## 2. Use CodeX to grab collisions.
Open CodeX.Explorer
Navigate to your desired collision(s). For this example we will be using these files:
*  s_07_collision_0
*  s_07_collision_1
*  s_07_collision_2
*  s_07_collision_3

Which can be found in CodeX.Explorer here:
`RDR2\levels_6.rpf\levels\rdr3\terrain\rstu_07_10\s_07_.rpf`

Highlight those files then Right Click -> Export XML...


## 3. Importing to Blender
*   Open Blender and ensure [RDR2SollumzNavmesh](https://github.com/Foxxyyy/RDR2SollumzNavmesh) is installed and enabled.
  1.  From an empty scene: File -> Import -> CodeX XML - Select the .ybn.xml files that were exported from CodeX
  2.  Open the "Sollumz Tools" sidebar. Highlight all objects in the scene.
  3.  Under the "Navigation Mesh" dropdown menu, check "Compute Edge Neighbors" then select "Generate Navmesh from Collision"
  4.  Wait. The bigger the collision, the longer it will take. Be patient.  
>  4a. If you see "0 Navmeshs Created", make sure you have enough terrain to cover a 150x150 space to generate the navmesh.  

>   4b. If you STILL see "0 Navmeshes Created" highlight all objects and goto Sollumz Tools -> Collisions -> Create Bounds -> Convert to ... -> Child ... "Bound GeometryBVH"  

>    4c. If you STILL see 0, make sure you are using .ybn files, the correct version of Sollumz, Blender, and CodeX. At this point, restart the tutorial :)  
  5. When you see your navmesh object in the scene, highlight it and goto File -> Export -> CodeX XML
  6. Done with Blender! 


## 4. Importing XML & Exporting RAW using CodeX
*  Open CodeX.Explorer
  1. Goto File -> Open Folder... location of your .XML from Blender  
  2. Right Click "navmesh[288][261].ynv.xml" (or whatever your file is)  
  3. Import XML... -> Open  
  4. You now have a streamable navmesh (.ynv) file in that directory!  

## 5. Streaming .ynv file
*  Navigate to the resource we created in Step 1.  
  1. Drag and Drop the "navmesh[###][###].ynv" into the "stream" folder.  
  2. Start the server  
  3. Spawn any ped on your new navmesh to test it out!  


## Credits
*   Everyone who works on Sollumz, CodeX/Codewalker.
*   Foxxyy for the forked Sollumz
