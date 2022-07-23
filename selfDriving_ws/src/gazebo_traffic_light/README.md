To make the code run smoothly, you need to include the "cfg", "models", "src", "yaml" folder.

In CMakeLists.txt, you need to do some changes based on the CMakeLists.txt. 

To use the traffic light in the gazebo environment, you need to include the below code in the .world file. You can refer to plugin_test.world in the "worlds" folder as an example.

    <model name="test_included_traffic_light">
      <plugin name="traffic_light_plugin" filename="libgazebo_traffic_light.so" />
      <include>
        <uri>model://gazebo_traffic_light</uri>
        <static>false</static>
        <pose>0 0 0 0 0 0</pose>
      </include>
    </model>

To run the example code:
catkin_make
source devel/setup.bash
roslaunch gazebo_traffic_light traffic_light_test.launch