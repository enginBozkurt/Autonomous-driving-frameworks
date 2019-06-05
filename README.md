# Autonomous-driving-frameworks
Autonomous driving visualization and test frameworks


<p>

This general overview and comparison repo includes a comparison of the two Autonomous Driving visualization test framework :
1.  Autoware (ROS - Rviz)
2.  Uber AVS  (XVIZ and  streetscape.gl) 

</p>


# Autoware
<p>
Autoware.AI is the world's first "All-in-One" open-source software for autonomous driving technology. 
It is based on ROS 1 and available under Apache 2.0 license. It contains the following modules:


- Localization is achieved by 3D maps and SLAM algorithms in combination with GNSS and IMU sensors. 

- Detection uses cameras and LiDARs with sensor fusion algorithms and deep neural networks.

- Prediction and Planning are based on probabilistic robotics and rule-based systems, partly using deep neural networks as well. 

- The output of Autoware to the vehicle is a twist of velocity and angular velocity. This is a part of Control, though the major part of Control stack commonly reside in the by-wire controller of the vehicle.

</p>


<p>

The capabilities of Autoware are primarily well-suited for urban cities, but highways, freeways, 
and geofenced areas can be also covered.  It provides  a ROSBAG-based simulation environment.


</p>


<p>
In addition, the framework supports the following  Cloud Services:
</p>

## Autoware Online
<p>

You may test Autoware at Autoware Online. No need to install the Autoware repository to your local environment.
</p>

## Automan
<p>

You may annotate and train your ROSBAG data using your web browser through Automan. 
The trained models can be used for deep neural network algorithms in Autoware, such as SSD and Yolo.
</p>


## ROSBAG STORE
<p>

You may download a number of test and simulation data sets from Tier IV's ROSBAG STORE.
Note that free accounts would not allow you to access image data due to privacy matters.

</p>

## Map Tools
<p>

You may create 3D map data through Tier IV's Map Tools. 
The 3D map data used in Autoware are composed of point cloud structure data and vector feature data.

</p>

## Useful Plugins -  MapToolbox

<p>
This a unity plugin helps user create vector maps for Autoware efficiently.
https://github.com/autocore-ai/MapToolbox
</p>

# ROSBAG Demo in Autoware

## Demo data
<p>
This demo will need the given 3D map and ROSBAG sample data. Please download the following sample data before running the demo.
</p>

1. Download the sample 3D pointcloud/vector map data.[link](http://db3.ertl.jp/autoware/sample_data/sample_moriyama_data.tar.gz)

```bash
$ wget http://db3.ertl.jp/autoware/sample_data/sample_moriyama_data.tar.gz
```
