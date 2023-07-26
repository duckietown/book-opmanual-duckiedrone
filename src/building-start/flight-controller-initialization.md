# II. Initializing the Flight Controller

```{admonition} What you will need
:class: note

* A base station computer
* Flight Controller
* USB to micro USB cable
```


```{admonition} What you will get

* An up-to-date, initialized Flight Controller
```

The Flight Controller (FC) implements several low-level behaviors, e.g., stabilizing the Duckiedrone around roll, pitch, and yaw through three different PID controllers. Correctly configuring the Flight Controller is critical for flying safely.  

## 1. Installing Cleanflight Configurator (CFC)
Cleanflight Configurator is an app that allows the base station to connect directly to the Flight Controller and access its configuration interface.

```{note}
Cleanflight Configurator used to be a Chrome App, however Chrome Apps' support has been dropped from Google so you will use the native app for your OS.
```

Steps:

a.  Download the correct version of Cleanflight Configurator v2.4.0 for your OS from [**this link**](https://github.com/cleanflight/cleanflight-configurator/releases/tag/CLFL_v2.4.0).

b. Install Cleanflight Configurator on your system

c. Start Cleanflight Configurator on your base station. You should see the below interface.

    ```{figure} ../_images/software-initialization/CFC_welcome_screen.png

    Cleanflight Configurator (CFC) `welcome screen`
    ```

## 2. Flashing the correct firmware

### Updating the Flight Controller firmware (Flashing the Flight Controller)

Flight Controllers might have different versions of firmware (i.e., the software that runs on the Flight Controller microcontroller) out of the factory. Normally, this only needs to be done once initially. Follow this procedure to update your firmware.

```{attention}
During flashing, do not press the `“Connect”` button in Cleanflight Configurator. 
```

a. Our current target firmware is: 

*   **BTFL v3.3.3** (Download the `.hex` file below to your base station) [Download BTFL v3.3.3 here](https://github.com/betaflight/betaflight/releases/download/v3.3.3/betaflight_3.3.3_SPRACINGF3.hex)


### 3. Prepare for flashing the Flight Controller firmware

```{attention}
Regardless of the firmware version, if it is the first time setting up the Flight Controller, we recommend performing the below flashing procedure once anyways in order to start from a clean state.
```

Perform the following 2 steps with the Flight Controller **disconnected**.

       a. In the default Welcome page of Cleanflight Configurator, in the left sidebar, please click on the `Firmware Flasher` tab 
    ```{figure} ../_images/software-initialization/cleanflight_flasher.png

    `Firmware Flasher` tab in Cleanflight Configurator
    ```

        b. Configure the options in the tab as below:
    ```{figure} ../_images/software-initialization/flasher_parameters.png

    `Firmware Flasher` parameters to set
    ```
        
### Different Flight Controller versions

There are currently 2 types of Flight Controller hardware. Use the steps corresponding to your hardware. Videos for both hardware versions are provided later in the document.

```{attention} 

If you have the `OSD` version of the Flight Controller you need to solder the micro USB adapter before being able to connect to the base station.

**Choose in the following tabs which Flight Controller version you have**
```

```{seealso}
Identify your flight controller in [**this chapter**](identifying_fc).
```


::::{tab-set}

:::{tab-item} OSD
You will need to solder the pins to the microUSB board and connect it to the Flight Controller.

```{admonition} what you'll need
:class: note

*   soldering tools
*   Flight Controller microUSB board
*   90° header pins
*   6 pins cable connector (in the Flight Controller bag)
```

```{admonition} what you'll get
*   `OSD` Flight Controller connected to the base station
```

a.  Solder the 90° pins to the microUSB board as shown
    ```{figure} ../_images/software-initialization/OSD_usb_board.jpg
    :width: 300px

    Pins soldered to the microUSB board
    ```

b.  Connect the 6 pins cable that came with the Flight Controller to the microUSB board according to the following table (there's one unused `GND` pin on the board). 

    |USB board pin  |Cable color  |
    |:---           |---:         |
    |`GND`          |Black        |
    |`5.0V`         |Red          |
    |`TXD`          |Yellow       |
    |`RXD`          |Green        |
    |`DTR`          |White        |

    ```{figure} ../_images/software-initialization/OSD_usb_board_connection.png

    USB board pinout connection
    ```
    
    ````{attention}
    **Once you verify the connection** between the base station and the Flight Controller, it is recommended to hot glue the pins in place.

    ```{image} ../_images/software-initialization/OSD_usb_hot_glued.png
    :width: 300px
    ```

    ````

c.  Connect the white connector of the 6 pins cable to the Flight Controller port shown here.
    ```{figure} ../_images/software-initialization/usb_connector_port_OSD.jpg

    Connect the white end of the 6 pin cable to this port on the Flight Controller
    ```

:::

:::{tab-item} ACRO

The microUSB port is already soldered to your board, you can go on with the tutorial.

:::

::::

## 4. Flashing the Flight Controller

The videos to flash the **ACRO** version and the **OSD** version of Flight Controllers are below in this section, in their respective tab. 

A summary is provided here.

Most operations are the same with both versions, and any version-wise operations are written in the respective tab.

```{attention}
Normally, when connected to the base station, the Flight Controller connects in `Normal mode`.

This can be identified by:

*    Having a red blinking LED on the Flight Controller board

If this is the case during this section, unplug from base station and try to reactivate `bootloader mode` as detailed below.
```

To flash the firmware, we need the Flight Controller to be in `bootloader mode`.

**Start by having the Flight Controller disconnected**

::::{tab-set}

:::{tab-item} OSD

a. Identify the `"BO"` pins on the board

    ```{figure} ../_images/software-initialization/OSD_boot_pins.jpg

    Location of the boot pins `"BO"` on the `OSD` Flight Controller
    ```

b. Use some conductive metal tool to short the `"BO"` while connecting the USB cable

c. Once connected, you can take the pin-shorting material/tool away

    ```{admonition} Check
    :class: seealso

    there is no red blinking LED. There should be no LED on now on the Flight Controller (there is a red LED on the USB board).

d. The Flight Controller is now in `bootloader mode`

:::

:::{tab-item} ACRO

a. Identify the `"BOOT"` button on the Flight Controller

    ```{figure} ../_images/software-initialization/ACRO_boot_button.jpg

    Location of the boot button `"BOOT"` on the ACRO Flight Controller
    ```

b. hold the `“BOOT”` button while connecting the Flight Controller to base station

c. Once connected, one could release the boot button

d. Check there is a solid blue LED, **not a red blinking LED**.

e. The Flight Controller is now in `bootloader mode`

:::

::::

Now that the Flight Controller is in `bootloader mode` you can flash the correct firmware:

a.  In the Cleanflight Configurator Firmware Flasher tab, click the `Load Firmware [Local]` button (bottom right), and select the `.hex` file downloaded at the beginning of this section.

    ```{admonition} Check
    :class: seealso

    The progress bar should look like `“Loaded Local Firmware: (… bytes)”`
    ```

b.  Click the Flash Firmware button (bottom right) and check the progress bar.

    ```{admonition} Check
    :class: seealso
    
    The progress bar shows: `“Flashing…”` => `“Verifying…”` => `“Programming SUCCESSFUL”`
    ```

    ```{tip}
    In case the progress bar turns red, see the [Troubleshooting section below](fc_initialization_troubleshooting)
    ```

c.  If successful, without needing to reconnect the cable, the Flight Controller should go back to the `Normal mode`.

    ```{admonition} **Check**
    :class: seealso

    1. Verify the red blinking LED is back on

    1. Click `“Connect”` and verify the firmware version is correct as detailed below
    ```

```{attention}
To see the whole process for your version of the Flight Controller choose the correct tab below:
```

::::{tab-set}

:::{tab-item} OSD

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/797686771?h=24e66cc7e7&badge=0&autopause=0&player_id=0&app_id=58479/embed" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen frameborder="0" style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe></div>

:::

:::{tab-item} ACRO

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/797686809?h=c32430cc49&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="FC(with microUSB) flash firmware"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

:::

::::

## 5. onnecting to the Flight Controller

a.  Unplug the battery from your drone

    ```{attention}
    Double-check the battery is unplugged
    ```

b.  Connect the micro USB cable from your Flight Controller to your base station

c. Identify the `"Connect"` button in the top right corner (right now it will be green as the Flight Controller is not connected yet)
    ```{figure} ../_images/software-initialization/CFC_connect_button.png

    `"Connect"` button in the top-right corner of Cleanflight Configurator

d. Select the correct connection port

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
e. Leave the baud rate (number) at the default value of `115200`

f.  Press the `“Connect”` button and a `“Setup”` page should greet you with a rendering of your drone (see figure below).

```{figure} ../_images/software-initialization/CFC_setup_screen.png

Cleanflight Configurator `"Setup"` page
```

```{attention}
g. Please check below that you have the correct version:

*   Firmware:   `BTFL 3.3.3`
```

### Checking the firmware version

On the top left of the Cleanflight Configurator interface, one could check for the Firmware version. For example, in the figure below, the firmware version of the Flight Controller is `BTFL 3.3.3`.

```{figure} ../_images/software-initialization/cleanflight_firmware_version.png

Top left of Cleanflight Configurator, check Cleanflight Configurator version and Flight Controller firmware version here
```

## 6. Restoring the correct settings
We will restore the correct settings for the Flight Controller that reflect the setup we have on Duckiedrones (i.e. Flight Controller upside down, ESCs communication protocol, etc.)

The settings for the Flight Controller can be saved and restored through the CLI interface of Cleanflight, which is akin to a shell used to interact with the firmware.

We have created a file with the required setup for you, so you will only need to restore it without having to tweak parameters through the Cleanflight Configurator.

To do this:

a.  Download [this](https://assets.duckietown.com/robot/duckiedrone/cleanflight_cli_dump.txt) `.txt` configuration file.

b.  Open it in the notepad app of your base station

c.  Copy all content of the file from the notepad by simply clicking on the text and using <kbd>CTRL</kbd> + <kbd>A</kbd> or <kbd>CMD</kbd> + <kbd>A</kbd>

d.  Go in the `CLI` tab of Cleanflight Configurator
    ```{figure} ../_images/software-initialization/fc_cli_tab.png
    :width: 300px

    CLI tab
    ```
e.  Paste all the text you previously copied using <kbd>CTRL</kbd> + <kbd>V</kbd> or <kbd>CMD</kbd> + <kbd>V</kbd> in the text field at the bottom (the one with the text  `Write your command here. Press Tab for AutoComplete`).
    ```{figure} ../_images/software-initialization/fc_cli_interface.png

    CLI interface
    ```
f.  Press `Enter` on your keyboard to execute the commands and wait for the shell to finish (it should take about 30 seconds)

g.  Save the configuration by executing the command `save` in the CLI.

The Flight Controller will now reboot and reconnect.

```{admonition} Check
:class: seealso

In the `setup` tab check that the drone now results facing up when the side of the Flight Controller with the chips faces downward.
```

(fc_initialization_troubleshooting)=
## Troubleshooting

```{trouble}
The `OSD` version of the Flight Controller does not enter `bootloader mode`
---
It is tricky to jump the exposed Boot pins. Try applying a bit of force when pressing on the pins. If possible, also try verifying they have actually been jumped with a multi-meter.
```

```{trouble}
The progress bar turns red and shows `"No response from the bootloader, programming:FAILED"`
---
It might happen when, on the Firmware Flasher tab, the Flash Firmware button is clicked. This is likely due to the Flight Controller not being in Bootloader mode. Please double check the indicators of that mode in the section above.
```

```{trouble}
`"Flashing..."` started, but progress bar turns red with a `"Timeout"` error
---
It might happen during “Flashing…” or “Verifying…”. Click the `Flash Firmware` button and try again
```

````{trouble}
On Linux, Cleanflight Configurator doesn't connect to the Flight Controller and an error `Failed to open serial port` appears in the log 
---
This is a permission issue to access the serial port of the Flight Controller. 
First try to run `sudo usermod -a -G dialout <USERNAME> `, replacing <USERNAME> with your base station username; this will add your user to the group that has access to the serial ports. **Reboot** for the change to take effect.

If this doesn't work, the quickest solution is to run `sudo chmod 0777 /dev/tty*` while Cleanflight Configurator is open, where `/dev/tty* is the port you're using to connect to the Flight Controller.

This second procedure has to be done each time the Flight Controller is reconnected to the base station.

````


```{trouble}
   
I'm using Ubuntu 22.04 and Cleanflight Configurator does not open nor install.
---
If that's the case use Cleanflight Configurator v2.6.0 from [here](https://github.com/cleanflight/cleanflight-configurator/releases/tag/CLFL_v2.6.0)
```

```{trouble}
   
I'm using Ubuntu 22.04 and Cleanflight Configurator freezes when flashing the firmware.
---
Proceed with the following workaround:

1. Open Cleanflight Configurator.
2. Go in the `Firmware Flasher` tab.
3. Select the `Flash on connect` option.
4. Load the firmware with `Load Firmware [Local]` (the screen will freeze, this is expected).
5. Connect the flight controller. The flashing will start at this point.

```
```{trouble}
Other issues
---
We’re happy to support! Please contact our hardware team via email: [hardware@duckietown.com](mailto:hardware@duckietown.com)
```
