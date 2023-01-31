# Overview
## NOTE: DO THIS, THEN STRIP IT OF DESCRIPTIONS AND ADD IT TO THE INCLUDED MATERIALS PAGE 

## Preface
In this first part of the build, you will create a circuit to provide power to the Raspberry Pi from the battery. You will make the circuit connections using the soldering skills that you've gained from the Soldering Module.
First, we will reintroduce you to the components that you will be working with. Then, you will do some preliminary tasks that will run in the background. As those tasks are running, you will go through the first portion of the build.

### Required Materials
**Part : Quantity** (MAKE IT A TABLE?)
* Battery : 1
* Battery Charger : 1
* Battery Charging Adapter : 1
* Power Distribution Board : 1
* Universal Battery Eliminator Circuit : 1
* Pi Hat : 1
* XT60 Connector : 1
* Soldering Tools : 1
* Raspberry Pi: 1
* Heat Sinks: 1 set
* Micro SD Card : 1
* Base Station : 1
* Micro SD Card Reader : 1

## Detailed Hardware Descriptions
### Battery
```{figure} ../_images/rpi-power/battery.png
LiPo Battery
```

The Battery on your drone is a 1500mAh 3S 20C LiPo Battery. Let's go over what all that means.

### Capacity
The unit milliAmp hour, or mAh, is a measure of how much charge a battery can hold. The higher this number is, the more charge the battery can hold; therefore, the battery will "last" longer and your drone will fly for a longer time without needing to be recharged.

### Structure
A Lithium-ion polymer (LiPo) battery is made up of one or more LiPo cells. Each cell has a voltage of 3.7 V when it is discharged, and 4.2 V when it is charged. The cells in your battery are connected in series, so that the voltages add together to get a total of 11.1 V when discharged, and 12.6 V when charged. There are three cells connected in series in your battery, so it is a 3S battery.

### Current Output
The "C" rating of a LiPo Battery determines how much current the battery can deliver. The maximum current draw is equal to the battery's C rating multiplied by the battery's capacity. For the drone's 1500mAh 20C batteries, the maximum current draw is 1500mAh x 20C = 30A.

### Precautions
Review the safety information on the battery [ADD LINK TO THE CHAPTER]. Taking the proper precautions when using, storing, or charging is very important to keeping the battery safe. Only store the battery at room temperature and out of direct sunlight. Do not discharge a battery below 10.5 V. 

```{danger}
Never leave the battery charging unattended. Unplug the battery once it is fully charged.
```

### Power Distribution Board (PDB)
```{figure}../_images/rpi-power/PDB.png
Power Distribution Board (PDB)
```

The Power Distribution Board is used to distribute power from the battery to electrical components of the drone. The PDB is an example of a Printed Circuit Board (PCB), which is a circuit board that has connections within its structure. For the PDB, the internal wiring connects all of the positive (+) pads together, and all of the negative (-) pads together; this allows for the battery to be connected to one set of positive and negative pads, and all of the other pads receive power.

### UBEC (Universal Battery Eliminator Circuit)
```{figure}../_images/rpi-power/UBEC.png
UBEC
```

The UBEC, solves the issue that arises from different electrical components requiring different supply voltages. In the case of the drone, the LiPo battery is used for outputs around 12V; this is the required voltage for the motors, but not for the Raspberry Pi, which requires 5V. The Universal Battery Eliminator Circuit eliminates the need to carry multiple batteries of different voltages by converting the 12V supply from the battery down to a 5V supply for the Pi.

### Raspberry Pi
```{figure}../_images/rpi-power/raspberry.png
Raspberry Pi 3 Model B
```

The Raspberry Pi, or, Pi, is a single-board computer. The Pi is capable of running a full desktop operating system; you can use it as a computer similar to the one you're using now. The Pi is used on the drone as the main computer that reads and processes all of the sensor data and user inputs, and then sends commands to the flight controller to control the drone motors. The drone would be able to fly without the Pi if a person had a remote controller to manually steer the drone. However, for the DuckieSky Drone, the person with a remote controller is replaced by software and sensors on the Pi. The Pi, as well as the sensors you will connect later, makes autonomous flight possible.

### Pi Hat
The Pi hat is a special type of breadboard. One useful property of a breadboard is that it has rails. A rail is a sequence of holes that share an electrical connection:

```{figure}../_images/rpi-power/pihat_1.png
Pi Hat shield
```
```{figure}../_images/rpi-power/pihat_2.jpg
PiHat with rails highlighted in purple
```

The rails are useful because every wire put on a rail will be electrically connected; this means that it does not matter which hole along a rail a wire is inserted. This is useful for wire organization, and if a soldering mistake is made in one hole, an adjacent hole in the same rail can be used instead. Notice especially the long +5V and GND rails; we can use any of the holes in these rails to provide power to components. Also notice that there is a 3.3V rail, be sure not to mix this up with the 5V rail because electrical components will only work at the correct voltages

### Micro SD Card
```{figure}../_images/rpi-power/microSD.png
microSD card
```
```{figure}../_images/rpi-power/microSD_reader.png
Micro SD Card adapter
```

The Micro SD card stores the operating system on the pi, as well as all the software needed for autonomous flight.
    

### XT60 Connector
```{figure}../_images/rpi-power/XT60_cable.png
XT60 connector cable
```

An XT60 connector cable is a component which provides power when a power source (e.g. battery) is connected to it. By soldering it to the PDB, the PDB will get power to distribute to other components.

## Preliminary Tasks
### Charge the Battery
Start charging your drone battery so it is ready when you need it.

```{note} Never leave the battery charging unattended. The battery takes about 2 hours to charge.  When charging, the battery flashes between the voltage on each cell and "ALL", the voltage on all cells together.  The battery is fully charged when "ALL" is 12.5 volts.  You can also tell by measuring the voltage across the battery's power and ground with a multimeter.  When the battery is plugged into a charger and the charger is not plugged into a wall, it uses power from the battery to display the voltage on the battery.  Over time this will drain the battery.  If a battery's voltage gets too low, the battery can then no longer be charged.  Never leave a charging battery unattended, and always unplug the battery as soon as it is charged.
```

### Download Image and Image Flashing Software
1. If you have not already, on a base station, download the image flashing tool [Etcher](https://www.balena.io/etcher/).


2. If you have not already, on a base station, download the latest drone image.
**Download the [Duckiedrone DD21 system image](https://duckietown-public-storage.s3.amazonaws.com/brown/disk_image/dt-amelia-DD21-brown2022-sd-card-v11.zip) (~2.5 GB)**


3. Connect the micro SD card to the base station. Use the micro SD to USB card reader if the  base station does not have a micro SD port.


4. Open Etcher and select the downloaded drone image. Then select the micro SD card as the drive to flash. Finally, click the "Flash" button.

```{note} Double check that the "drive" is your micro SD card. You may be prompted to enter the base station password to proceed. This is normal; flashing an SD card deletes everything that is on it, so Etcher is making sure this process is OK with you.
```
```{note} Flashing will take 10 - 15 min. In the meantime, you can move on to the next section.
```