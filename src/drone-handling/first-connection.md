# First connection

You are now ready to connect to your Duckiedrone through the Duckietown Dashboard.

#### What you will need:

*   A live `DD21` ([https://ethidsc.atlassian.net/l/cp/i12MEjsu](https://ethidsc.atlassian.net/l/cp/i12MEjsu))
    
*   A Duckietown token ([https://docs.duckietown.org/daffy/opmanual\_duckiebot/out/dt\_account.html](https://docs.duckietown.org/daffy/opmanual_duckiebot/out/dt_account.html))
    
*   A base station with wireless connectivity, or a preexisting network
    

#### What you will get:

*   A fully operational `DD21`
    

# Cheatsheet

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
    

# Connecting to the Duckiedrone  

Any Duckiedrone is accessible by any base station through a browser, but only the first user setting up a Dashboard will have admin powers over it.

For best performance, we recommend using Google Chrome as browser.

1.  Obtain and write down your Duckietown token before starting this procedure
    
    1.  Follow the "Setup Duckietown Account” instruction (Sec. 2.1, 2.2) here: [https://docs.duckietown.org/daffy/opmanual\_duckiebot/out/dt\_account.html](https://docs.duckietown.org/daffy/opmanual_duckiebot/out/dt_account.html)  
        The token will look something like this:  
        
        ```
        dt1-daZUHiuSz7CUfhK5S8sExu63FeQrye2twajB1kvtReZqv-xxxxxxxxxxxxxxxxxxx
        ```
        
2.  Make sure you are on the same network as your Duckiedrone
    
    1.  Connect to `duckietown-<hostname>-ap` if the drone is in AP mode, where `<hostname>` is the robot name chosen during the initialization procedure. If you forgot to do it, the default hostname is `amelia`.
        
    2.  Connect to the same network of the drone if the drone is in CL mode. The default network is `duckietown` (psw: `quackquack`)  
        
3.  Access the Dashboard interface
    
    1.  Open a browser and navigate to: `http://hostname.local` (where `hostname`… yep)
        
    2.  You will be greeted by the Dashboard configuration screen (only at first log-in):  
        
4.  Configure the Dashboard TO BE UPDATED BY JT
    
    1.  **Steps 1 and 2** of the Dashboard setup will appear as already completed, this is normal. We will start from Step 3.
        
    2.  **Step 3:** The Dashboard is built using a framework called `\compose\` and the first tab on the dashboard’s setup page is its configuration. You can leave the default values here and press “Next”. Feel free to change the timezone if you feel like it.  
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220712-195356.png?api=v2)
        
    3.  **Step 4:** In this tab, we will be prompted to agree to the terms and conditions of Duckietown. Follow the instructions on the screen. It is necessary to accept Duckietown terms to use Duckietown software.  
          
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220712-195908.png?api=v2)
        
          
        
    4.  **Step 5:** Provide permissions for Duckietown to collect anonymous data for useful debugging, system, and user experience improvements. Acceptance of these permissions is not mandatory but refusing will prevent Duckietown from offering assistance and other useful services like configuration backups, access to the logs database, and more. Click on “Next” when done.  
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220712-200411.png?api=v2)
        
          
        
    5.  **Step 6:** This tab contains general information. Simply click “Finish” to complete the setup.  
        

Congratulations, you are now connected to your Duckiedrone and should already start seeing live diagnostics data. A nominal setup would be like the picture below. If you reached this step it means the drone is healthy and you are able to talk to it through your base station. The fun part is yet to start!  

![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220712-200756.png?api=v2)

# Accessing the Duckiedrone functionalities

Albeit connected to the Duckiedrone, we need to provide our Duckietown user profile information before being able to access more advanced functionalities.

1.  Click on the “Login” button on the top left of the Dashboard  
      
    
    ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220713-075618.png?api=v2)
    
2.  Click on “Sign in with Duckietown" and provide your Duckietown token (you should have this written down). Click “Login” to proceed.  
      
    You should now be redirected to your User profile page, and be able to see many more options in the left nav bar:
    

![](https://ethidsc.atlassian.net/wiki/download/attachments/2227503282/image-20220713-075833.png?api=v2)

We are now ready to investigate some of the most exciting features of the Duckiedrone Dashboard ([https://ethidsc.atlassian.net/l/cp/iyPW131R](https://ethidsc.atlassian.net/l/cp/iyPW131R)).