# line_follower_pkg_ros
---_Made by: Suyash Verma (MrCrazyUnknown)_
## line_follower package for ROS (with a test arena)

This package holds a 'Line following Robot'.

---
### Features:

- It has a fully functional Robot.

- It also an already prepared _Arena_ (for testing and tuning purposes)

- The _Line Following Bot_ stays on the path(line) using **PID Control algorithm**.

- The Main control node _"Movement.py"_ controls the bot by finding the path and processing it to find the appropriate response to stay on the path(line) using dynamic recongiruation (rqt)

- It has a node for viewing the input received by the Bot's camera.

- It also has a node for controlling the bot manually using _Keyboard_teleop_twist_. [More Info on that here](https://github.com/MrCrazyUnknown/keyboard_teleop_twist "Keyboard_twist_teleop")

- It also has a node for viewing the **image processing** involved for finding the error factor in the PID algorithm.

- It also has a node for controlling the bot using PID control and cv2(trackbars) (but not very precise).

---

### Usage:

- First install the package:
    ```linux shell
    cd <workspace>/src
    git clone https://github.com/MrCrazyUnknown/line_follower_pkg_ros
    cd ..
    catkin build line_follower
    ```
    
- Next, use it:
    ```linux shell
    roslaunch line_follower arena.launch
    ```
    In a new terminal tab:
    ```linux shell
    rosrun rqt_reconfigure rqt_reconfigure
    ```
    In another new terminal tab:
    ```linux shell
    rosrun line_follower Movement.py
    ```
    Now, refresh the 'dynamic reconfiguration' window.
    
    Select the 'Movement' option.
    
    Control the different the parameters on the window.
    
        (KP, KI, KD are PID parameters).
        (SP is the forward speed).
        (ROI_W, ROI_H are the parameters to control the dimensions of the Region of Interest).
        (ROI_Y is the parameter for controlling the positioning of Region of Interest).
    
- Alternate Usages (Only launch the world using `roslaunch line_follower arena.launch`):

    Using the keyboard_teleop (No need to install the teleop pkg):
    ```linux shell
    rosrun line_follower teleop.py
    ```
    
    Viewing the camera input:
    ```linux shell
    rosrun line_follower CamRcv.py
    ```
    
    Viewing the Image_Processing involved:
    ```linux shell
    rosrun line_follower threshold.py
    ```
    
    Controlling the bot using cv2(trackbars):
    ```linux shell
    rosrun line_follower AutoMove.py
    ```
    
---
