(sw-initialization)=
# Software initialization

```{admonition} What you will need
:class: note

* A computer (a.k.a. “base station”) with an internet connection

* Balena Etcher or similar program

* A micro SD card (32GB, U3, Class 10), e.g., that from your Duckiebox 

* A micro SD card reader, e.g., that from your Duckiebox
```

```{admonition} What you will get

* A DD21 initialized and customized micro SD card
```

## Flashing the SD card

In this section you will install the Duckiedrone software on the microSD card.

1. If you have not already, on a base station, download the image flashing tool [Etcher](https://www.balena.io/etcher/).

1. If you have not already, on a base station, download the latest drone image:

    ```{button-link} https://duckietown-public-storage.s3.amazonaws.com/brown/disk_image/dt-amelia-DD21-brown2022-sd-card-v12.zip
    :color: primary
    :shadow:
    
    DD21 system image
    ```

1. Connect the micro SD card to the base station. Use the micro SD to USB card reader if the base station does not have a micro SD port.
  
    ```{figure} ../_images/components-official/microSD_reader.png
    :width: 400px

    Micro SD Card adapter
    ```

1. Open Etcher and select the downloaded drone image. Then select the micro SD card as the drive to flash. Finally, click the `"Flash"` button.

Watch this video to see how the process looks like.

```{vimeo} 795166491
:alt: sd card flashing procedure
```

<div style="padding:61.68% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/795166491?h=ad68dd5e48&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;" title="Screencast from 01-02-2023 170837"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

```{warning} **Double check** that the "drive" is your micro SD card.

You may be prompted to enter the base station password to proceed. This is normal: flashing an SD card deletes everything that is on it, so Etcher is making sure this process is OK with you.
```

```{note} Flashing will take 10 - 15 min. In the meantime, you can move on to the next section.
```

## Customizing the Duckiedrone `hostname` and client network settings

```{warning}
This step is particularly important.

Skipping it means having to re-flash the SD card.
```

Changing the Duckiedrone `hostname` (also known as the “robot name") is needed to prevent conflicts when multiple Duckiedrones are operating in the same environment. If you intend to operate the drone in isolation from other Duckiedrones (e.g., at home), you can maintain the default settings.

```{warning}
The `hostname` can only be changed at this stage in the process. **It cannot** be changed later.
```

```{attention}
The `hostname` **must** start with a lower case letter and can contain **only** lower case letters (of the latin alphabet) and numbers:

Using special characters will break things and require re-flashing

Examples:

* ✅ `argo`
* ✅ `mydrone01`
* ❌ `mydrone_01`
* ❌ `My Drone`
* ❌ `Argo`
```

```{attention}
If you are in an environment where multiple drones are operating at the same time, make sure your `hostname` is unique!
```

1. To change your robot’s `hostname` navigate to the newly flashed SD card.

    * You will have to unplug it from your base station first and plug it back in as Balena Etcher dismounts the drive after finishing the flashing process.

    * If the flashing is successful, you will see that it has one partition named `boot`, with many files inside and `overlays` folder. **Do not** manually alter these files.

      ```{figure} ../_images/rpi-sw-initialization/boot_partition.png
      :width: 200px

      `boot` partition, **do not** alter!
      ```

1. There will be a second partition called `config`. Open this partition. You will find two files inside:

    * `hostname`

    * `wpa_supplicant.conf`

    ```{figure} ../_images/rpi-sw-initialization/config_partition.png

    `config` partition content
    ```

1. Open the `hostname` file with any text editor program (e.g., Notepad on Windows) and replace the default robot name, `amelia`, with one of your choosing.  

    ```{warning}
    Make sure to follow the naming guidelines in the `attention` box above. 
    ```

    A wrong `hostname` will mean having to reflash the SD card and start from step 1.

    ```{attention}
    **Save** the file before closing it.
    ```

1. Open the `wpa_supplicant.conf` with a text editor of your choice and either edit the default connection settings or duplicate them to add a new network. These parameters will be used only when booting the Duckiedrone in client-network mode, i.e. connecting to an existing Wi-Fi access point.

    ```bash
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=US

    # NOTE: the following block is a template, use it to define connection to custom wifi networks
    network={
      id_str="network_1"
      ssid="duckietown"
      psk="quackquack"
      key_mgmt=WPA-PSK
    }
    ```

    * `country`: change it if you are not in the US (e.g., `CH` for Switzerland, `CA` for Canada; [full list](https://www.arubanetworks.com/techdocs/InstantWenger_Mobile/Advanced/Content/Instant%20User%20Guide%20-%20volumes/Country_Codes_List.htm) of country codes)

    * `id_str`: an identifier for the network; change it if adding a new one;

    * `SSID`: name of the Wi-Fi you want the Duckiedrone to connect to;

    * `psk`: password for the above Wi-Fi;

    You can add as many Wi-Fi settings as you want, e.g., for home, school, office, etc., by copying and pasting the first block.

    ```{note}
    This file can be edited after the first boot as well if you want to add other networks.
    ```

    ```sh
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=US

    # NOTE: the following block is a template, use it to define connection to custom wifi networks
    network={
      id_str="network_1"
      ssid="duckietown"
      psk="quackquack"
      key_mgmt=WPA-PSK
    }

    network={
      id_str="network_2"
      ssid="example-second-network"
      psk="quackquack2"
      key_mgmt=WPA-PSK
    }

    network={
      id_str="network_3"
      ssid="example-third-network"
      psk="quackquack3"
      key_mgmt=WPA-PSK
    }
    ```

````{admonition} Eject your SD card safely.
:class: warning

Do not just unplug the SD crad from the base station

```{image} ../_images/rpi-sw-initialization/eject_sd.png
:width: 300px
```
````

You are now ready for the first boot.

## Troubleshooting

````{trouble}
I’m using a Mac and the Flashing step fails for lack of permissions.
---

Go to your computer’s `System Preferences > Security & Privacy > Files and Folders` and enable access to `Removable Volumes`
![](../_images/rpi-sw-initialization/mac_troubleshooting.png)

````
