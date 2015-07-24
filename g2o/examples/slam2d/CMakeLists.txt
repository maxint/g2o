include(${QT_USE_FILE})

include_directories(${CSPARSE_INCLUDE_DIR})

QT4_WRAP_UI(UI_HEADERS base_main_window.ui)
QT4_WRAP_CPP(UI_SOURCES main_window.h)

add_executable(slam2d_g2o
  main_window.cpp
  slam2d_viewer.cpp
  slam2d_viewer.h
  slam2d_g2o.cpp
  draw_helpers.cpp
  ${UI_HEADERS}
  ${UI_SOURCES}
)

set_target_properties(slam2d_g2o PROPERTIES OUTPUT_NAME slam2d_g2o${EXE_POSTFIX})
include_directories(${CMAKE_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(slam2d_g2o core solver_csparse types_slam2d qglviewer)

