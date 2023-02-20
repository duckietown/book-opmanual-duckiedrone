There is only one first time you can connect to your Duckiedrone. Savoir the experience.

#### What you will need:

*   An assembled DD21 ([https://ethidsc.atlassian.net/l/cp/QoKKr1xz](https://ethidsc.atlassian.net/l/cp/QoKKr1xz))
    
*   A `DD21` initialized SD card ([https://ethidsc.atlassian.net/l/cp/VzDw80Fi](https://ethidsc.atlassian.net/l/cp/VzDw80Fi))
    

#### What you will get:

*   A live `DD21`
    

# The first boot: before getting started

The first time a newly flashed SD card is inserted in the Duckiedrone a special “first boot” procedure is executed.

The first boot procedure will take roughly 10-15 minutes, during which your Raspberry Pi might look unresponsive. It is crunching as fast as it can, do not worry.

Do not start this procedure if you do not have the time to finish it!

During this process the Duckiedrone will require a stable power source. Make sure you have a wall outlet power adapter, e.g., a phone charger (5V, 2-3A) or a fully charged Duckiebattery before starting the process. Do not power the Raspberry Pi just yet.

Do not interrupt the first boot procedure, e.g., by removing power to the Raspberry Pi. It will likely corrupt the SD card. A corrupted SD card will have to be flashed again.

# The first boot: getting started

1.  Make sure the Raspberry Pi is **not powered.**  
    
2.  Make sure you have a wall adapter or fully charged battery available.  
    
3.  Networks are typically one of the biggest headaches in robotics. We offer different network configurations to minimize these headaches. If you are not sure which choice to make, the right answer typically is: if you are in a university go for AP mode. If you are at home go for CL mode. In both cases, you need to place the jumper accordingly on your 5&6 pins before getting started.  
    
    1.  **Access point (AP) mode**: if you want to have the drone emit its own Wi-Fi network that your base station can connect to. This is the go-to choice if you do not have a network (WLAN) or admin access to the existing network where you are operating.  
        
        1.  Pros:
            
            *   You can connect to your drone without the need for a pre-existing existing network infrastructure  
                
        2.  Cons:
            
            *   You might not have access to the internet (which is not required, but useful during development), unless your base station has a secondary network adapter (e.g., an ethernet port) and you bridge the connection.  
                
        3.  How to: **short** pins 5 and 6 on the breadboard by using the provided jumper.
            
            ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114128.png?api=v2)
            
            TODO Change the picture with a better one (with proper pin header, not jumper wire)  
            
    2.  **Client (CL) mode**: if you want to have the drone connect to an existing local area network. This is the go-to choice if you have an existing network and admin powers to it in the environment where you are operating.  
        
        1.  Pros: both your base station and your drone can talk with each other (and other devices on the network), and to the internet.  
            
        2.  Cons: requires admin access to a pre-existing network in your space.  
            
        3.  How to: **do not** **short** pins 5 and 6 on the breadboard by using the provided jumper.  
            
            ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114844.png?api=v2)
            
              
            TODO Change the picture with a better one (with proper pin header, not jumper wire)  
            
4.  Insert the initialized SD card inside the SD card slot of the Raspberry Pi.
    
    1.  **Do not** connect the SD card inside the adapter to a USB-A port of the Raspberry Pi.  
          
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114729.png?api=v2)
        
5.  Power the Raspberry Pi
    
    1.  you will see a red and green light turning on on the Raspberry Pi. The green light shows computation usage. You should expect it to become solid green for several minutes.  
        
        1.  Watch a short video of a busy Raspberry Pi booting up for the first time: [https://vimeo.com/728539828/6cbc396872](https://vimeo.com/728539828/6cbc396872)  
            
6.  Wait until the first boot sequence is complete:  
    

*   **If you selected AP mode**
    
    *   Scan available networks through the base station: once the booting procedure is complete you will find a network called `duckietown-<hostname>-ap`, where `<hostname>` is the name of the robot, as determined during the initialization procedure. The default name is `amelia`.  
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220710-110530.png?api=v2)
        
*   Connect to your robot’s access point, e.g., `duckietown-amelia-ap`
    

Unless you have set up an alternative connection and bridged it, you will now lose access to the internet.

*   **If you selected CL mode**  
    
    *   Once the booting procedure is complete the Duckiedrone will automatically connect to the default client network, or any available network previously set up in the `wpa_supplicant.conf` file ([https://ethidsc.atlassian.net/l/cp/Ps0aPzsY](https://ethidsc.atlassian.net/l/cp/Ps0aPzsY) ).  
        
        *   You can add different networks by manually editing the `wpa_supplicant.conf` file in the SD card’s `config` partition. To edit this file, you will need to power off the drone, remove the SD card from the SD card slot of the raspberry pi, use the USB-A adapter to connect it back to the base station, and open the `config` disk partition.
            

Congratulations, you are now ready to connect to your Duckiedrone for the first time! ([https://ethidsc.atlassian.net/l/cp/ApxoZQKu](https://ethidsc.atlassian.net/l/cp/ApxoZQKu))

# Troubleshooting

**Problem**: I disconnected my 5&6 pins but cannot see my robot on the network.

**Solution**: Sometimes things go awry during the first boot. It is possible that the Wi-Fi detection container times out. Search for a `duckietown-hostname-ap` network instead. Reboot the Duckiedrone (with disconnected pins) to have it join the configured existing network.There is only one first time you can connect to your Duckiedrone. Savoir the experience.

#### What you will need:

*   An assembled DD21 ([https://ethidsc.atlassian.net/l/cp/QoKKr1xz](https://ethidsc.atlassian.net/l/cp/QoKKr1xz))
    
*   A `DD21` initialized SD card ([https://ethidsc.atlassian.net/l/cp/VzDw80Fi](https://ethidsc.atlassian.net/l/cp/VzDw80Fi))
    

#### What you will get:

*   A live `DD21`
    

# The first boot: before getting started

The first time a newly flashed SD card is inserted in the Duckiedrone a special “first boot” procedure is executed.

The first boot procedure will take roughly 10-15 minutes, during which your Raspberry Pi might look unresponsive. It is crunching as fast as it can, do not worry.

Do not start this procedure if you do not have the time to finish it!

During this process the Duckiedrone will require a stable power source. Make sure you have a wall outlet power adapter, e.g., a phone charger (5V, 2-3A) or a fully charged Duckiebattery before starting the process. Do not power the Raspberry Pi just yet.

Do not interrupt the first boot procedure, e.g., by removing power to the Raspberry Pi. It will likely corrupt the SD card. A corrupted SD card will have to be flashed again.

# The first boot: getting started

1.  Make sure the Raspberry Pi is **not powered.**  
    
2.  Make sure you have a wall adapter or fully charged battery available.  
    
3.  Networks are typically one of the biggest headaches in robotics. We offer different network configurations to minimize these headaches. If you are not sure which choice to make, the right answer typically is: if you are in a university go for AP mode. If you are at home go for CL mode. In both cases, you need to place the jumper accordingly on your 5&6 pins before getting started.  
    
    1.  **Access point (AP) mode**: if you want to have the drone emit its own Wi-Fi network that your base station can connect to. This is the go-to choice if you do not have a network (WLAN) or admin access to the existing network where you are operating.  
        
        1.  Pros:
            
            *   You can connect to your drone without the need for a pre-existing existing network infrastructure  
                
        2.  Cons:
            
            *   You might not have access to the internet (which is not required, but useful during development), unless your base station has a secondary network adapter (e.g., an ethernet port) and you bridge the connection.  
                
        3.  How to: **short** pins 5 and 6 on the breadboard by using the provided jumper.
            
            ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114128.png?api=v2)
            
            TODO Change the picture with a better one (with proper pin header, not jumper wire)  
            
    2.  **Client (CL) mode**: if you want to have the drone connect to an existing local area network. This is the go-to choice if you have an existing network and admin powers to it in the environment where you are operating.  
        
        1.  Pros: both your base station and your drone can talk with each other (and other devices on the network), and to the internet.  
            
        2.  Cons: requires admin access to a pre-existing network in your space.  
            
        3.  How to: **do not** **short** pins 5 and 6 on the breadboard by using the provided jumper.  
            
            ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114844.png?api=v2)
            
              
            TODO Change the picture with a better one (with proper pin header, not jumper wire)  
            
4.  Insert the initialized SD card inside the SD card slot of the Raspberry Pi.
    
    1.  **Do not** connect the SD card inside the adapter to a USB-A port of the Raspberry Pi.  
          
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220711-114729.png?api=v2)
        
5.  Power the Raspberry Pi
    
    1.  you will see a red and green light turning on on the Raspberry Pi. The green light shows computation usage. You should expect it to become solid green for several minutes.  
        
        1.  Watch a short video of a busy Raspberry Pi booting up for the first time: [https://vimeo.com/728539828/6cbc396872](https://vimeo.com/728539828/6cbc396872)  
            
6.  Wait until the first boot sequence is complete:  
    

*   **If you selected AP mode**
    
    *   Scan available networks through the base station: once the booting procedure is complete you will find a network called `duckietown-<hostname>-ap`, where `<hostname>` is the name of the robot, as determined during the initialization procedure. The default name is `amelia`.  
        
        ![](https://ethidsc.atlassian.net/wiki/download/attachments/2227667008/image-20220710-110530.png?api=v2)
        
*   Connect to your robot’s access point, e.g., `duckietown-amelia-ap`
    

Unless you have set up an alternative connection and bridged it, you will now lose access to the internet.

*   **If you selected CL mode**  
    
    *   Once the booting procedure is complete the Duckiedrone will automatically connect to the default client network, or any available network previously set up in the `wpa_supplicant.conf` file ([https://ethidsc.atlassian.net/l/cp/Ps0aPzsY](https://ethidsc.atlassian.net/l/cp/Ps0aPzsY) ).  
        
        *   You can add different networks by manually editing the `wpa_supplicant.conf` file in the SD card’s `config` partition. To edit this file, you will need to power off the drone, remove the SD card from the SD card slot of the raspberry pi, use the USB-A adapter to connect it back to the base station, and open the `config` disk partition.
            

Congratulations, you are now ready to connect to your Duckiedrone for the first time! ([https://ethidsc.atlassian.net/l/cp/ApxoZQKu](https://ethidsc.atlassian.net/l/cp/ApxoZQKu))

# Troubleshooting

**Problem**: I disconnected my 5&6 pins but cannot see my robot on the network.

**Solution**: Sometimes things go awry during the first boot. It is possible that the Wi-Fi detection container times out. Search for a `duckietown-hostname-ap` network instead. Reboot the Duckiedrone (with disconnected pins) to have it join the configured existing network.