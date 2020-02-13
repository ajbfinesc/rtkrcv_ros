cmake_minimum_required(VERSION 2.8.3)
project(rtkrcv_ros)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  geometry_msgs
  message_generation
)

 add_message_files(
   FILES
   states_hms.msg
   states_tow.msg
   geodetic_coord.msg
   nmea_gpgga.msg
   nmea_gpgsa.msg
   nmea_gpgsv.msg
   nmea_gprmc.msg
   nmea.msg
   gsv_sat.msg
)

add_service_files(
    DIRECTORY srv
    FILES
    receive_command.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES rtkrcv_ros
  CATKIN_DEPENDS roscpp std_msgs message_runtime message_generation geometry_msgs
  DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${PROJECT_SOURCE_DIR}/include/rtklib
  ${PROJECT_SOURCE_DIR}/../../devel/include
)

set(OPTION -DENAGLO -DENAGAL -DENAQZS -DENACMP -DTRACE -DNFREQ=3 -DNEXOBS=3)
set(CFLAGS  -O3 -ansi -pedantic -Wno-unused-but-set-variable -Wno-unused-variable -Wno-unused-function ${OPTION} -g)
add_definitions(${CFLAGS} ${OPTION})
#############Sources rtklib receivers gnss##############
set(RTKLIB_RECEIVERS  src/src/rcv/binex.c src/src/rcv/crescent.c src/src/rcv/gw10.c src/src/rcv/javad.c
src/src/rcv/novatel.c src/src/rcv/nvs.c src/src/rcv/rcvlex.c src/src/rcv/rt17.c src/src/rcv/septentrio.c
src/src/rcv/skytraq.c src/src/rcv/ss2.c src/src/rcv/ublox.c)

######################Sources rtklib rtkrcv#####################
set(RTKLIB_SOURCES_RTKRCV src/vt.c src/src/rtkcmn.c src/src/rtksvr.c src/src/rtkpos.c src/src/geoid.c src/src/solution.c
src/src/lambda.c src/src/sbas.c src/src/stream.cpp src/src/rcvraw.c src/src/rtcm.c src/src/preceph.c
src/src/options.c src/src/pntpos.c src/src/ppp.c src/src/ppp_ar.c src/src/rcv/novatel.c src/src/ephemeris.c
src/src/rinex.c src/src/ionex.c src/src/rtcm2.c src/src/rtcm3.c src/src/rtcm3e.c src/src/qzslex.c ${RTKLIB_RECEIVERS})

###################Executable rtkrcv_ros_node####################
add_executable(rtkrcv_ros_node src/rtkrcv.cpp ${RTKLIB_SOURCES_RTKRCV})
add_dependencies(rtkrcv_ros_node rtkrcv_ros_msgs_generate_messages_cpp ${catkin_EXPORTED_TARGETS} ${${PROJECT_NAME}_EXPORTED_TARGETS}  )
target_link_libraries(rtkrcv_ros_node ${catkin_LIBRARIES})
