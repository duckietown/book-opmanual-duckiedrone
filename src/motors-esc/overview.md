(overview_motors_esc)=
# Overview
## Preface

In this phase of the build, you’ll be adding the essential elements of every drone– the motors, ESCs, and the flight controller.

## Required Materials
```{list-table} Materials
:header-rows: 1
:name: materials-motors-esc

* - Part
  - Quantity
* - Counter-clockwise Motors
  - 2
* - Clockwise Motors 
  - 2
* - Long gray metal M3 Bolts 
  - 16
* - Nylon M3 Bolts and nuts
  - 4 pairs
* - Electronic Speed Controllers (ESCs)
  - 4
* - Propeller guards
  - 4
* - Plastic standoffs
  - 4
* - Battery leads Wire
  - 1
* - Soldering Tools
  - 1
* - Zip ties
  - ~ 8
```



## Detailed Hardware Descriptions

### Motors
The motors used are Brushless Direct Current (BLDC) motors. They are a particular type of electric motor commonly used in drones for their high reliability and low wear during usage.

```{figure} ../_images/motors-esc/motors.jpg
:width: 400px
:align: center

BLDC motors

**black nut** : *counter*-clockwise motors

**red nut** : clockwise motor
```

### Electronic Speed Controller (ESC)
An Electronic Speed Controller (ESC) is used to regulate the speed of a motor according to a signal from the flight controller. A brushless motor would not be able to spin without an ESC, as they are responsible for changing the magnetic fields that generate a moment to make the motor spin.

```{figure} ../_images/components-official/ESC.png
:width: 400px
:align: center

Electronic Speed Controller
```

### Battery Monitoring Leads

The battery monitor wires allow the flight controller to monitor the power traversing the PDB. This is useful because the flight controller can inform the Pi of the battery voltage. The benefit of this is that the software will prevent the battery from draining too low and permanently damaging it.

You will be using the extra red and black wire that came with the kit to make the battery monitor leads.

```{figure} ../_images/motors-esc/wire.png
:width: 400px
:align: center

Battery monitoring leads
```

### Long M3 screws

These long gray screws are used to attach the motors to the frame together with the propellers guards (prop guards) and the plastic standoffs used as landing legs.

```{image} ../_images/components-official/long_M3_screws.png
```

```{danger} 
The motors include short black M3 screws. You must not use these as they are too short to attach to the motors when the landing standoffs and prop guards are attached. 

**You MUST use the long gray M3 screws.**

```{figure} ../_images/motors-esc/motors_screws.png

**left:** right screws to use

**right:** wrong screws, DO NOT USE
```

### Nylon M3 bolts and nuts
These plastic bolts are used to attach the PDB to the frame of the Duckiedrone.

```{warning}
You will fing both M3 and M2 bolts and nuts in your Duckiebox, pay attention to use the M3 in this section.

You can distinguish them by:
1. comparing the two; the M3 bolts will be slightly thicker
1. the M2 bolts only have 4 corresponding nuts
1. the M3 bolts have 11 corresponding nuts

The M3 bolts will fit firmly in the PDB mounting holes, whereas the M2 bolts would wobble and be loose.
```
```{figure} ../_images/components-official/nylon_M3_bolts_nuts.png

Nylon M3 bolts (8) and nuts (11)
```

### Zip Ties

Zip Ties will help you tie up your Duckiedrone together and manage its cabling (Duckiecaptain wants its ship to be tidy!).

```{figure} ../_images/components-official/zip_ties.png

Zip Ties (Large on top, small on bottom)
```

### Propeller Guards

The propeller guards protect both the propellers and the environment where the drone flies.

```{figure} ../_images/components-official/prop_guard.jpg
:width: 400px
Propeller guard
```

### Standoffs feet

These white plastic standoffs are mounted beneath the motors' attachment point on the frame and provide stable ground contact points for the drone.

```{figure} ../_images/components-official/feet_standoffs.png
:width: 400px

Drone feet standoffs
```