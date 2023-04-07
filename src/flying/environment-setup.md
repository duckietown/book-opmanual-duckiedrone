(environment_setup)=
# Environment setup

## Stopping the standard containers

To setup the development environment you need to bring
down all docker containers and then setup a special development container.

To do so:

1.  Bring down all the containers by going to `http://<hostname>.local:9000/#/containers` in your browser and stopping each container. 
    
    ```{note}
    The only exception would be the `wifi-access-point` container. Keep it running if you want to be able to connect to the Duckiedrone own access point.
    ```

1.  Reboot, and run 
    
    ```bash
    docker update --restart=no <CONTAINER_NAME_1> <CONTAINER_NAME_2> <...>
    ```
    
    for all containers that you had stopped and automatically restarts.



1.  Reboot again. When you are done, `docker ps -a` should show no containers running.

## Development container setup

To make it possible for you to develop your own code on the drone, you need to set up a docker workspace from the source code of the repository `pidrone_pkg`.

1.  Run `ssh duckie@yourdrone` from your base station to ssh into your drone.  The password is
`quackquack`.

1. From the `duckie` user home directory, install the needed dependencies by running:

    ```
    sudo apt install rake git -y
    ```

1. Then clone the repository to your Duckiedrone's SD card and switch to the branch `ente`:

    ```shell
    mkdir -p catkin_ws/src
    cd catkin_ws/src
    git clone https://github.com/h2r/pidrone_pkg
    cd pidrone_pkg
    git checkout ente
    ```

1.  Finally build the Docker image needed to run the software (which is back on an older version of ROS, ROS Kinetic).

    ```
    rake build && rake create
    ```

    ```{note}
    The next step will take a long time because it has to download all the dependencies to build the image.  Make sure your Raspberry Pi is plugged into an external USB power supply.
    ```

1.  Before using this container, you will want to bring down all the other containers. We recommend doing this from the Portainer page (accessible at `<hostname>:9000`), stopping all the running containers.

    ```{note}
    You will need to do this each time you reboot the drone.
    ```
    ```{warning}
    If you are running the access point (**AP**) configuration by shorting the pins on the Raspberry Pi Hat, **do not** stop the container `dt-wifi-access-point`.
    
    Doing so will make the AP stop and you will lose your connection, requiring to reboot.
    ```

1.  You also need to download the `raspicam_node` package to be installed later:

    ```shell
    cd ~/catkin_ws/src/
    git clone https://github.com/UbiquityRobotics/raspicam_node 
    ```

1.  You can start the container and go inside it by running, from the `pidrone_pkg` directory:

    ```shell
    rake start
    ```

1.  Once in the container, you need to install the `pidrone_pkg` and `raspicam_node` ROS packages. To do this execute:

    ```shell
    cd ~/catkin_ws
    catkin_make && catkin_make install
    ```

1.  Now that all the packages are installed, to access the workspace you will use to control the drone, run:
    ```shell
    screen -c pi.screenrc
    ```

This will start a screen session with each of the ROS nodes needed to
run the drone and make it fly. 

```{note}
Anytime you'll want to interact with the drone software you will first need to start the container by running `rake start` from the `~/catkin_ws/src/pidrone_pkg` directory and then, inside the container, running `screen -c pi.screenrc`.
``` 
