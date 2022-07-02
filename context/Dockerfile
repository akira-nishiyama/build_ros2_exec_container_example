################################
# multi-stage for build
################################
FROM ros:humble-ros-base-jammy as build
#project workspace
ARG PRJ_WS=/workspace/install
ARG TMP_WS=/tmp
WORKDIR $TMP_WS

# import project
# copy from host directory.
COPY ./project/src $TMP_WS/src
## clone using vcstool is also ok.
##(see https://github.com/dirk-thomas/vcstool for detail)
#RUN echo "\
#repositories: \n\
#  ros2/demos: \n\
#    type: git \n\
#    url: https://github.com/ros2/demos.git \n\
#    version: ${ROS_DISTRO} \n\
#" > ./project.repos
#RUN vcs import ./src < ./project.repos

# install rosdep
RUN apt-get update && apt-get install -y --no-install-recommends python3-rosdep

# resolve dependency
RUN rosdep update && rosdep install -y --from-paths $TMP_WS/src

# build
RUN colcon build --install-base $PRJ_WS

################################
# multi-stage for exec
################################
FROM ros:humble-ros-core-jammy as exec
#project workspace
ARG PRJ_WS=/workspace/install
WORKDIR $PRJ_WS
# import artifacts
COPY --from=build $PRJ_WS $PRJ_WS

# install rosdep
RUN apt-get update && apt-get install -y --no-install-recommends python3-rosdep

# resolve dependency
RUN rosdep init && rosdep update \
		&& rosdep install -y --from-paths $PRJ_WS \
		&& apt-get remove -y python3-rosdep \
		&& apt-get -y clean \
		&& rm -rf /var/lib/apt/lists/*

# source entrypoint setup
ENV PRJ_WS $PRJ_WS
RUN sed --in-place --expression \
	'$isource "$PRJ_WS/local_setup.sh"' \
	/ros_entrypoint.sh

CMD ["ros2", "run", "py_pubsub", "talker"]
#CMD ["bash"]
