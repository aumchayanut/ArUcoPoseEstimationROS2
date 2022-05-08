# ArUcoPoseEstimationROS2
First change models/box(cylinder)/meshes/model.mtl    
/home/aum/aruco_ws/src/aruco/models/box/materials/textures/texture.png    
to your texture.png path    
    
going to your workspace
```
colcon build
```
Then sorce your workspace
```
~/yourworkspace/install/setup.bash
```
then launch gazebo and rviz by use this command
```
ros2 launch aruco launch.py
```
You will have 
1. gazebo and rviz with differential drive robot with camera
2. Box and Cylinder with ArUco mark in gazebo
like this
![ArUcoPoseEstimationROS2](GazeboExample.png)
    
Then source workspace in another terminal and run pose estimation node by run sub_cam.py
```
ros2 run aruco sub_cam.py
```
You will have camera frame window like this
![ArUcoPoseEstimationROS2](OpenCameraExample.png)
 You will have marker info from terminal that consists of Id, TranslationVector(XYZ), EulerAngle(RPY), RotationMatrix and Quaternion of objects in camera frame.
 These store in Dictionary name "Marker" variable
 Camera frame are X right Y Down Z Out of the camera

Custom msg structure can see in /msg/Custom.msg the messages consist of
1. ID: uint16 array size 1*n [1,2]
2. Translation Vector: float array size 1*3n [x1,y1,z1,x2,y2,z2]
3. Euler Angle: float array size 1*3n [r1,p1,y1,r2,p2,y2]
4. Quaternion: float array size 1*4n [qx1,qy1,qz1,qw1,qx2,qx3,qx4]
while n is number of markers found.

Custom message publish in to topic "/HouseM8/Aruco"
