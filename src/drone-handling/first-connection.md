(first-connection)=
# First connection

You are now ready to connect to your Duckiedrone through the Duckietown Dashboard.

```{needget}

*   A live `DD21` ([First Boot](../first-boot.md))

*   A Duckietown token ([See here](https://docs.duckietown.org/daffy/opmanual_duckiebot/out/dt_account.html) how to obtain it)

*   A base station with wireless connectivity, or a pre-existing network

---

*   A fully operational `DD21`

```

```{admonition} Cheatsheet
:class: note

Default robot name: `amelia`

Default user name: `duckie`

Default user password: `quackquack`

Ssh always possible: `ssh duckie@amelia.local`

**Default** access point (**AP**) network configuration:

*   SSID: `duckietown-amelia-ap`
    
*   Password: `quackquack`
    

**Default** client (**CL**) network configuration:

*   SSID: `duckietown`
    
*   Password: `quackquack`
```

## Connecting to the Duckiedrone  

Any Duckiedrone is accessible by any base station through a browser, but only the first user setting up a Dashboard will have admin powers over it.

For best performance, we recommend using Google Chrome as browser.

1.  Obtain and write down your Duckietown token before starting this procedure
    
    *  Follow the "Setup Duckietown Account” instruction (Sec. 2.1, 2.2) [here](https://docs.duckietown.org/daffy/opmanual_duckiebot/out/dt_account.html)  

        ````{tip}
        The token will look something like this:  
        
        ```
        dt1-daZUHiuSz7CUfhK5S8sExu63FeQrye2twajB1kvtReZqv-xxxxxxxxxxxxxxxxxxx
        ```
        ````
        
2.  Make sure you are on the same network as your Duckiedrone
    
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
        
        
3.  Access the Dashboard interface
    
    * Open a browser and navigate to: `http://<hostname>.local` (where `<hostname>` is the name of your Duckiedrone)
        
4.  Configure the Dashboard: at the first login you will be greeted by the Dashboard configuration screen
    
    1.  **Steps 1 and 2** of the Dashboard setup will appear as already completed, this is normal. We will start from Step 3.
        
    2.  **Step 3:** The Dashboard is built using a framework called `\compose\` and the first tab on the dashboard’s setup page is its configuration. You can leave the default values here and press {bdg-success}`Next`.
    
        Feel free to change the timezone if you feel like it.  
        
        ```{figure} ../_images/first-connection/step_3.png
        
        Step 3
        ```

    3.  **Step 4:** In this tab, you will be prompted to agree to the terms and conditions of Duckietown. Follow the instructions on the screen. It is necessary to accept Duckietown terms to use Duckietown software.  
        
        ```{figure} ../_images/first-connection/step_4.png

        Step 4
        ```          
        
    4.  **Step 5:** Provide permissions for Duckietown to collect anonymous data for useful debugging, system, and user experience improvements.
    
        Acceptance of these permissions is not mandatory but refusing will prevent Duckietown from offering assistance and other useful services like configuration backups, access to the logs database, and more.
    
        Click on {bdg-success}`Next` when done.  
        ```{figure} ../_images/first-connection/step_5.png
        
        Step 5
        ```
          
        
    5.  **Step 6:** This tab contains a recap of the information. Simply click {bdg-success}`Finish` to complete the setup.  
        

Congratulations, you are now connected to your Duckiedrone and should already start seeing live diagnostics data. A nominal setup would show a {bdg-warning}`ROBOT` page as in the picture below. If you reached this step it means the drone is healthy and you are able to talk to it through your base station. The fun part is yet to start!  

```{figure} ../_images/first-connection/robot_dashboard.png

Robot dashboard
```

## Accessing the Duckiedrone functionalities

Albeit connected to the Duckiedrone, we need to provide our Duckietown user profile information before being able to access more advanced functionalities.

1.  Click on the {bdg-warning}`Login` button on the top left of the Dashboard  
    
    ```{image} ../_images/first-connection/dashboard_sign_in.png
    ```
    
2.  Click on {bdg-warning}`Sign in with Duckietown` and provide your Duckietown token (you should have this written down). Click {bdg-dark-line}`Login` to proceed.  
      
    You should now be redirected to your User profile page, and be able to see many more options in the left nav bar:
    
    ```{image} ../_images/first-connection/setup_complete.png
    ```

We are now ready to investigate some of the most exciting features of the Duckiedrone Dashboard.

## Troubleshooting

```{trouble}
I cannot connect to my Duckiedrone in AP mode.
---
Try using client mode and shut down the docker container `dt-access-point` through the Portainer interface (accessible through your browser from your base station at `<hostname>.local:9000`)
```