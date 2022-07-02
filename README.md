# build_ros2_exec_container_example
Build example for docker container with custom package and ros2 core.

# setup
install docker(https://docs.docker.com/engine/install/ubuntu/)

# usage
To run this example, do the following.
```
git clone https://github.com/akira-nishiyama/build_ros2_exec_container_example.git
cd build_ros2_eec_container_example
docker-compose build
docker-compose up
```
Enter Ctrl+c to exit.

# exec result
We get the following results. 

```
Starting env_listener_1 ... done
Starting env_talker_1   ... done
Attaching to env_talker_1, env_listener_1
talker_1    | [INFO] [1656748948.461309414] [minimal_publisher]: Publishing: "Hello World: 0"
talker_1    | [INFO] [1656748948.947667336] [minimal_publisher]: Publishing: "Hello World: 1"
talker_1    | [INFO] [1656748949.447749747] [minimal_publisher]: Publishing: "Hello World: 2"
talker_1    | [INFO] [1656748949.947751669] [minimal_publisher]: Publishing: "Hello World: 3"
talker_1    | [INFO] [1656748950.447781256] [minimal_publisher]: Publishing: "Hello World: 4"
talker_1    | [INFO] [1656748950.947751269] [minimal_publisher]: Publishing: "Hello World: 5"
talker_1    | [INFO] [1656748951.447926078] [minimal_publisher]: Publishing: "Hello World: 6"
listener_1  | [INFO] [1656748951.586250380] [minimal_subscriber]: I heard: "Hello World: 6
talker_1    | [INFO] [1656748951.947916486] [minimal_publisher]: Publishing: "Hello World: 7"
listener_1  | [INFO] [1656748951.948192281] [minimal_subscriber]: I heard: "Hello World: 7
talker_1    | [INFO] [1656748952.447858693] [minimal_publisher]: Publishing: "Hello World: 8"
listener_1  | [INFO] [1656748952.448205040] [minimal_subscriber]: I heard: "Hello World: 8
talker_1    | [INFO] [1656748952.947910963] [minimal_publisher]: Publishing: "Hello World: 9"
listener_1  | [INFO] [1656748952.948246575] [minimal_subscriber]: I heard: "Hello World: 9
```

# Image size

```
REPOSITORY   TAG                     IMAGE ID       CREATED       SIZE
py_pubsub    latest                  5283a26d5ab9   3 hours ago   466MB
ros          humble-ros-base-jammy   014f0adf022e   3 weeks ago   750MB
ros          humble-ros-core-jammy   cbadb9c27f26   3 weeks ago   422MB
ubuntu       jammy                   27941809078c   3 weeks ago   77.8MB
```

# License
This software is released under the Apache 2.0 License where except otherwise indicated, see LICENSE.  
py_pubsub package is refers to [ROS2 Tutorial](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html)

