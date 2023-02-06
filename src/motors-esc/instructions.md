# Instructions

```{note} Sometimes parts will have wires already tinned out-of-the-box by the manufacturer (i.e. pre-tinned). You can identify this by: 1) the “shininess” of the tip of a wire and 2) the inability to fray the wire strands of the tip of a wire. However, such tinning is often ineffective. Cut off any pre-tinned tips, then strip and tin the part yourself.
```
Visually inspect each ESC and verify that the heat shrinks are on properly; there should be no exposed wires and each heat shrink should be a tight fit. 
Do a connectivity check on the XT60 connector cable; verify there is no short between the red and black wire.

## Soldering ESCs to the PDB

An ESC (i.e. Electronic Speed Control) is a component which requires power. It takes this power and provides a variable amount of it to a motor; since a motor’s RPM depends on how much power it gets, an ESC can control how fast a motor spins by controlling how much power it supplies the motor.

```{figure} ../_images/motors-esc/motors_esc_schematic.jpg
:width: 400px
:align: center

Schematic of motors-ESCs connections
```

```{attention}
Do not solder the wires flat against the PDB - solder them at ~20° angle. If you solder them flat, then you will not be able to fit the PDB into the drone frame.
```

Solder each of your 4 ESCs to the PDB:
1. Strip about 5mm of wire from (+) and (-) of ESC
1. Tin the wire
1. Solder on the pad at a 20 deg angle.


```{figure} ../_images/motors-esc/soldered_motors.jpg
[TODO: Pic of ESCs Soldered to PDB ]
```

## Solder battery monitor leads to the PDB

Solder the 6-inch red and black wires to the PDB to the `VCC` and `GND` pads respectively. 

```{figure} ../_images/motors-esc/battery_monitor_pads.jpg
```

[TODO: ADD PICTURE OF SOLDERED LEADS]

These wires are soldered as to go across the PDB, toward where the flight controller will be mounted.

```{attention}
While trying to solder on these wires, you may accidentally unsolder the existing wires from the PDB. We recommend temporarily holding down the existing wires with long-nose pliers, tape, or helping hands.
```

## Attach parts to drone frame
This section will cover attaching the first set of items to the drone frame.
Before beginning, verify the PDB is completely soldered with all necessary parts (as covered in previous sections).

```{note}
The flight controller is not shown in these images.

However, don’t be alarmed that your build is incorrect.

For now, just move the flight controller as you are working so it is not in the way. In the next section, you will attach the flight controller to the drone frame.
```

For reference, here are the motor directions with respect to the frame:

```{figure} ../_images/motors-esc/spin_direction_reference.jpg
:width: 400px
:align: center

Your motors MUST spin in these directions
```

```{admonition} What you'll need

Gather the following:
* Drone frame
* Completed PDB
* 4 motors (2 Clockwise, 2 Counterclockwise)
* Velcro strap
* Crash guards
* 4 standoffs
* 12 black screws (in motors box, not drone frame box)
```
### Align the frame
Place the drone frame on a flat surface so that the back is facing you.
 
### Attach PDB to frame

Place the completed PDB into the front center of the drone frame. With plastic screws in their respective holes. For each of the 4 corner screw holes of the PDB, add a plastic nut on the other end to secure it. 

```{figure} ../_images/motors-esc/pdb_on_frame.jpg

PDB Secured in Drone Frame
```

### Attach motors

There are two clockwise and two counter-clockwise motors.  Unfortunately the motors themselves are not labeled, so only the color of the screw will let you tell the difference.  The clockwise motors have a nut threaded so that when the propellers spin clockwise, the nut will tend to tighten, and the counter-clockwise motors are the opposite.  

* The counter-clockwise motors have a black nut. * The clockwise motors have a red nut.

Take the motors out of their bags.  

```{attention} Immediately screw on the red or black nut into the main screw sticking out of the motor.

This will prevent you from mixing up the motors.
```

```{admonition} TODO
this section is not very clear, take some pictures and improve it
```

```{admonition} TODO: CLARIFY and COMPLETE
Find the prop guards, and put a prop guard underneath each motor between [TODO: CLARIFY]

Attach **CW** motors to the bottom-right and top-left of the drone frame, using 2 silver screws for each attachment.  (Do not use the black screws that come with the motor.) [TODO: CLARIFY]
The image below is just for reference but belongs to a previous build.

Top View Add completed picture here with feet and prop guards + motors
```

Attaching CW Motors
Attach Counter-Clockwise (CCW) Motors

Attach CCW motors to the bottom-left and top-right of the drone frame, using 2 black screws for each attachment.



[Attaching CCW Motors]
### Connecting the Motors to the ESCs

For each motor, connect its plug bullet connectors to the socket bullet connectors of the ESC in the motor’s corner (e.g. top-left motor connects to top-left ESC). Any connection order will suffice for now, as you will be able to change them in a later phase.

```{figure} ../_images/motors-esc/connected_esc.jpg

ESCs plugs connected to motors
```
