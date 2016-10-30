Simple node to try the radar ranging.

There are two radar rangers.  One goes in a location across the room, the other is attached to a computer.
Note: The antennas need to be attached BEFORE powering up.  They go on the connector marked "A".

For the one that goes with the computer, you have to use a USB power source in addition to the USB signal source.
Plugging into two USB ports on a laptop generally works, but it is possible you will need more current than a laptop
USB port will provide, in which case plug the power one into a USB charger that can deliver an amp or two.

The USB connectors are hard to see.  They are located underneath the ethernet connector and there are two of them on each board.
Connect the power cable to the connector below the "P" that I inscribed on the top of the ethernet connector.
Connect the data cable to the one below the "S" (for signal) that I inscribed.

The other just needs the power source and only has a "P" for power on it.  If you get them mixed up, no big deal, but you won't
get ranges unless you swap them or change the value of DEFAULT_DEST_NODE_ID from 2 to 1 on line 41 of radar_ranging_node.cpp .

When you plug in the USB cable, you should see it attach on /dev/ttyACM0
If not, you can change the port on line 101 of radar_ranging_node.cpp

Run the node as usual with roscore, if it is all working you should get a range printed out.

This is the simplest example I have, just a modification of their sample code to put it into a class, add some
helpful comments, and make it a ROS node.

There is a lot more you can do with it, such as change the power output level. I think I had it set on 7 or 8 out of a max of 9
power.

I wrote a library of code to do things like take a group of samples, toss the extremes and average the middle.
I also have it incorporated into a Kalman filter that has a bunch of other data, such as odometry and laser
rangefinder data.  That data is fed into the ROS package robot_localization:
http://wiki.ros.org/robot_localization

If it looks like these are useful, let me know and we can move forward with them.



