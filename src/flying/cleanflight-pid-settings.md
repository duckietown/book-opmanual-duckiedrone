(cleanflight-pid-settings)=
# Flight Controller PID Tuning

```{needget}

* A fully operational `DD21`

---

* A `DD21` that flies stably and responsively in manual mode

```

For a consumer level drone, when you launch it for the first time (e.g. with virtual joysticks on phones, or with remote controls), you would expect it to take off and fly more or less stably, instead of shaking and going out of control.
This is indeed what a Duckiedrone is capable of doing, too.
In this section, we will have a look at the parameters on the flight controller that make it happen.
And you will be able to play with them!

## Expectation with good parameter settings

The Flight Controller (FC) runs high-frequency control loops to stabilize the drone. It utilizes the sensors (e.g. IMU & Gyro) to estimate the state of the drone. In the **Angle Mode** that we configure the FC to, the following is expected:
* On the roll / pitch axis:
  * when commands are issued, the FC tries to make the drone reach the commanded roll/pitch as soon as possible, and minimize the fluctuation and stay at the designated angle.
  * When no commands are given, the drone would try to return to a neutral roll and pitch.
* On the yaw axis:
  * When commands are issued, the FC tries to keep the yaw rate to the command.
  * When no commands given, the drone should not rotate along the vertical axis.

## PID terms in drones and tuning

Primarily, a **proportional–integral–derivative controller** ([PID controller](https://en.wikipedia.org/wiki/PID_controller)) is used on the FC to achieve these. Here are some materials helping explain the influence of `P`, `I` and `D` terms, in the context of drones, and how should they be tuned based on the behaviors of the drone.

* [FPV Drone PID Explaned by Oscar Liang](https://oscarliang.com/pid/)
* [CleanFlight PID Tuning on OpenTXU by John Case](http://open-txu.org/home/special-interests/multirotor/cleanflight-pid-tuning/)
* [A video on recognition of PID problems.](https://www.youtube.com/watch?v=YNzqTGEl2xQ) It is not necessary to use the string method to tune a Duckiedrone, but the behaviors are also clearly presented in that part, when certain parameters are far from good values.

## Setting your PID values


### How to update in CleanFlight
```{figure} ../_images/fc-pid-setting/FC_PID_starter.png
:width: 100%
:name: fig-fc-pid-setting-fc-pid-starter

GUI tab in CleanFlight to set the PID values (with recommended starter values)
```

As shown in {numref}`fig-fc-pid-setting-fc-pid-starter`, here is how to set the PID values:
1. Connect the FC to the workstation.
1. Go to the “PID Tuning” tab.
1. Change the values and click "Save" on the bottom right of the tab

### Recommended starting values

| Axis  | P   | I   | D   | RC Rate | Super Rate  | Max Vel |
| ---   | --- | --- | --- | ---     | ---         | ---     |
| Roll  | 80  | 60  | 75  | 1.00    | 0.00        | 200     |
| Pitch | 80  | 60  | 75  |         | 0.00        | 200     |
| Yaw   | 70  | 45  |     | 1.00    | 0.70        | 667     |

In addition, change the Angle Limit to 55.

Finally, click “Save”.

### Your tuning loop

```{note}
In your own PID tuning process, you should only change the `P`, `I` and `D` on ROLL, PITCH and `P` and `I` on YAW. Only change the other values if you are sure what they mean and what you are doing.
```

After apply the recommended starter values, with the knowledge from the previous subsection, you can keep trying the following for improving the basic manual performance of your Duckiedrone: 
* Flying the drone manually and look out for erroneous behaviors
* Connect the FC to CleanFlight, and adapt the PID values