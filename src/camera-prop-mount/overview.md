(overview_camera_prop_mount)=
# Overview


In this section of the build, you will attach the camera, and finalize the drone assembly.

```{admonition} What you'll need
Part : Quantity
Raspberry Pi Camera : 1
Pi Mount : 1
Pi Mount Screws : 3
Plastic Standoffs : 2
CW Propellers : 2
CCW Propellers : 2
8mm Wrench : 1
Zip Ties : 10+
Double sided tape : 1

```

## Hardware overview

### Camera

The camera is used to measure the planar position and velocity of the drone; by planar, we mean that the camera provides position and velocities in the x and y-axis but not z (left and right, forward and back, but not up and down). The planar velocity of the drone is found using optical flow, which is a technique that computes the change in position between two “features” over time. A feature is a distinct group of pixels in an image. The position of the drone is found by computing the change in position between two subsequent camera frames. The drone is also able to localize the drone in a known map. This means that if you upload to the drone a photo of the surface that the drone will be flying over, the drone will be able to know where it is within this photo, or “map.” Finally, the drone is able to Simultaneously Localize And Map (SLAM) which means that it can build its own map of what it is flying over, and then localize within the map that it creates. SLAM is used on all robot vacuums that clean your house for you. Without knowing what your house looks like, the robot bumps around and remembers where it's been, creating a map.
For more information about the camera, watch [these lectures](https://edge.edx.org/courses/course-v1:Brown+CSCI1951-R+2020_summer/courseware/0e3596880ec446d8ab63df427e02e9c4/ccd9eede2624475b91ce4b55ee51ce87/?activate_block_id=block-v1%3ABrown%2BCSCI1951-R%2B2020_summer%2Btype%40sequential%2Bblock%40ccd9eede2624475b91ce4b55ee51ce87) (you will need to create a free EdX account to view the material)

```{figure} ../_images/components-official/camera.png

Raspberry Pi Camera
```

### Propellers
The propellers are what provide lift for the drone and allow it to fly. When the propeller spins, it creates a pressure difference between the air above and below it. The pressure below the propeller is greater than the pressure above, generating lift. Another way to think about how a drone prop works is that it pushes air down and the opposite reaction is the thrust lifting the drone up.
The drone propeller is specified by three numbers. The propellers on your drone are 5 x 4 x 3. The first number, 5, is the size, and it indicates the length of the blades; measured from the center to the tip. The second number, 4, is the pitch, and it is a theoretical measurement of how far the propeller would travel through the air in one revolution. A larger pitch means more air is moved, so the propeller travels further, while a smaller pitch would move less air and therefore move less. The last number, 3, is the number of blades.

```{figure} ../_images/components-official/propellers.png

Propellers
```

## [TODO]
Add:

*   Long white standoffs
*   M2 screws
*   Zip ties
*   M3 screw (for TOF sensor)
*   small metal screws and nuts 