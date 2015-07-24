cmake_minimum_required(VERSION 3.0)

project(qglviewer)

find_package(Qt4 REQUIRED)

set(QT_USE_QTOPENGL TRUE)
set(QT_USE_QTXML TRUE)
include(${QT_USE_FILE})

file(GLOB HEADERS *.h)
file(GLOB SOURCES *.cpp)

QT4_WRAP_UI(UI_HEADERS ImageInterface.ui)
QT4_WRAP_CPP(UI_SOURCES camera.h frame.h keyFrameInterpolator.h manipulatedFrame.h manipulatedCameraFrame.h qglviewer.h)

add_library(${PROJECT_NAME} STATIC
  ${HEADERS} ${SOURCES}
  ${UI_HEADERS} ${UI_SOURCES}
  )
target_compile_definitions(${PROJECT_NAME} PRIVATE NO_VECTORIAL_RENDER)
target_include_directories(${PROJECT_NAME}
  PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${QT_INCLUDES}
  PRIVATE ${CMAKE_CURRENT_BINARY_DIR}
  )
target_link_libraries(${PROJECT_NAME} ${QT_LIBRARIES} ${OPENGL_LIBRARY})

# Install
install(TARGETS ${PROJECT_NAME}
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
  LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
  ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
install(FILES ${HEADERS} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/EXTERNAL/${PROJECT_NAME})
