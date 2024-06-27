# UltimateDiceMechanic
Guide Page for Ultimate Dice Mechanic

![Screenshot 2024-06-21 104641](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/0e7ba709-0730-4d75-a166-e2a5c89a53ed)

## Getting Started
IMPORTANT: Since this is an asset pack, the project doesn't come with a config file. So make sure to add a new trace channel called "Dice" in your project settings and set the default to ignore.
Now open the BP_ProceduralDie, select all "Face" static mesh components, and set their trace channel's Dice to "BLOCK". Do the same for BP_RegularDie, this time all the Face Colliders.

![Trace-Channels](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/c688f811-c3c9-4145-aa5e-9780957968f2)

Also, ensure the line trace in the __GetDieValue()__ in both the BP_RegularDie and BP_ProceduralDie is set to the Dice channel. This should be on by default on new projects, with no existing trace channels. But, for existing projects, be sure to double-check.

![Screenshot 2024-06-27 181912](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/a063d8f3-b377-485f-8341-f7cc32d14aae)

## Simply Drag and Drop

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
see the Face Colliders. These are name matched to those in the data table. So see which collider represents what value of your custom mesh and
then assign that value to the appropriate collider in the data table.

![Regular-Data-table](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/2052ba0b-4dec-4fdd-96da-f0c4d912cc17)

Once the modifications are done, you can assign the data table in the *Data* section of the BP_DiceManager, or any die blueprint manually.

![Screenshot 2024-06-22 125444](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/7113453e-f452-45b4-a045-92829836e2c6)

## Procedural Body

### Custom Frames and Faces
When modeling the face, be sure to face it in the up direction of Unreal Engine. Only one face is required since it will be duplicated inside UE.
The frame can be modeled in any way, just make sure it's a single whole piece that can accommodate all six faces. Also, make sure to keep the origins of these
meshes centered at the cube. This can be done in UE, but it's better to do it in one go.

![origin](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/8719ee66-90f4-4e7a-9edd-a3479b1404cb)

## Tweaking Roll Physics

Adjusting roll physics is pretty self-explanatory, open your BP_DiceManager and play around with various settings. There's no "right" setting since it depends heavily on your project. But here's an explanation of each setting.

![Physics-Settings](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/ddf77b2b-f1c4-4736-a729-0ec52a0e2337)

## Stationary Checks

Stationary check refers to the method used to see if a die is stationary. We need this information to efficiently read values. I have strayed away from using a tick method for this because it can be quite expensive, instead, I've used a Timer by Event. There are currently two methods to choose from: DeltaTransform and RigidBodyAwake. 

        - Delta Transform: Compares the previous transform to the current. (Faster but can be inaccurate).
        - RigidBodyAwake: Checks if a rigid body is asleep. (Slower but accurate).

I've also implemented a "Side Check" to see if the die has landed on any of its sides. This is to prevent reading values in non-optimal landing positions. For this, a floor actor is __required__.

![Side-Check](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/ec7e04d0-f4aa-40d8-9785-757f4494dee4)

## Shoot Dice

This one could be named better. What I mean is "throw" the dice from a point. As opposed to the default "rolling" on the ground. Shooting can be done either from an actor of your choice or from the player's location, like a gun. When Shoot from Player is not active, the default is reverted to an object. So, a shooter object is __required__.

![Shoot-from-palyer](https://github.com/rohithateappple/UltimateDiceMechanic/assets/131531154/74962796-6d1b-4762-8302-39880fde3722)

## Enjoy!

Hope you find my program helpful and have fun rolling some dice!
        
