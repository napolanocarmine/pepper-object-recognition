# Pepper with ROS

## GROUP 6

- 622701164 - CAVALLARO VIRGINIA
- 622701163 - COPPOLA DAVIDE
- 622701202 - NAPOLANO CARMINE 
- 622701106 - PANDOLFI GIULIANO

# How to use our application

## Workspace Setup

```bash
cd group6_ws/src
ln -s ../group6_git/pepper_robot .
ln -s ../group6_git/naoqi_bridge .
ln -s ../group6_git/naoqi_bridge_msgs .
cd ..
catkin build
echo "export PYTHONPATH=\${PYTHONPATH}:$D/lib/python2.7/site-packages" >> devel/setup.bash
echo "export DYLD_LIBRARY_PATH=\${DYLD_LIBRARY_PATH}:$D/lib" >> devel/setup.bash # configure where to find naoqi sdk
source devel/setup.bash
```

## Pepper bring up

You can execute these commands for Pepper bring up.
nao_ip parameter depends on which Pepper you use for testing.
In our case, the IP address is 10.0.1.230

```bash
cd group6_ws
roslaunch pepper_bringup pepper_full_py.launch nao_ip:=XX.X.X.XXX
```

## Execute custom nodes

In a new terminal window, after you must be placed in the workspace directory, you have to execute the following commands, :

```bash
source devel/setup.bash
cd src
cd launch
roslaunch launcher.launch
```

In this way, you have executed only the detector and pepper_voice nodes.
To be able to move the Pepper's head you need to execute the others commands.
In a new terminal window, you must be placed in the workspace directory:

```bash
source devel/setup.bash
cd src/pepper_voice/
python pepper_head.py # to perfome a complete movement, from right to left
```

You can substitute the last line of the previous commands group with:

```bash
python pepper_head.py --position=right 	# to move Pepper's head to the right.
python pepper_head.py --position=center 	# to move Pepper's head to the center.
python pepper_head.py --position=left 		# to move Pepper's head to the left.
```







