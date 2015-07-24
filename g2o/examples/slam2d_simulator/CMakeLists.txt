include_directories(${CSPARSE_INCLUDE_DIR})

add_executable(tutorial_slam2d_simulator
  rand.h
  simulator.h simulator.cpp
  slam2d_simulator.cpp
)
target_link_libraries(tutorial_slam2d_simulator core types_slam2d solver_csparse)
