(overview_motors_esc)=
# Overview
## Preface

In this phase of the build, you’ll be adding the essential elements of every drone– the motors, ESCs, and the flight controller.
Required Materials

## Required Materials
```{list-table} Materials
:header-rows: 1
:name: materials-motors-esc

* - Part
  - Quantity
* - Flight Controller
  - 1
* - Counter-clockwise Motors
  - 2
* - Clockwise Motors 
  - 2
* - Long gray M3 Bolts (included w/ motor) 
  - 16
* - Short M3 Bolts (included w/ motor) 
  - 4
* - Electronic Speed Controllers (ESCs)
  - 4
* - Velcro Strap 
  - 1
* - Propeller guards
  - 4
* - Plastic standoffs
  - 4
* - Battery leads Wire
  - 1
* - Soldering Tools
  - 1
```



## Detailed Hardware Descriptions

### Motors
The motors used are Brushless Direct Current (BLDC) motors. They are a particular type of electric motor commonly used in drones for their high reliability and low wear during usage.

```{figure} ../_images/motors-esc/motors.jpg
:width: 400px
:align: center

BLDC motors
```

### Electronic Speed Controller (ESC)
An Electronic Speed Controller (ESC) is used to regulate the speed of a motor according to a signal from the flight controller. A brushless motor would not be able to spin without an ESC, as they are responsible for changing the magnetic fields that generate a moment to make the motor spin.

```{figure} ../_images/motors-esc/ESC.png
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

```{image} ../_images/motors-esc/long_M3_screws.png
```

```{danger} 
The motors include short black M3 screws. You must not use these as they are too short to attach to the motors when the landing standoffs and prop guards are attached. 

**You MUST use the long gray M3 screws.**

```{figure} ../_images/motors-esc/motors_screws.png

**left:** right screws to use

**right:** wrong screws, DO NOT USE
```


% REMOVED: build progress