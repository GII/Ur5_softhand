.. UR5-Softhand documentation master file, created by
   sphinx-quickstart on Mon Jan 27 2025.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

UR5-Softhand Project
=====================

This documentation provides an overview of the "UR5-Softhand" project, covering its objectives, implementation, and usage. It is designed to guide developers, researchers, and engineers through the setup, functionality, and customization of the project.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   introduction
   requirements
   installation
   configuration
   usage
   contributing
   license

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

---

Introduction
============

The "UR5-Softhand" project integrates advanced robotic systems for performing precise pick-and-place tasks. The primary components of the system include:

- A UR5e robotic arm.
- The qbHand2M robotic hand.
- ROS 2 Humble as the middleware.
- MoveIt 2 for motion planning.
- An Intel RealSense L515 camera for object detection.

This system is designed for applications in automated object manipulation, offering a modular and extendable framework for various tasks.

---

System Requirements
===================

To run this project, ensure that your environment meets the following requirements:

- **Operating System**: Ubuntu 22.04 LTS (Jammy Jellyfish).
- **ROS 2 Version**: Humble Hawksbill.
- **Dependencies**:
  - Python 3.10+
  - MoveIt 2.0
  - Intel RealSense SDK
  - Docker (optional, for containerized deployment)
- **Hardware**:
  - UR5e robotic arm.
  - qbHand2M robotic hand.
  - Intel RealSense L515 camera.
  - A high-performance computer with GPU support (optional).

---

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

4. (Optional) Install the Docker image:

   ```bash
   docker pull username/ur5-softhand:latest
   ```

---

Configuration
=============

1. **Camera Setup**:
   - Mount the Intel RealSense L515 camera two meters above the work surface.
   - Publish a static transformation between the `world` frame and `camera_link` using the following command:

     ```bash
     ros2 run tf2_ros static_transform_publisher -0.17 1 2.06 0 1.57 0 world camera_link
     ```

2. **Robot Controller Configuration**:
   - Verify the UR5e controller settings in `config/ur5e_controllers.yaml`.
   - Check the qbHand2M controller settings in `config/qbhand_controllers.yaml`.

3. **MoveIt Configuration**:
   - Update the planning groups in `moveit_config/ur5_softhand.srdf`.
   - Set the `Home` position for the robot in `motion_planning_python/config/waypoints.yaml`.

---

Usage
=====

1. **Launching the System**:
   - To launch the UR5e and qbHand2M:

     ```bash
     ros2 launch ur5-softhand bringup.launch.py
     ```

2. **Performing Pick-and-Place**:
   - Define the target positions in the `waypoints.yaml` file.
   - Run the motion planning script:

     ```bash
     python3 scripts/motion_planning.py
     ```

3. **Testing the System**:
   - Use MoveIt to manually control the robot and test its functionality.

---

Contributing
============

Contributions to this project are welcome! Please follow these steps to contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix:

   ```bash
   git checkout -b feature-name
   ```

3. Commit your changes and push the branch:

   ```bash
   git commit -m "Description of changes"
   git push origin feature-name
   ```

4. Submit a pull request.

---

License
=======

This project is licensed under the MIT License. See the `LICENSE` file for details.

