# Copyright (C) 2007-2009 LuaDist.
# Created by Peter Drahoš
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(glew C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
INCLUDE(dist.cmake)

FIND_PACKAGE(OpenGL REQUIRED)
INCLUDE_DIRECTORIES(include ${OPENGL_INCLUDE_DIR})

ADD_LIBRARY(glew SHARED src/glew.c)
TARGET_LINK_LIBRARIES(glew ${OPENGL_LIBRARIES})

ADD_EXECUTABLE(glewinfo src/glewinfo.c)
TARGET_LINK_LIBRARIES(glewinfo glew)

ADD_EXECUTABLE(visualinfo src/visualinfo.c)
TARGET_LINK_LIBRARIES(visualinfo glew)

INSTALL(TARGETS glewinfo visualinfo DESTINATION ${INSTALL_BIN})
INSTALL(TARGETS glew DESTINATION ${INSTALL_LIB})
INSTALL(DIRECTORY include/ DESTINATION ${INSTALL_INC})
INSTALL(FILES LICENSE.txt README.txt DESTINATION ${INSTALL_DATA})
