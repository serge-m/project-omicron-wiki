# How To Configure Throttle and Steering PWM.

Steering and throttle processing nodes require preliminary configuration.
The user has to set up the range of PWM values.


An attempt to execute `run.launch` from steering and throttle without configuration results in exception:

```
Traceback (most recent call last):
  File "/omicron_robocar/catkin_ws/src/steering/src/run_steering.py", line 70, in <module>
    set_variables()
  File "/omicron_robocar/catkin_ws/src/steering/src/run_steering.py", line 25, in set_variables
    raise ("CONFIG does not exist! Please calibrate your car first!")
TypeError: exceptions must be old-style classes or derived from BaseException, not str
PYTHONPATH
/omicron_robocar/catkin_ws/devel/lib/python2.7/dist-packages:/catkin_ws/devel/lib/python2.7/dist-packages:/opt/ros/kinetic/lib/python2.7/dist-packages
Traceback (most recent call last):
  File "/omicron_robocar/catkin_ws/src/throttle/src/run_throttle.py", line 78, in <module>
    set_variables()
  File "/omicron_robocar/catkin_ws/src/throttle/src/run_throttle.py", line 27, in set_variables
    raise ("CONFIG does not exist! Please calibrate your car first!")
TypeError: exceptions must be old-style classes or derived from BaseException, not str
[steering-1] process has died [pid 4388, exit code 1, cmd /omicron_robocar/catkin_ws/src/steering/src/run_steering.py __name:=steering __log:=/.ros/log/74ee8a3c-d0dc-11e5-a419-75b1d9c8907a/steering-1.log].
log file: /.ros/log/74ee8a3c-d0dc-11e5-a419-75b1d9c8907a/steering-1*.log
[run_throttle-2] process has died [pid 4389, exit code 1, cmd /omicron_robocar/catkin_ws/src/throttle/src/run_throttle.py __name:=run_throttle __log:=/.ros/log/74ee8a3c-d0dc-11e5-a419-75b1d9c8907a/run_throttle-2.log].
log file: /.ros/log/74ee8a3c-d0dc-11e5-a419-75b1d9c8907a/run_throttle-2*.log
```


## Configuration for steering module
```
roslaunch steering config.launch
```

That will start a [dynamic configuration node](http://wiki.ros.org/dynamic_reconfigure). Default values (0) will be written to the config.

To overwrite the defaults one should run in another terminal (change values accordingly):
```
rosrun dynamic_reconfigure dynparam set /config_steering STEERING_RIGHT_PWM 1200
rosrun dynamic_reconfigure dynparam set /config_steering STEERING_LEFT_PWM 1600
```

## Configuration for throttle module
```
roslaunch throttle config.launch
```

Overwrite the defaults:
```
rosrun dynamic_reconfigure dynparam set /config_throttle THROTTLE_REVERSE_PWM 1300
rosrun dynamic_reconfigure dynparam set /config_throttle THROTTLE_STOPPED_PWM 1400
rosrun dynamic_reconfigure dynparam set /config_throttle THROTTLE_FORWARD_PWM 1500
```
