Configuration
=============

1. **Camera Setup**:
   - Mount the Intel RealSense L515 camera two meters above the work surface.
   - Publish a static transformation between the `world` frame and `camera_link`:

     ```bash
     ros2 run tf2_ros static_transform_publisher -0.17 1 2.06 0 1.57 0 world camera_link
     ```

2. **Robot Controller Configuration**:
   - Verify the UR5e controller settings in `config/ur5e_controllers.yaml`.
   - Check the qbHand2M controller settings in `config/qbhand_controllers.yaml`.

3. **MoveIt Configuration**:
   - Update the planning groups in `moveit_config/ur5_softhand.srdf`.
   - Set the `Home` position for the robot in `motion_planning_python/config/waypoints.yaml`.
