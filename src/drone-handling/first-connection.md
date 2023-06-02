(first_connection)=
# First connection

You are now ready to connect to your Duckiedrone through the Duckietown Dashboard.

```{needget}

*   A live `DD21` ([First Boot](sec:first-boot))

*   A base station with wireless connectivity, or a pre-existing network

---

*   A fully operational `DD21`

```


## Connecting to the Duckiedrone  
Make sure you are on the same network as your Duckiedrone:
    
::::{tab-set}

:::{tab-item} Access Point (AP) mode

Connect to `duckietown-<hostname>-ap` if the drone is in AP mode, where `<hostname>` is the robot name chosen during the initialization procedure.

If you forgot to change it, the default hostname is `amelia`.

:::

:::{tab-item} Client (CL) mode

Connect to the same network that the drone is connected to if the drone is in CL mode.

The default network is `duckietown` (password: `quackquack`)  

:::

::::
    
## Accessing the Duckiedrone functionalities

```{admonition} Cheatsheet
:class: note

Default robot name: `amelia`

Default ssh user name: `duckie`

Default ssh user password: `quackquack`

Ssh always possible: `ssh duckie@amelia.local`

**Default** access point (**AP**) network configuration:

*   SSID: `duckietown-amelia-ap`
    
*   Password: `quackquack`
    

**Default** client (**CL**) network configuration:

*   SSID: `duckietown`
    
*   Password: `quackquack`
```

## Troubleshooting

```{trouble}
I cannot connect to my Duckiedrone in AP mode.
---
Try using client mode and shut down the docker container `dt-access-point` through the Portainer interface (accessible through your browser from your base station at `<hostname>.local:9000`)
```
