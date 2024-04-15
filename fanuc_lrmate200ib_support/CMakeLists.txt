cmake_minimum_required(VERSION 3.12)
project(fanuc_lrmate200ib_support)

find_package(ament_cmake REQUIRED)
ament_package()

install(DIRECTORY launch meshes urdf
  DESTINATION share/${PROJECT_NAME})
install(FILES readme.md
  DESTINATION share/${PROJECT_NAME})
