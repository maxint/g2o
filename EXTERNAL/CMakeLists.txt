# Only build CSPARSE if we need to
IF(G2O_BUILD_CSPARSE)
  ADD_SUBDIRECTORY(csparse)
ENDIF()

IF(G2O_HAVE_OPENGL)
  ADD_SUBDIRECTORY(freeglut)
ENDIF()

IF(G2O_HAVE_OPENGL AND QT4_FOUND)
  ADD_SUBDIRECTORY(qglviewer)
ENDIF()
