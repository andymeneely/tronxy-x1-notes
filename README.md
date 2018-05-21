Here are my notes for how I use the Tronxy X1

If you have any questions or suggestions, file a GitHub issue!!

# Bed Adhesion

I use a glass bed instead of the plastic cover they provide

* Got an old picture frame from a thrift store
* Got a glass cutter
* Cut to size

I cover the bed in painter's tape.

* 3M 2-inch wide tape seems to work better than Blue Hawk

I typically put a glue stick down

* Elmer's Washable School glue
* Even if it dries out it will work fine.

# IdeaMaker

I use ideaMaker as my slicer, since it allows me to set my own supports.

TODO: put some settings here

## Infill

It all depends on my part

## Retraction

* I use 4mm of retraction distance
* To reduce retraction in general, I check ""

# OctoPrint

Originally I used Repetier server until the trial expired. I was happy with it, just not the price.

With OctoPrint, I:

* Had to add a plugin to set my EEPROM. It's the Repetier flavor. MAKE SURE you hit "Save to EEPROM", not just the save button at the bottom. Otherwise it won't actually save to the machine.


# Webcam

I use YawCam with a cheap webcam I got off of Amazon. I wish I got a better webcam, though.

# Noisey Z-Axis

My z-axis stepper likes to make a lot of noise. Putting some 3-in-1 oil

# Calibration notes

I'm constantly adjusting my X, Y, and Z home pos. Especially Z. It all depends on adjustments I make to the machine, what kind of bed I use, how much tape I put down, etc. My Z home position is generally -14 to -16mm. But I also set my limit switch pretty low.

To find my Z home position, I will go to manual control. First, home the machine. Then, move the head above the center of the plate, with plenty of Z space. Move the head down to the plate, keeping track of how far you've moved. Go until a piece of paper has trouble fitting between the bed and the extruder. For example, my sequence of operations is:

1. Home X and Y
2. Home Z
3. Move Z up 30mm
4. Write down "30mm" on a piece of paper
5. Move X and Y to middle of the plate (~80-100mm each)
6. Move Z down by 10mm, writing down 20mm
7. Repeat above step, but with smaller increments so as not to hit the bed.
8. When the extruder barely passes a piece of paper between, you're about done
9. Say the number is 16.3mm, put (NEGATIVE!) -16.3mm in your EEPROM Z Home Pos

Definitely a good idea to adjust your EEPROM X/Y/Z-axis steps per mm. I used this [calibration cube on Thingiverse](https://www.thingiverse.com/thing:1278865). Just pay attention to what the X and Y are - I got them reversed initially.

Also a good idea to calibrate your extruder steps per mm. Repetier firmware won't let you do cold extrusion, so you'll need to heat up the extruder, then disconnect the bowden tube up by the extruder. Then push 100mm of filament. Measure. Do this a few times and get an average. Then adjust your steps per mm as:

`New Steps/mm = (Current steps/mm) x [100 / (measured distance filament traveled)]`

Default baud rate of 115200 works for me. If use anything higher, my machine constantly reboots.

Everything else is still default for me.
