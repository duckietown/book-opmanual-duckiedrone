# Introduction
The software architecture is designed to be modular and so that the code is extensible, or it is easy to replace each component when a better or different one when desired. The sensors are interfaced into ROS nodes which publish the data for the state estimator to combine into and estimate of the state of the drone. Based on this estimate, the controller (ours is a PID) is used to move the drone to a desired velocity or position based on the inputs from the web interface or a higher level behavioral engine. The mode controller ensures that the desired mode changes (such as ‘Armed’ to ‘Flying’) are legal, and will stop the flight if any safety checks failed (for example, the web interface heartbeat stops).

## 1.1. Diagram of the Software Architecture
This is the general layout of the software architecture. Take a look at the key to better understand its meaning.

```{figure} ../_images/software-architecture/software-architecture-diagram.png
:name: flowchart showing the messages connecting each ros node on a DuckieDrone
:width: 600
:align: center
```