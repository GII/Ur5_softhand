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
