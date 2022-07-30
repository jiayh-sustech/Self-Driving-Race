# AD Race Map
Instruction on how to launch gazebo simulation with the autonomous driving race map.

## The gazebo world and model
* Map model: in ```<workspace path>/src/ad_race_map``` folder. 
* Gazebo world: in ```<workspace path>/src/limo/limo_gazebo_sim/worlds```.

## Prerequisite
* First you should follow the instruction in the README.md file.

## Getting Start
* Put the ```ad_race_map``` in ```~/.gazebo/models```.
* Source the workspace.
* Run the launch file ```roslaunch limo_gazebo_sim limo_ackerman_ad_map.launch```.

