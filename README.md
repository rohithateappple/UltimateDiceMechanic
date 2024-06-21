# UltimateDiceMechanic
Guide Page for Ultimate Dice Mechanic

![Screenshot 2024-06-21 104641](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/0e7ba709-0730-4d75-a166-e2a5c89a53ed)

## Getting Started
IMPORTANT: Since this is an asset pack, the project doesn't come with a config file. So make sure to add a new trace channel called "Dice" in your project settings and set the default to ignore.
Now open the BP_ProceduralDie, select all "Face" static mesh components, and set their trace channel's Dice to "BLOCK". Do the same for BP_RegularDie, this time all the Face Colliders.

 - Drag the BP_DiceManager into your level.
 - Tweak settings if needed.
 - Hit Play.
 - Press the Space Bar to roll dice.
 - Press H to toggle 'Spawn at Cursor'.

## Changing Values
This section focuses mainly on working with the available data tables. How to each die's values and materials.

## Procedural Die Guide

### Custom Frames and Faces
When modeling the face, be sure to face it in the direction of the up vector in Unreal Engine. Only one face model is required since it will be duplicated inside UE.
The frame can be modeled in any way, just make sure it's a single whole piece that can accommodate all six faces.
