# Fanuc-TeachPendant Basics

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [About](#about)
- [Limitations](#limitations)
- [Controlling the Robot](#controlling-the-robot)
  - [Unlocking the robot](#unlocking-the-robot)
  - [Set speed](#set-speed)
  - [Moving the robot](#moving-the-robot)
- [Programming](#programming)
  - [Create a program](#create-a-program)
    - [1. Create new step-by-step procedure](#1-create-new-step-by-step-procedure)
    - [2. Name program](#2-name-program)
    - [3. Add steps](#3-add-steps)
    - [4. Run program](#4-run-program)
  - [Editing steps](#editing-steps)
  - [Deleting/Copying/etc. steps](#deletingcopyingetc-steps)
  - [Looping a program](#looping-a-program)
  - [Run program in automatic mode](#run-program-in-automatic-mode)
- [Helpful Videos](#helpful-videos)
- [Notes](#notes)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## About
Industrial Robots are difficult to control, they are made for specially trained personal and hardly accessible to anybody else. 

For our semester project at the [HfG Schwäbisch Gmünd](http://www.hfg-gmuend.de/) we used a [Fanuc 200ic/5h](https://www.robots.com/fanuc/lr-mate-200ic-5h). This tutorial will show teach you the basics of the TeachPendant – a remote control by Fanuc to program their robots.

## Limitations
Originally we planned to control the robot externally via tools such as [Processing](https://processing.org/) or [Arduino](https://www.arduino.cc/). We were however not able to do that. If you have a solution to externally control the robot, feel free to fork this repo and add it to it.

Your help would be hugely appreciated.

## Controlling the Robot
### Unlocking the robot
In order to control the robot you have to diactivate his safety mechanism – the [dead man's switch](https://en.wikipedia.org/wiki/Dead_man%27s_switch):

1. Press and hold <kbd>SHIFT</kbd>
2. Press (half-way through) and hold one <kbd>vertical yellow button</kbd> on the rear of the TeachPendant 
3. Keep holding these buttons (otherwise robot will go back into a locked mode)

### Set speed
After power up, the robot's speed will be slow by default. Current speed is shown as percentage with a green background in the top right corner. You can control the maximum speed on the TeachPendant:

- <kbd>+%</kbd> Raises speed
- <kbd>-%</kbd> Lowers speed

**Note:** The robot's speed in manual mode is only a fraction of what it will in automatic mode. **Be careful!**


### Moving the robot
There are multiple ways to control the robot. However, we only used the movement types "JOINT" and "WORLD". They can be cycled through by pressing <kbd>COORD</kbd> on the TeachPendant. The current mode will be shown in the top right with a black background. These settings affect the functions of the blue buttons (on the right of the TeachPendant) which control the robots movement:

#### Joint
The movement type "JOINT" controls every joint individually. 

**J1** = base joint:

- <kbd>+X(J1)</kbd> Rotate anti-clockwise
- <kbd>-X(J1)</kbd> Rotate clockwise

**J2** = lower arm joint:

- <kbd>+Y(J2)</kbd> Rotates upwards
- <kbd>-Y(J2)</kbd> Rotates downwards


**J3** = upper arm joint:

- <kbd>+Z(J3)</kbd> Rotates upwards
- <kbd>-Z(J3)</kbd> Rotates downwards

**J4** = "hand" joint:

- <kbd>+X(J4)</kbd> Rotates upwards
- <kbd>-X(J4)</kbd> Rotates downwards

**J5** = tool mount joint:

- <kbd>+Y(J5)</kbd> Rotates clockwise
- <kbd>-Y(J5)</kbd> Rotates anit-clockwise

**J6** is not assigned in our robot (because it is only euqipped with five axis). Normally it would control the arm's rotation itself.


#### World
The movement type "WORLD" defines one point, where the robot points to. This point is the tip of the tool mount. This means, that you just set where the tool mount's tip should be located and the robot will move all necessary joints to reach that position.

**J1** = x-axis:

- <kbd>+X(J1)</kbd> Move forward
- <kbd>-X(J1)</kbd> Move backward

**J2** = y-axis:

- <kbd>+Y(J2)</kbd> Move left
- <kbd>-Y(J2)</kbd> Move right


**J3** = z-axis:

- <kbd>+Z(J3)</kbd> Move up
- <kbd>-Z(J3)</kbd> Move down

**J4** = "hand" joint:

- <kbd>+X(J4)</kbd> Rotates "hand" upwards
- <kbd>-X(J4)</kbd> Rotates "hand" downwards

**J5** = tool mount joint:

- <kbd>+Y(J5)</kbd> Rotates clockwise
- <kbd>-Y(J5)</kbd> Rotates anit-clockwise

**J6** is not assigned in our robot (because it is only euqipped with five axis). Normally it would control the arm's rotation itself.



## Programming
### Create a program

#### 1. Create new step-by-step procedure
1. Press <kbd>select</kbd> to open the menu 
2. Press <kbd>F2</kbd> ("CREATE") to create a new program

#### 2. Name program
1. Using the arrow keys you can either choose presets ("Words") or type your own name ("Upper Case" and "Lower Case"). "Options" also reveals more advanced functions.
2. Press <kbd>ENTER</kbd> on the TeachPendant to close naming menu
3. Press <kbd>ENTER</kbd> again to confirm name

#### 3. Add steps
1. Press <kbd>F1</kbd> ("POINT")
2. Select the kind of motion and speed you want from the dropdown. 
	- "J" stands for joint movement
	- "L" stands for linear movement
	- "FINE" stands for a precise movement
	- "CNT100" stands for an approximate movement
3. Press <kbd>enter</kbd> to select
4. The current postion of the robot has now been saved to that point and just appeared as a new line in your code

**Note:** "CNT100" is normally used as an intermediate point. It is faster than "FINE", because will approach that coordinate just roughly. 

Example: If you want to move from Point A to B via Point C (e.g. to avoid collision with something), Point C should be set to "CNT100".

#### 4. Run program
Hold dead man switch, the press the <kbd>FWD</kbd> (forwards) button to run the program. Pressing <kbd>BWD</kbd> (backwards) will do the opposite.

Pressing the <kbd>STEP</kbd> button on the TeachPendant will cycle between two differend modes. It is shown in the top left corner labeled "step". 

- **Green background** indicates that the robot will cycle through all steps (once)
- **Logo with two arrows and red bars** indicates that the robot will move only step at a time (after each completion you have to hit <kbd>FWD</kbd> again)

### Editing steps
Using the arrow keys you navigate from top to bottom and also from left to right

**Set new coordinate for point:**
Select the line number of the point you want to change. Pressing <kbd>F5</kbd> ("TOUCHUP") will overwrite the previous coordinates with the current one

**Change movement type:**
Select the letter after the line number (C, J or L) and press <kbd>F4</kbd> ("CHOICE") to switch to a different motion type.

**Change movement precision:**
Select "CNT100"/"FINE" press <kbd>F4</kbd> ("CHOICE") to select a different precision.

**Set speed to point:**
Select the type of speed (either %, sec or msec) and press <kbd>F4</kbd> ("CHOICE") to change it. You can also change the value by typing numbers on the TeachPendant (confirm by pressing <kbd>ENTER</kbd>).

### Deleting/Copying/etc. steps
- Press <kbd>F5</kbd> for **"|EDCMD|"** (You may have to press <kbd>NEXT</kbd> in the menu bar to navigate there)
- Select action you want from the dropdown menu
- Press <kbd>ENTER</kbd>
- Confirm action

### Looping a program
As you might have noticed, the robot will only run the program once. You have to loop a program for that reason. This happens by creating a "label" and using a command to jump to that label.

1. In the programm editing mode, press <kbd>NEXT</kbd> on the TeachPendant to reveal the menu points "[INST]" and "[EDCMD]"
2. Press <kbd>F1</kbd> ("[INST]")
3. Select "5 JMP/LBL" and press <kbd>ENTER</kbd>
4. Select "2 LBL[  ]" and press <kbd>ENTER</kbd>
5. Enter a number on the TeachPendant and press <kbd>ENTER</kbd>
6. The line you have create will say something like "1: LBL[12]" and means that there is the label with the index 12 where you can "jump" to, but more on that soon
7. Now enter the "[INST]" menu again, but this time select "2 JMP LBL[  ]" and press <kbd>ENTER</kbd>
8. Give it the same number as the label before.
9. You should have something like:

```
1:  LBL[12]
2:J @P[1] 100% FINE
3:J  P[2] 100% FINE
4:  JMP LBL[12]
```
This means that the robot will read line 1 (won't do anything though), move to the coordinates specified in line 2, afterwards move to the coordinates from line 3 then he reads in line 4 that he has to continue from the label with the number 12 (which is in line 1), so he will jump back to line 1 and therefore do the same procedure again.

You can now loop this action in the automatic mode.


### Run program in automatic mode
Switch into automatic mode by:

- Rotate the key on the base station to "AUTO"
- Turn the TeachPendant off (Switch in top left corner)

Switch it on
Press "CYCLE START"-button (Green button next to the emergency stop on the base station)

**If it doesn't start:**

- Clear Errors by pressing <kbd>Reset</kbd> on the TeachPendant and start the cycle again
- The TeachPendant might inform you, that the robot is at a different position, select "Yes" if this happens (the robot will move to position 1 of your script and then start)

## Helpful Videos
- [TeachPendant Programming Demo – Draw rectangle with rounded corners](https://www.youtube.com/watch?v=303LHXET0W4)

## Notes
- Table of contents was created using [DocToc](https://github.com/thlorenz/doctoc)
