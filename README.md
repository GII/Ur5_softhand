
# UR5e - Softhand (qbrobotics) Integration 

[![ROS 2 Jazzy](https://img.shields.io/badge/ROS%202-Jazzy-blue)](https://docs.ros.org/en/jazzy/index.html)
[![ROS 2 Humble](https://img.shields.io/badge/ROS%202-Humble-green)](https://docs.ros.org/en/humble/index.html)

This project integrates a **UR5e robotic arm** with a **qbHand2M (SoftHand)** using **MoveIt** for advanced motion planning and manipulation tasks. The setup combines state-of-the-art robotic control with a soft robotic hand, enabling precise pick-and-place operations and other complex manipulations.

The project is designed for:
- **Industrial automation**: For tasks requiring adaptive grippers.
- **Human-robot interaction**: Leveraging the soft-hand capabilities.
- **Robotic research**: Providing a flexible platform for algorithm testing and development.
- **Education**: A hands-on tool for students and educators in robotics.

It is implemented using **ROS 2** for seamless integration with modern robotic ecosystems. Features include:
- **Joint state merging**
- **Custom motion planning configurations**
- **Scalable deployment**

---

## Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/GII/Ur5_softhand.git
cd ur5e-softhand-integration
rosdep install --from-paths src --ignore-src -r -y
colcon build
source install/setup.bash
```
## Usage
The following commands and actions must be performed in **order** 

 1. Start-up the UR5e using the pedant and connect the softhand to the power outlet, check the blue light is powered in the hand connection.
 2. Start the softhand controller using 
   ```bash
    ros2 launch qb_hand_description bringup_qbhand2m.launch standalone:=true activate_on_initialization:=true
   ```
  
 3. Start the UR5e controller using
```bash
ros2 launch my_robot_cell_control start_robot.launch.py
```
4. Start moveit
```bash
ros2 launch ur_softhand_moveit_config start.launch.py
```
5. Run URCaps from UR5e pedant ```Control by laboratorio``` script
