# Initializing the Flight Controller

**What you will need before starting**:

* A base station computer
* Flight Controller
* USB to Micro USB cable

**What you will have after finishing**:

* An up-to-date, initialized Flight Controller

The flight controller (FC) implements several low-level behaviors, e.g., stabilizing the Duckiedrone around roll, pitch, and yaw through three different PID controllers. Correctly configuring the FC is critical for flying safely.  

## Installing Cleanflight Configurator (CFC)
Cleanflight configurator is an app that allows the base station to connect directly to the FC and access its configuration interface.

```{note}
Cleanflight Configurator used to be a Chrome App, however Chrome Apps' support has been dropped from Google so we'll use native apps for your OS.
```

Steps:

1.  Download the correct version of Cleanflight Configurator v2.4.0 for your OS from [**this link**](https://github.com/cleanflight/cleanflight-configurator/releases/tag/CLFL_v2.4.0).

1. Install Cleanflight Configurator on your system

1. Start CFC on your base station. You should see the below interface.

```{figure} ../_images/software-initialization/CFC_welcome_screen.png

Cleanflight Configurator (CFC) welcome screen
```

## Flashing the correct firmware

### Prepare for flashing the FC firmware

```{important}
Regardless of the firmware version, if it is the first time setting up the Fligh Controller, we recommend performing the below flashing procedure once anyways in order to start from a clean state.
```

Perform the following 2 steps with the Flight Controller disconnected.

*   In the default Welcome page of CFC, in the left sidebar, please click on the Firmware Flasher tab 
    ```{figure} ../_images/software-initialization/cleanflight_flasher.png

    **Firmware Flasher** tab in Cleanflight Configurator
    ```

*   Configure the options in the tab as below:
    ```{figure} ../_images/software-initialization/flasher_parameters.png

    Firmware Flasher parameters to set
    ```

### Updating the FC firmware (Flashing the FC)

FCs might have different versions of firmware (i.e., the software that runs on the FC’s micro-controller) out of the factory. Normally, this only needs to be done once initially. Follow this procedure to update your firmware.

```{important}
During flashing, do not press the `“Connect”` button in CFC. 
```

Our current target firmware is: 

*   BTFL v3.3.3  (Download the `.hex` file below to your base station) [Download BTFL v3.3.3 here](https://github.com/betaflight/betaflight/releases/download/v3.3.3/betaflight_3.3.3_SPRACINGF3.hex)

### Different FC versions
There are currently 2 types of FC hardware. Use the steps corresponding to your hardware. Videos for both hardware versions are provided later in the document.

[TODO: ADD THE LINK TO FC IDENTIFICATION OR MOVE IT HERE]

```{attention} 

If you have the `OSD` version of the Flight Controller you need to solder the micro USB adapter before being able to connect to the base station.

**Choose in the following tabs which Flight Controller version you have**
```

::::{tab-set}

:::{tab-item} OSD

:::

:::{tab-item} ACRO

:::

::::

## Flashing the FC

The videos to flash respectively the **ACRO** version and the **OSD** version of Flight Controllers are below in this section. A summary is provided here. Most operations are the same with both versions, and any version-wise operations are written in the respective tab.

```{attention}
Normally, when connected to the base station, the Flight Controller connects in `Normal mode`.

This can be identified by:

*    Having a red blinking LED on the board

If this is the case during this section, unplug from base station and try to reactivate `bootloader mode` as detailed below.
```

To flash the firmware, we need the FC to be in Bootloader mode instead.

**Start by having the Flight Controller disconnected**

::::{tab-set}

:::{tab-item} OSD

1. Identify the `"BO"` pins on the board

    ```{figure} ../_images/software-initialization/OSD_boot_pins.jpg

    Location of the boot pins `"BO"` on the OSD Flight Controller
    ```

2. Use some conductive metal tool to short the `"BO"` while connecting the USB cable

1. Once connected, you can take the pin-shorting material/tool away

1. **check** there is no red blinking LED. There should be no LED on now on the Flight Controller (there is a red LED on the USB board).

1. The Flight Controller is now in `bootloader mode`

:::

:::{tab-item} ACRO

1. Identify the `"BOOT"` button on the Flight Controller

    ```{figure} ../_images/software-initialization/ACRO_boot_button.jpg

    Location of the boot button `"BOOT"` on the ACRO Flight Controller
    ```

1. hold the `“BOOT”` button while connecting the FC to base station

1. Once connected, one could release the boot button

1. Check there is a solid blue LED, **not a red blinking LED**.

1. The Flight Controller is now in `bootloader mode`

:::

::::

Now that the Flight Controller is in `bootloader mode` you can flash the correct firmware:

1.  In the CFC Firmware Flasher tab, click the `Load Firmware [Local]` button (bottom right), and select the .hex file downloaded at the beginning of this section.

    - **check** The progress bar should look like `“Loaded Local Firmware: (… bytes)”`

1.  Click the Flash Firmware button (bottom right) and check the progress bar.

    -   **check** The progress bar shows: `“Flashing…”` => `“Verifying…”` => `“Programming SUCCESSFUL”`

    ```{tip}
    In case the progress bar turns red, see the Troubleshooting section below
    ```

3.  If successful, without needing to reconnect the cable, the FC should go back to the Normal mode.

    ```{admonition} **Check**
    
    * Verify the red blinking LED is back on

    * Click `“Connect”` and verify the firmware version is correct as detailed below
    ```

To see the whole process for your version of the Flight Controller choose the correct tab below:

::::{tab-set}

:::{tab-item} OSD

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/797686771?h=24e66cc7e7&badge=0&autopause=0&player_id=0&app_id=58479/embed" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen frameborder="0" style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe></div>

:::

:::{tab-item} ACRO

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/797686809?h=c32430cc49&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="FC(with microUSB) flash firmware"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

:::

::::

### Checking the existing firmware version

On the top left of the CFC interface, one could check for the Firmware version. For example, in the figure below, the firmware version of the FC is BTFL 3.3.3.

```{figure} ../_images/software-initialization/cleanflight_firmware_version.png

Top left of CFC, check CFC version and FC firmware version here
```

## Connecting to the Flight Controller (FC)

1.  Unplug the battery from your drone

    ```{important}
    Double-check the battery is unplugged
    ```

1.  Connect the micro USB cable from your FC to your base station

1. Identify the `"Connect"` button in the top right corner (right now it will be green as the Flight Controller is not connected yet)
    [add image of connect button]

1. Select the correct connection port

    ```{tip}
    Details might vary depending on available connections on your base station. 
    
    The correct port should start with: 

    *   Linux/macOS
        *   `/dev/tty.usbserial*`
        *   `/dev/cu.usbserial*` 
        *   `/dev/ttyUSB*`
    *   Windows
        *   `COM*`
    ```
1. Leave the baud rate (number) at the default value of `115200`

1.  Press the `“Connect”` button and a `“Setup”` page should greet you with a rendering of your drone (see figure below). Before configuring anything, please read the next section and flash the firmware.

## Troubleshooting

```{trouble}
The OSD version of the Flight Controller does not enter `bootloader mode`
---
It is tricky to jump the exposed Boot pins. Try applying a bit of force when pressing on the pins. If possible, also try verifying they have actually been jumped with a multi-meter.
```

```{trouble}
The progress bar turns red and shows `"No response from the bootloader, programming:FAILED"`
---
It might happen when, on the Firmware Flasher tab, the Flash Firmware button is clicked. This is likely due to the FC not being in Bootloader mode. Please double check the indicators of that mode in the section above.
```

```{trouble}
`"Flashing..."` started, but progress bar turns red with a `"Timeout"` error
---
It might happen during “Flashing…” or “Verifying…”. Click the `Flash Firmware` button and try again
```

```{trouble}
Other issues
---
We’re happy to support! Please contact our hardware team via email: [hardware@duckietown.com](mailto:hardware@duckietown.com)
```