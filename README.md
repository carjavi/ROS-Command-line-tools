<p align="center"><img src="./img/ros_logo.png" height="100" alt=" " /></p>
<h1 align="center"> ROS Command-line tools </h1> 
<h4 align="right">Jun 23</h4>

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)

![ROS](https://img.shields.io/badge/ros-%230A0FF9.svg?style=for-the-badge&logo=ros&logoColor=white)

<br>

# ROS Cheat Sheet


- [ROS Cheat Sheet](#ros-cheat-sheet)
  - [Filesystem Command-line Tools](#filesystem-command-line-tools)
  - [ROS commands summary](#ros-commands-summary)
  - [Logging Command-line Tools](#logging-command-line-tools)
  - [Graphical Tools](#graphical-tools)
- [Workspaces](#workspaces)
  - [Create workspace](#create-workspace)
  - [Add repo to workspace](#add-repo-to-workspace)
  - [Resolve dependencies in workspace](#resolve-dependencies-in-workspace)
- [Packages](#packages)
  - [Create a package](#create-a-package)
  - [Package folders](#package-folders)
  - [Release repo packages](#release-repo-packages)
- [Running System](#running-system)
  - [Run ROS using plain](#run-ros-using-plain)
  - [Running `roslaunch` will run its own `roscore` automatically](#running-roslaunch-will-run-its-own-roscore-automatically)
  - [Nodes, topics, messages](#nodes-topics-messages)
  - [Remote connection - master’s ROS environment](#remote-connection---masters-ros-environment)
  - [Remote connection - your environment](#remote-connection---your-environment)
  - [ROS Console](#ros-console)
- [Developer Commands](#developer-commands)
- [Setting up your environment](#setting-up-your-environment)
  - [ROS\_MASTER\_URI](#ros_master_uri)
  - [ROS\_HOSTNAME](#ros_hostname)
  - [Examples Commands](#examples-commands)

<br>

## Filesystem Command-line Tools

<table style="border-collapse: collapse;border-top: 0.5pt solid ; border-bottom: 0.5pt solid ; ">
    <colgroup><col align="left"><col align="left"><col align="left"></colgroup>
    <thead>
        <tr>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Command</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Action</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Example usage and subcommand examples</p></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rospack/rosstack</code></p></td>
            <td style="" align="left" valign="top"><p>A tool inspecting packages/stacks.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ rospack find [package]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">roscd</code></p></td>
            <td style="" align="left" valign="top"><p>Changes directories to a package or
stack.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ roscd [package[/subdir]]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rosls</code></p></td>
            <td style="" align="left" valign="top"><p>Lists package or stack information.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ rosls [package[/subdir]]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">roscreate-pkg</code></p></td>
            <td style="" align="left" valign="top"><p>Creates a new ROS package.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ roscreate-pkg [package name]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">roscreate-stack</code></p></td>
            <td style="" align="left" valign="top"><p>Creates a new ROS stack.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ ros command [parameter]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rosdep</code></p></td>
            <td style="" align="left" valign="top"><p>Installs ROS package system dependencies.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">rosdep install [package]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rosmake</code></p></td>
            <td style="" align="left" valign="top"><p>Builds a ROS package.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ rosmake [package]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">roswtf</code></p></td>
            <td style="" align="left" valign="top"><p>Displays a errors and warnings about a running ROS system or launch file.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ roswtf or roswtf [file]</code></p></td>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rxdeps</code></p></td>
            <td style="" align="left" valign="top"><p>Displays package structure and dependencies.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ rxdeps [options]</code></p></td>
        </tr>
        <tr>
	        <td style="" align="left" valign="top"><p><code class="literal">rosed</code></p></td>
	        <td style="" align="left" valign="top"><p>It allows you to directly edit a file within a package by package name rather than having to know the package path.</p></td>
	        <td style="" align="left" valign="top">
                <p>Usage:</p>
                <p><code class="literal">$ rosed packagename filename</code></p>
                <p>Example:</p>
                <p><code class="literal">$ rosed roscpp ros.h</code></p>
            </td>
	    </tr>
    </tbody>
</table>


<br>
<br>


## ROS commands summary

<table style="border-collapse: collapse;border-top: 0.5pt solid ; border-bottom: 0.5pt solid ; ">
    <colgroup><col align="left"><col align="left"><col align="left"></colgroup>
    <thead>
        <tr>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Command</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Action</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Example usage and subcommand examples</p></th>
        </tr>
    </thead>
    <tbody>
    <tr><td style="" align="left" valign="top">
    <p><code class="literal">roscore</code></p>
    </td><td style="" align="left" valign="top">
    <p>This <a id="id98" class="indexterm"></a>starts the Master</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ roscore</code></p>
    </td></tr><tr><td style="" align="left" valign="top">
    <p><code class="literal">rosrun</code></p>
    </td><td style="" align="left" valign="top">
    <p>This <a id="id99" class="indexterm"></a>runs an executable program and creates nodes</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ rosrun [package name] [executable name]</code></p>
    <p><code class="literal">$ rosrun package executable</code></p>
    </td></tr><tr><td style="" align="left" valign="top">
    <p><code class="literal">rosnode</code></p>
    </td><td style="" align="left" valign="top">
    <p>This <a id="id100" class="indexterm"></a>shows information about nodes and lists the active nodes</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ rosnode info [node name]</code></p>
    <p><code class="literal">$ rosnode &lt;subcommand&gt;</code></p>
    <p><code class="literal">$ rosnode list</code> List active nodes.</p>
    <p><code class="literal">$ rosnode ping [node name]</code> Test connectivity to node.</p>
    <p><code class="literal">$ rosnode ping --all</code> Ping all nodes.</p>
    <p><code class="literal">$ rosnode info [node name]</code> Print information about a node.</p>
    <p><code class="literal">$ rosnode machine</code> List nodes running on a particular ma-
chine.</p>
<p><code class="literal">$ rosnode kill [node name]</code> Kills a running node.</p>
<p><code class="literal">$ rosnode kill -a</code> Kill all nodes:</p>
    </td></tr>
    <tr><td style="" align="left" valign="top">
    <p><code class="literal">rostopic</code></p>
    </td><td style="" align="left" valign="top">
    <p>This<a id="id101" class="indexterm"></a> shows information about ROS topics</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ rostopic &lt;subcommand&gt; &lt;topic name&gt;</code></p>
    <p>Subcommands: <code class="literal">echo</code>, <code class="literal">info</code>, and <code class="literal">type</code></p>
    <p><code class="literal">$ rostopic echo</code> Print messages to screen.</p>
    <p><code class="literal">$ rostopic list</code> Print information about active topics.</p>
    <p><code class="literal">$ rostopic pub</code> Publish data to topic.</p>
    <p><code class="literal">$ rostopic type</code> Print topic type.</p>
    <p><code class="literal">$ rostopic find</code> Find topics by type.</p>
    <p><code class="literal">$ rostopic hz</code> Display publishing rate of topic.</p>
    <p><code class="literal">$ rostopic bw</code> Display bandwidth used by topic.</p>
    <p>Example:</p>
    <p>Publish hello at 10 Hz: <code class="literal">$ rostopic pub -r 10 /topic name std msgs/String hello</code></p>
    <p>Clear the screen after each message is published: <code class="literal">$ rostopic echo -c /topic name</code></p>
    <p>Display messages that match a given Python expression: <code class="literal">$ rostopic echo --filter "m.data=='foo'" /topic name</code></p>
    <p>Pipe the output of rostopic to rosmsg to view the msg type: <code class="literal">$ rostopic type /topic name | rosmsg show</code></p>
    </td></tr>
    <tr><td style="" align="left" valign="top">
    <p><code class="literal">rosmsg</code></p>
    </td><td style="" align="left" valign="top">
    <p>This <a id="id102" class="indexterm"></a>shows information about the message types</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ rosmsg &lt;subcommand&gt; [package name]/ [message type]</code></p>
    <p>Subcommands: <code class="literal">show</code>, <code class="literal">type</code>, and <code class="literal">list</code></p>
    <p><code class="literal">$ rosmsg show</code> Display the fields in the msg.</p>
    <p><code class="literal">$ rosmsg package</code> List all the messages in a package.</p>
    <p><code class="literal">$ rosnode packages</code> List all the packages with messages.</p>
    <p><code class="literal">$ rosmsg users sensor msgs/CameraInfo</code> List the files using sensor msgs/CameraInfo.</p>
    </td></tr>
        <tr><td style="" align="left" valign="top">
        <p><code class="literal">roslaunch</code></p>
        </td><td style="" align="left" valign="top">
        <p>Starts ROS nodes locally and remotely via SSH, as well as
setting parameters on the parameter server.</p>
        </td><td style="" align="left" valign="top">
        <p>Launch on a different port: <code class="literal">$ roslaunch -p 1234 package filename.launch</code></p>
        <p>Launch a file in a package: <code class="literal">$ roslaunch package filename.launch</code></p>
        <p>Launch on the local nodes: <code class="literal">$ roslaunch --local package filename.launch</code></p>
    </td></tr>
    </td></tr><tr><td style="" align="left" valign="top">
    <p><code class="literal">rosservice</code></p>
    </td><td style="" align="left" valign="top">
    <p>This <a id="id103" class="indexterm"></a>displays the runtime information about various services and allows the display of messages being sent to a topic</p>
    </td><td style="" align="left" valign="top">
    <p><code class="literal">$ rosservice &lt;subcommand&gt; [service name]</code></p>
    <p>Subcommands: <code class="literal">args</code>, <code class="literal">call</code>, <code class="literal">find</code>, <code class="literal">info</code>, <code class="literal">list</code>, and <code class="literal">type</code></p>
    </td></tr>
    <tr><td style="" align="left" valign="top">
    <p><code class="literal">rosparam</code></p>
    </td><td style="" align="left" valign="top">
    <p>This<a id="id104" class="indexterm"></a> is used to get and set parameters (data) used by nodes. A tool for getting and setting ROS parameters on the
parameter server using YAML-encoded files.</p>
    </td>
    <td style="" align="left" valign="top">
    <p><code class="literal">$ rosparam &lt;subcommand&gt; [parameter]</code></p>
    <p>Subcommands: <code class="literal">get</code>, <code class="literal">set</code>, <code class="literal">list</code>, and <code class="literal">delete</code></p>
    <p><code class="literal">$ rosparam set</code> Set a parameter.</p>
    <p><code class="literal">$ rosparam get</code> Get a parameter.</p>
    <p><code class="literal">$ rosparam load</code> Load parameters from a file.</p>
    <p><code class="literal">$ rosparam dump</code> Dump parameters to a file.</p>
    <p><code class="literal">$ rosparam delete</code> Delete a parameter.</p>
    <p><code class="literal">$ rosparam list</code> List parameter names.</p>
    <p>Example:</p>
    <p>List all the parameters in a namespace: <code class="literal">$ rosparam list /namespace</code></p>
    <p>Setting a list with one as a string, integer, and 
oat: <code class="literal">$ rosparam set /foo "['1', 1, 1.0]"</code></p>
<p>Dump only the parameters in a specific namespace to file: <code class="literal">$ rosparam dump dump.yaml /namespace</code></p>
</td></tr>
    <tr>
	   <td style="" align="left" valign="top"><p><code class="literal">rosservice</code></p></td>
	   <td style="" align="left" valign="top"><p>A tool for listing and querying ROS services.</p></td>
	   <td style="" align="left" valign="top">
            <p><code class="literal">$ rosservice list</code> Print information about active services.</p>
            <p><code class="literal">$ rosservice node</code> Print the name of the node providing a
service.</p>
            <p><code class="literal">$ rosservice call</code> Call the service with the given args.</p>
            <p><code class="literal">$ rosservice args</code> List the arguments of a service.</p>
            <p><code class="literal">$ rosservice type</code> Print the service type.</p>
            <p><code class="literal">$ rosservice uri</code> Print the service ROSRPC uri.</p>
            <p><code class="literal">$ rosservice find</code> Find services by service type.</p>
            <p>Examples:</p>
            <p>Call a service from the command-line: <code class="literal">$ rosservice call /add two ints 1 2</code></p>
             <p>Pipe the output of rosservice to rossrv to view the srv type: <code class="literal">$ rosservice type add two ints | rossrv show</code></p>
             <p>Display all services of a particular type: <code class="literal">$ rosservice find rospy tutorials/AddTwoInts</code></p>
       </td>
	</tr>
    </tbody>
</table>


<br>
<br>

## Logging Command-line Tools

<table style="border-collapse: collapse;border-top: 0.5pt solid ; border-bottom: 0.5pt solid ; ">
    <colgroup><col align="left"><col align="left"><col align="left"></colgroup>
    <thead>
        <tr>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Command</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Action</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Example usage and subcommand examples</p></th>
        </tr>
    </thead>
    <tbody>
     </td></tr>
        <tr><td style="" align="left" valign="top">
        <p><code class="literal">rosbag</code></p>
        </td><td style="" align="left" valign="top">
        <p>This is a set of tools for recording from and playing back to
ROS topics.</p>
        </td><td style="" align="left" valign="top">
        <p>Record all topics: <code class="literal">$ rosbag record -a</code></p>
        <p>Record select topics: <code class="literal">$ rosbag record topic1 topic2</code></p>
    </td></tr>
    </td></tr>
        <tr><td style="" align="left" valign="top">
        <p><code class="literal">rosbag play</code></p>
        </td><td style="" align="left" valign="top">
        <p>will take the contents of one or more bagfile,
and play them back in a time-synchronized fashion.</p>
        </td><td style="" align="left" valign="top">
        <p>Replay all messages without waiting: <code class="literal">$ rosbag play -a demo log.bag</code></p>
        <p>Replay several bag files at once: <code class="literal">$ rosbag play demo1.bag demo2.bag</code></p>
    </td></tr>
    </tbody>
</table>

<br>
<br>

## Graphical Tools

<table style="border-collapse: collapse;border-top: 0.5pt solid ; border-bottom: 0.5pt solid ; ">
    <colgroup><col align="left"><col align="left"><col align="left"></colgroup>
    <thead>
        <tr>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Command</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Action</p></th>
            <th style="border-bottom: 0.5pt solid ; " align="left" valign="bottom"><p>Example usage and subcommand examples</p></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rxgraph</code></p></td>
            <td style="" align="left" valign="top"><p>Displays a graph of the ROS nodes that are currently running,as well as the ROS topics that connect them.</p></td>
            <td style="" align="left" valign="top"><p><code class="literal">$ rxgraph</code></p>
        </tr>
        <tr>
            <td style="" align="left" valign="top"><p><code class="literal">rxplot</code></p></td>
            <td style="" align="left" valign="top"><p>A tool for plotting data from one or more ROS topic fields using matplotlib.</p></td>
            <td style="" align="left" valign="top"><p>To graph the data in different plots: <code class="literal">$ rxplot /topic1/field1 /topic2/field2</code></p>
            <p>To graph the data all on the same plot: <code class="literal">$ rxplot /topic1/field1,/topic2/field2</code></p>
            <p>To graph multiple fields of a message: <code class="literal">$ rxplot /topic1/field1:field2:field3</code></p>
        </tr>
        <tr>
	        <td style="" align="left" valign="top"><p><code class="literal">rxbag</code></p></td>
	        <td style="" align="left" valign="top"><p>A tool for visualizing, inspecting, and replaying histories (bag
files) of ROS messages.</p></td>
	        <td style="" align="left" valign="top"><p><code class="literal">$ rxbag bag file.bag</code></p></td>
	    </tr>
        <tr>
	        <td style="" align="left" valign="top"><p><code class="literal">rxconsole</code></p></td>
	        <td style="" align="left" valign="top"><p>A tool for displaying and filtering messages published on
rosout.</p></td>
	        <td style="" align="left" valign="top"><p><code class="literal">$ rxconsole</code></p></td>
	    </tr>
    </tbody>
</table>

<br>
<br>

# Workspaces
## Create workspace
```
mkdir catkin_ws
cd catkin_ws
wstool init src
catkin_make
source devel/setup.bash
```

`Source space (/src)`: contains the source code of catkin packages. Subfolder of this are the ROS packages you want to add to your system. All your stuff goes here!

`Build space (/build)`: space where cmake is invoked to build the catkin packages cmake and catkin keep their cache information and other intermediate files here. Not where catkin_make is invoked!

`Devel space (/devel)`: Space where built targets are placed prior to being installed

## Add repo to workspace
```
roscd
cd ../src
wstool set repo_name --git http://github.com/org/repo_name.git --version=indigo-devel
wstool up
```

## Resolve dependencies in workspace
```
sudo rosdep init # only once
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro=indigo -y
```
<br>
<br>

# Packages
## Create a package
```
catkin_create_pkg package_name [dependencies ...]
```
## Package folders
```
include/package_name   # C++ header files
src                    # Source files, Python libraries in subdirectories
scripts                # Python nodes and scripts
msg, srv, action       # Message, Service, and Action definitions
```
## Release repo packages
```
catkin_generate_changelog
# review & commit changelogs"
catkin_prepare_release
bloom-release --track indigo --ros-distro indigo repo_name
```
<br>
<br>

# Running System

## Run ROS using plain
```
roscore
```

## Running `roslaunch` will run its own `roscore` automatically
```
roslaunch my_package package_launchfile.launch
```

## Nodes, topics, messages
```
rosnode list
rostopic list
rostopic echo cmd_vel
rostopic hz cmd_vel
rostopic info cmd_vel
rosmsg show geometry_msgs/Twist
```

## Remote connection - master’s ROS environment
```
export ROS_IP or ROS_HOSTNAME set to this machine’s network address
export ROS_MASTER_URI set to URI containing that IP or hostname
```

## Remote connection - your environment
```
export ROS_IP or ROS_HOSTNAME #set to your machine’s network address
export ROS_MASTER_URI #set to the URI from the master
```
To debug, check ping from each side to the other, run roswtf on each side

## ROS Console
```
vi $HOME/.ros/config/rosconsole.config log4j.logger.ros.package_name=DEBUG
```
Adjust using rqt_logger_level and monitor via rqt_console. Use the roslaunch --screen flag to force all node output to the screen, as if each declared <node> had the output="screen" attribute.

<br>
<br>


# Developer Commands

| Name      | Purpose                                         |
|-----------|-------------------------------------------------|
| `catkin_make`   | Build all projects in workspace. Run from root folder. Example: `~/catkin_ws/`. |
| `catkin_make clean` | Clean all projects in workspace. Run from root folder. Example: `~/catkin_ws/`. |

<br>
<br>

# Setting up your environment

## ROS_MASTER_URI
Set the address of the robot.
```
export ROS_MASTER_URI=http://<robot ip>:11311/
```
## ROS_HOSTNAME
Should be set to the PC you are as the workstation.
```
export ROS_HOSTNAME=<workstation IP>
```

<br>
<br>


## Examples Commands
```
$ rostopic find sensor_msgs/String // you want to find all the topics of a certain message type
```

More info:
http://wiki.ros.org/ROS/CommandLineTools


ROS2: https://osrf.github.io/ros2multirobotbook/intro.html

ROS1 & NodeJs: http://wiki.ros.org/rosnodejs

<br>

---
Copyright &copy; 2022 [carjavi](https://github.com/carjavi). <br>
```www.instintodigital.net``` <br>
carjavi@hotmail.com <br>
<p align="center">
    <a href="https://instintodigital.net/" target="_blank"><img src="./img/developer.png" height="100" alt="www.instintodigital.net"></a>
</p>


