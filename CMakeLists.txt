cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-garden VERSION 1.0.0)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 2.7.0 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
ign_configure_project(VERSION_SUFFIX pre1)

# all list of garden packages

ign_find_package(ignition-common4 REQUIRED VERSION 4.3)
ign_find_package(ignition-fuel_tools7 REQUIRED)
ign_find_package(ignition-gazebo7 REQUIRED)
ign_find_package(ignition-gui7 REQUIRED)
ign_find_package(ignition-launch6 REQUIRED)
ign_find_package(ignition-math6 REQUIRED COMPONENTS eigen3 VERSION 6.9)
ign_find_package(ignition-msgs8 REQUIRED)
ign_find_package(ignition-physics5 REQUIRED)
ign_find_package(ignition-plugin1 REQUIRED VERSION 1.2.1)
ign_find_package(ignition-rendering7 REQUIRED VERSION 6.0.1)
ign_find_package(ignition-sensors7 REQUIRED)
ign_find_package(ignition-tools REQUIRED VERSION 1.3)
ign_find_package(ignition-transport11 REQUIRED)
ign_find_package(ignition-utils1 REQUIRED VERSION 1.1)
ign_find_package(sdformat12 REQUIRED)

install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
