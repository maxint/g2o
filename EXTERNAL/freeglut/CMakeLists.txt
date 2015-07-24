file(GLOB HEADERS *.h *.hpp)
add_library(freeglut_minimal ${G2O_LIB_TYPE}
  ${HEADERS}
  freeglut_font.cpp
  freeglut_stroke_mono_roman.cpp
  freeglut_stroke_roman.cpp
)

target_link_libraries(freeglut_minimal ${OPENGL_gl_LIBRARY})
set_target_properties(freeglut_minimal PROPERTIES OUTPUT_NAME ${LIB_PREFIX}ext_freeglut_minimal)

# Install
install(TARGETS freeglut_minimal
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
  LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
  ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
install(FILES ${HEADERS} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/EXTERNAL/freeglut)
