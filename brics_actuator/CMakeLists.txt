cmake_minimum_required(VERSION 2.8)
project(brics_actuator)

find_package(genmsg REQUIRED)

set(MSG_DEPS geometry_msgs std_msgs)

find_package(catkin REQUIRED ${MSG_DEPS})

catkin_package(
  INCLUDE_DIRS include
)

set(MSG_FILES
	CartesianPose.msg
	CartesianTwist.msg
	CartesianVector.msg
	CartesianWrench.msg
	JointAccelerations.msg
	JointConstraint.msg
	JointImpedances.msg
	JointPositions.msg
	JointTorques.msg
	JointValue.msg
	JointVelocities.msg
	Poison.msg
)

add_message_files(DIRECTORY msg FILES ${MSG_FILES})

generate_messages(DEPENDENCIES ${MSG_DEPS})

