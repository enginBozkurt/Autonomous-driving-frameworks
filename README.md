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

1. Download the sample 3D pointcloud/vector map data.  [link](http://db3.ertl.jp/autoware/sample_data/sample_moriyama_data.tar.gz)

```bash
$ wget http://db3.ertl.jp/autoware/sample_data/sample_moriyama_data.tar.gz
```

2. Download the sample ROSBAG data (LiDAR: VELODYNE HDL-32E, GNSS: JAVAD GPS RTK Delta 3)[link](http://db3.ertl.jp/autoware/sample_data/sample_moriyama_150324.tar.gz)

```bash
$ wget http://db3.ertl.jp/autoware/sample_data/sample_moriyama_150324.tar.gz
```

## Demo run

### Assumptions

- Autoware built from source: the demo data and rosbag have been downloaded into the Downloads folder.
- Autoware run from docker image: the demo data and rosbag have been downloaded into the shared_dir folder within the host. Please go to step 3.

### Steps

1. Please checkout the release version 1.10.0 for this demo.

```bash
$ git checkout tags/1.10.0
```
2. And build it (using catkin) following the steps in [Source-Build](https://github.com/CPFL/Autoware/wiki/Source-Build)
Source the Autoware workspace once the compilation has finished:

```bash
$ source devel/setup.bash
```

3. Create the .autoware directory and extract the demo data inside.

```bash
$ cd ~
$ mkdir .autoware
$ cd .autoware
(from source) $ cp ~/Downloads/sample_moriyama_* .  OR (using docker)  $ cp ~/shared_dir/sample_moriyama_* .
$ tar zxfv sample_moriyama_150324.tar.gz
$ tar zxfv sample_moriyama_data.tar.gz
```

4. Run Autoware

```bash
$ cd ../Autoware/ros
$ ./run
```

5. Go to the Simulation tab of Autoware Runtime Manager (ARM), and load the sample ROSBAG data, which is located in   ~/.autoware .

Show Hidden Files needs to be checked for the .autoware folder to be displayed


![demo_load_rosbag1](https://user-images.githubusercontent.com/30608533/58966851-b661af00-87bb-11e9-9738-5d9b20e3fd3e.png)


6. Set the start time to 140, then click Play and Pause just after it has started playing.

![demo_play_pause_rosbag2](https://user-images.githubusercontent.com/30608533/58966948-e446f380-87bb-11e9-8609-a788cbbf11ab.png)

<p>
7. Launch RViz through the RViz button in the bottom-right corner of the ARM and load the default.rviz config provided with Autoware. To do this got to File -> Open Config and navigate to Autoware/ros/src/.config/rviz/default.rviz. Show Hidden Files needs to be checked inside Autoware/ros/src/ for the .config folder to be displayed.
</p>


![demo_load_rviz3](https://user-images.githubusercontent.com/30608533/58966998-fc1e7780-87bb-11e9-9e5d-2949d6e9afdd.png)

<p>
8. Go to the Quick Start tab of ARM, and load the preinstalled roslaunch scripts one by one. The scripts are located in Autoware/docs/quick_start. The scripts need to be enabled by clicking on the left button as shown in the image for the Map.
</p>

![demo_load_map4](https://user-images.githubusercontent.com/30608533/58966833-acd84700-87bb-11e9-8a74-2ac5e46380b6.png)


Un-pausing the simulation after starting the Map will show the pointcloud map in Rviz.

![demo_map_shown5](https://user-images.githubusercontent.com/30608533/58967045-13f5fb80-87bc-11e9-9468-2bbdacdbcd03.png)

# Uber AVS
![Introducing_AVS_Banner-1-696x522](https://user-images.githubusercontent.com/30608533/58969336-3853d700-87c0-11e9-928c-6381d993854f.png)


## XVIZ sample Dataset

The data provided in this repo is being processed into XVIZ. The original data is available at the following URLs:

- [Kitti](http://www.cvlibs.net/datasets/kitti/raw_data.php)


- [nuTonomy](https://www.nuscenes.org/login)

### How to convert

- *kitti*

```bash
yarn start 
-d <your_path_to_source_data>/kitti/2011_09_26/2011_09_26_drive_0005_sync 
-o <your_path_to_xviz-data>/kitti/2011_09_26_drive_0005_sync
--fake-streams=true
--disable-streams=image_00, image_01
```
    - Available image streams are image_00, image_01, image_02, image_03
    - Default --image-max-width is 400, --image-max-height is 300 (actual conversion will preserve aspect ratio)



- *nuTonomy*

```bash
yarn start 
-d <your_path_to_source_data>/streetscape.gl/data/nutonomy/nuscenes_teaser_meta_v1/v0.1
-o <your_path_to_xviz-data>/nutonomy --samples-directory=~/dev/streetscape.gl/data/nutonomy/samples 
--scenes=6
```


  - -d/--data-directory is metadata and annotations
  - --samples-directory is lidar, radar and images
  - --scenes also supports multiple numbers, --scenes=1,2,6
  - Default --image-max-width is 400, --image-max-height is 250 (actual conversion will preserve aspect ratio)
