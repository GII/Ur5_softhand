Installation
============

Follow these steps to install the "UR5-Softhand" project:

1. Clone the repository:

   ```bash
   git clone https://github.com/GII/Ur5_softhand.git
   cd Ur5_softhand
   ```

2. Install dependencies:

   ```bash
   sudo apt update && sudo apt install -y ros-humble-desktop python3-pip
   pip3 install -r requirements.txt
   ```

3. Setup your ROS 2 workspace:

   ```bash
   mkdir -p ~/ur5_softhand_ws/src
   cd ~/ur5_softhand_ws/src
   ln -s ~/Ur5_softhand .
   cd ~/ur5_softhand_ws
   colcon build
   source install/setup.bash
   ```
