# bno055_dockered_test

Expected software: Linux 22.04, Docker 20.10.17
Expected hardware: Adafruit BNO055 and CP2104 USB-to-UART Bridge (see https://github.com/flynneva/bno055 for hardware wiring)

Setup instructions

0. Wire your BNO055 to your CP2104 Bridge. Plug the bridge into your computer.
1. Clone this repo and cd into it
2. Copy ros2.rules to /etc/udev/rules.d/ and run $sudo udevadm control --reload-rules && sudo service udev restart && sudo udevadm trigger.
3. cd to /dev and run $ls, you should see a device named IMU_UART_bridge.
4. cd back to the repository. Within the repo, cd into docker, and run $docker compose up -d. Then run $docker exec -it bno055_test bash to enter into the container.
5. Within the container cd to /ros2_ws and run $colcon build; source install/setup.bash; 
6. Run the bno055 node with $ros2 run bno055 bno055 --ros-args --params-file ./src/bno055/bno055/params/bno055_params.yaml.
7. Open up another terminal and enter into the same container. Run $source /opt/ros/galactic/setup.bash, then run $ros2 topic echo /bno055/imu. You should see a stream of IMU messages print continously to the screen.
