# Fanuc-TeachPendant Basics

Still WIP

## About
Robots by Fanuc are controlled via the

## Programming
### Hold dead-man-switch
To activate the dead man switch:

- **First**, hold down <kbd>SHIFT</kbd>
- **While holding <kbd>SHIFT</kbd> pressed**, press and hold the **button at the rear of the TeachPendant** half-way through and hold it.

### Create a program

#### 1. Create new step-by-step procedure
- Press <kbd>select</kbd> to open the menu 
- Then press <kbd>F2</kbd> to create a new program

#### 2. Add step
- Press <kbd>F1</kbd> ("POINT")
- Select the kind of motion and speed you want from the dropdown
- Then press <kbd>enter</kbd>

#### 3. Edit step
- You can choose between linear motion or radial motion


#### 4. Run program
Hold dead man switch, the press the <kbd>FWD</kbd> button (= forward) to run the program.

#### Deleting/Copying/etc. steps
- Press <kbd>F5</kbd> for **"|EDCMD|"** (You may have to press <kbd>NEXT</kbd> in the menu bar to navigate there)
- Select action you want from the dropdown menu
- Press enter
- Confirm action

#### Looping a program
Label
Jump label

Can be created in the Menu ???

Example:
![Example of a looping movement](TeachPendant_Program_Loop.jpg)

## Run program in automatic mode
Switch into automatic mode by:

- Rotate the key on the base station to "AUTO"
![Turn mate to auto](Mate_auto.jpg)
- Turn the TeachPendant off (Switch in top left corner)
![Turn TeachPendant to off](TeachPendant_off.jpg)

Switch it on
Press "CYCLE START"-button (Green button next to the emergency stop on the base station)

**If it doesn't start:**

- Clear Errors by pressing <kbd>Reset</kbd> on the TeachPendant and start the cycle again
- The TeachPendant might inform you, that the robot is at a different position, select "Yes" if this happens (the robot will move to position 1 of your script and then start)

## Helpful Videos
- [TeachPendant Programming Demo – Draw rectangle with rounded corners](https://www.youtube.com/watch?v=303LHXET0W4)