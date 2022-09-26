Drone Smart Farm
1. Team Members
Lin Zhang
June (Junxian) Chen


2. INTRODUCTION (OBJECTIVE)
Since the Industrial Revolution, automated systems have continued to change people's lives. More and more intelligent machines are designed and aimed to replace human labor. Intelligent machines can provide longer working hours, more efficient outputs, and long-term stable profits. In some food factories, or Tesla's unmanned factories. Machines can work 24 hours a day and 7 days a week automatically. As the automation system continues to spread, we want to bring a new model to the farm. We have found that using drones to guard farms can save a lot of the workforce. First, for a large farm, how to monitor and prevent animals from eating crops is a big problem. It is difficult for workers who patrol the entire farm at different times of the day. Then, the farm may consider using some cameras to monitor the entire farm, but the problem is that the camera cannot move. When the problem is found and the workers rush over, the crops may have been cracked already. Therefore, is there a better way to avoid animals eating crops? Yes, we are proposing this smart farm project that relies on drones. The drone can provide a wider field of view and monitor the entire farm in a relatively short period of time. Farmers only need to stipulate a fixed route and the start time, then the drone can monitor the entire farm every day automatically and frequently. When some animals are found, the drone will generate a report in sync and send a notification to the user's phone. We also allow drones to get close to the animals and then try to chase the animal away through the sound. The use case of drones is not limited to the above scenario, and we think this is a good example. Drone Smart farms have a huge demand in market prospects.


3. TOOLS 
a) Olymp: Olympe is an SDK that provides a Python controller programming interface for Parrot ANAFI drones. It can be used to connect to and control a drone from a remote Python script running on a Linux based computer.

b) Sphinx: Sphinx is a drone simulation tool.
    Visualize and record flight data at run-time.
    Configure drone sensors and surrounding physics elements at run-time.
    Simulate all sensors, including cameras.
    Generate depth maps and segmentation images.
    Use many realistic 3D scenes .
    Connect to different kind of remote controllers via Wi-Fi.
    Use scripts to control the simulation entirely.
    Add pedestrians and vehicles.
    
c) OpenCV: Open Source Computer Vision Library.

4. INSTALLATION GUIDE
Please refer to the official documentation for installing all tools above.
In a shell enter the following commands:
$ sudo systemctl start firmwared.service
$ sphinx "/opt/parrot-sphinx/usr/share/sphinx/drones/anafi_ai.drone"::firmware="ftp://<login>:<pass>@ftp2.parrot.biz/versions/anafi2/pc/%23latest/images/anafi2-pc.ext2.zip"
To be updated….


5. SYSTEM OVERVIEW (DETAILS)

a) Basic actions
Set-up a local environment and configure the drone connection. 

b) Schedule route
Using a program to control the drone. Which includes take-off, landing, and flying drones in different directions, e.g.,  custom routes (through terminals). 
Custom routes require user inputs. 
A predetermined route, and run daily. This feature allows users to enter.
Absolute GPS coordinates.
Relative coordinates based on the starting position.

c) Run-time video
Send the video back to the terminal. 
A popup window will be created and sync the drone camera. 
Decode real-time video (H.256 decode).

d) ML object detection
classification.
ML for animal detection, we may use some pre-trained ML model. 
Attach our ML model to the real-time video.
Use a rectangle to circle the target object.

e) Following (we propose 2 approaches)
Rectangle approach
One trade-off solution is using the ML object detection and camera to calculate the drone directions. when an object is detected, there will be a rectangle on the screen for each frame (30 frames per second). We can calculate the size and position of the rectangle for each frame. Then we will know whether the drone needs to move forward, or backward based on the size of the rectangle. Up, down, left, and right based on the position of the rectangle. in this case, we find a way to transfer a 2d object into 6 directions. 
Add more sensors (like Laser)
Potentially use a reinforcement method for getting close to the animal. We can calculate the distance between the drone and the animal by sending an infrared sensor to the ground. Then rewarding the drone if the drone movements move closer to the animal and conversely.

f) Back to the route (restore after following)
Store the position before following the object. This position may be in the middle of the path. 

g) Generate report
Generate a log file that explains what object was detected, the position, time, and screenshot…. 


6. MILESTONES (TIMETABLE)
 
Milestone 1
Set up environment
Set up ML and get ideas on what to gather in the farm 
09/26 - 10/02 (1 week)

Milestone 2
Basic actions
gather data from the farm
10/03 - 10/09 (1 week)

Milestone 3
Schedule route
Train/Test the model
10/10 - 10/16 (1 week)

Milestone 4
Run-time video
ML object detection
Alongside with potentially doing reinforcement learning
10/17 - 10/30 (2 weeks)

Milestone 5
Following approach 1
Following approach 2
10/31 - 11/20 (3 weeks)

Milestone 6
Generate report
Generate report
11/21- 11/25 (1 week)


7. POTENTIAL PROBLEMS 
a) Detecting the crops while flying in the sky. If the crop takes a few pixels, it will be difficult to see if the animal is eating the crop. The machine learning model may not accurate because there might not be enough data due to improper data. Using images, the majority of the pixels will be the background. 
b) Camera adjustment. Keep turning around the camera while flying? Or the camera focuses in one direction.
c) How to avoid obstacles. We may need some sensors for avoiding obstacles,
d) Object following. The object following task is more like following a 2d picture object in the 3d world.  (Translate 2d camera image into drone directions).
e) Multiple objects are detected on one screen, which to follow.


8. CONCLUSION
We will provide a program that can be run in the terminal, this program can start the drone and plan a route. This route can be a collection of some GPS coordinates or some relative displacements related to the starting position. Then the drone will start its task, the drone will send back a real-time video (based on the camera), and users can easily catch up where the drone is and what the drone is looking at.  
 	We will also try to produce an accurate animal and crop drone detection. It is unnecessary for the drone to interact with the animal if the animal is not eating. Once the drone detects an animal eating a crop, the drone would develop a scheduled route to push the animal away. When the drone is next to the animal, the drone will bump the animal in the opposite direction of the crop. Once the animal stops, the drone will wait a bit to see if the animal tries to eat the crop again before flying back to the home station or the sky.
