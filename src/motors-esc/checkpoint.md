# Checkpoint

## Verify the wiring is correct

### Visually inspect the drone

Verify the following:
* All red wires connected to the PDB are connected to positive (`+`) pads
* All black wires connected to the PDB are connected to negative (`-`) pads
* The wires on the `INPUT` side - **NOT** the `OUTPUT` side - of the BEC are soldered to the PDB
* For the battery monitor lead: the red wire is connected to a positive (`+`) pad while the brown wire is connected to a negative (`-`) pad

```{attention}
Do a **connectivity check** on the PDB.

Verify there is:

* a short between any positive (`+`) pad and any other positive (`+`) pad
* a short between any negative (`-`) pad and any other negative (`-`) pad
* **no short** between any positive (`+`) pad and any negative (`-`) pad
```

### Do a *DC voltage check* on the PDB.
```{warning}

Perform the voltage check **only** if the connectivity check passed. 
```
Plug in a 12V battery and verify there is:

* ~0V between any positive (`+`) pad and any other positive (`+`) pad
* ~0V between any negative (`-`) pad and any other negative (`-`) pad
* ~12V between any positive (`+`) pad and any negative (`-`) pad.


```{note} If the battery is X volts instead of 12 volts (e.g. 10), then the multimeter will show X volts instead of 12 volts.
```

## ESC check
```{warning} **only** if the DC voltage check passed (in the previous section), perform the ESC check.
```
Re-connect the battery to your drone.

Verify the following:

* The PDB board lights up.
* Each ESC emits a noise (it does so by performing a slight rotation, so you should also notice some subtle movements of each motor)
