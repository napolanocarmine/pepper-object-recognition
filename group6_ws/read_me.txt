GROUP 6

622701164 - CAVALLARO VIRGINIA
622701163 - COPPOLA DAVIDE
622701202 - NAPOLANO CARMINE 
622701106 - PANDOLFI GIULIANO

-------------------------------------------------------------------------------------------

# Workspace setup:

cd group6_ws/src
ln -s ../group6_git/pepper_robot .
ln -s ../group6_git/naoqi_bridge .
ln -s ../group6_git/naoqi_bridge_msgs .
cd ..
catkin build
echo "export PYTHONPATH=\${PYTHONPATH}:$D/lib/python2.7/site-packages" >> devel/setup.bash
echo "export DYLD_LIBRARY_PATH=\${DYLD_LIBRARY_PATH}:$D/lib" >> devel/setup.bash # configure where to find naoqi sdk
source devel/setup.bash

-------------------------------------------------------------------------------------------

Move to group6_ws folder.
>> roslaunch pepper_bringup pepper_full_py.launch nao_ip:=XX.X.X.XXX

Move to /src/detector/src/
>> python3 detector_node.py 

Wait till the detector_node is loaded.

Move to /src/pepper_voice/
>> python pepper_voice_node.py

Move to /src/pepper_head/
>> python pepper_head.py 						# to perform a movement from right to left.
>> python pepper_head.py --position = right 	# to move Pepper's head to the right.
>> python pepper_head.py --position = center 	# to move Pepper's head to the center.
>> python pepper_head.py --position = left 		# to move Pepper's head to the left.

