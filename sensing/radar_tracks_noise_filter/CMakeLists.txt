cmake_minimum_required(VERSION 3.5)
project(radar_tracks_noise_filter)

# Dependencies
find_package(autoware_cmake REQUIRED)
autoware_package()

# Targets
ament_auto_add_library(radar_tracks_noise_filter_node_component SHARED
  src/radar_tracks_noise_filter_node/radar_tracks_noise_filter_node.cpp
)

rclcpp_components_register_node(radar_tracks_noise_filter_node_component
  PLUGIN "radar_tracks_noise_filter::RadarTrackCrossingNoiseFilterNode"
  EXECUTABLE radar_tracks_noise_filter_node
)

# Tests
if(BUILD_TESTING)
  list(APPEND AMENT_LINT_AUTO_EXCLUDE ament_cmake_uncrustify)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

# Package
ament_auto_package(
  INSTALL_TO_SHARE
  launch
)
