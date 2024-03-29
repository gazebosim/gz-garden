cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(gz-garden VERSION 1.0.0)

#============================================================================
# Find gz-cmake
#============================================================================
# If you get an error at this line, you need to install gz-cmake
find_package(gz-cmake3 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
gz_configure_project()

# all list of garden packages

gz_find_package(gz-common5 REQUIRED)
gz_find_package(gz-fuel_tools8 REQUIRED)
gz_find_package(gz-sim7 REQUIRED)
gz_find_package(gz-gui7 REQUIRED)
gz_find_package(gz-launch6 REQUIRED)
gz_find_package(gz-math7 REQUIRED COMPONENTS eigen3)
gz_find_package(gz-msgs9 REQUIRED)
gz_find_package(gz-physics6 REQUIRED)
gz_find_package(gz-plugin2 REQUIRED)
gz_find_package(gz-rendering7 REQUIRED)
gz_find_package(gz-sensors7 REQUIRED)
gz_find_package(gz-transport12 REQUIRED)
gz_find_package(gz-utils2 REQUIRED)
gz_find_package(sdformat13 REQUIRED)

if(build_warnings)
  set(all_warnings " CONFIGURATION WARNINGS:")
  foreach (msg ${build_warnings})
    gz_string_append(all_warnings " -- ${msg}" DELIM "\n")
  endforeach ()
  message(WARNING "${all_warnings}")
endif (build_warnings)

if(build_errors)
  message(SEND_ERROR "-- BUILD ERRORS: These must be resolved before compiling.")
  foreach(msg ${build_errors})
    message(SEND_ERROR "-- ${msg}")
  endforeach()
  message(SEND_ERROR "-- END BUILD ERRORS\n")

  set(error_str "Errors encountered in build. Please see BUILD ERRORS above.")

  message(FATAL_ERROR "${error_str}")

endif()

install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
