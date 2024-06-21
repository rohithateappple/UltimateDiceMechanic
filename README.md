# UltimateDiceMechanic
Guide Page for Ultimate Dice Mechanic

![Screenshot 2024-06-21 104641](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/0e7ba709-0730-4d75-a166-e2a5c89a53ed)

## Getting Started
IMPORTANT: Since this is an asset pack, the project doesn't come with a config file. So make sure to add a new trace channel called "Dice" in your project settings and set the default to ignore.
Now open the BP_ProceduralDie, select all "Face" static mesh components, and set their trace channel's Dice to "BLOCK". Do the same for BP_RegularDie, this time all the Face Colliders.

![Trace-Channels](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/c688f811-c3c9-4145-aa5e-9780957968f2)

 - Drag the BP_DiceManager into your level.
 - Tweak settings if needed.
 - Hit Play.
 - Press the Space Bar to roll dice.
 - Press H to toggle 'Spawn at Cursor'.

## Changing Values
This section focuses mainly on working with the available data tables. How to change each die's values and materials. First, navigate to:

Dice/Data/ProceduralDie/ValueGeneration/... --> Open any procedural data table.

or

Dice/Data/RegularDie/...--> Open any regular data table.

NOTE: Procedural data tables only work with procedural dice. The same goes for regular tables.

In the procedural table, you can see two options to change: materials and values. We're essentially mapping each material to a value that a face might use.
So if you have custom materials, assign them here and give them appropriate values. The order doesn't matter here.

![Prokcedural-Data-table](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/7191ef9d-a43f-4f1b-8c4e-615762bd449d)

Next for the regular data table. It's pretty much the same but with no materials and the order matters here. If you open the BP_RegularDie, you'll
see the Face Colliders. These are names matched to those in the data table. So see which collider represent with value of your custom die mesh and
then assign that value to the appropriate collider in the data table.



## Procedural Die Guide

### Custom Frames and Faces
When modeling the face, be sure to face it in the direction of the up vector in Unreal Engine. Only one face model is required since it will be duplicated inside UE.
The frame can be modeled in any way, just make sure it's a single whole piece that can accommodate all six faces.
