# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Drahoš
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( glew C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )

find_package ( OpenGL REQUIRED )
include_directories ( include ${OPENGL_INCLUDE_DIR} )

add_library ( glew src/glew.c )
target_link_libraries ( glew ${OPENGL_LIBRARIES} )

add_executable ( glewinfo src/glewinfo.c )
target_link_libraries ( glewinfo glew )

add_executable ( visualinfo src/visualinfo.c )
target_link_libraries ( visualinfo glew )

install_executable ( glewinfo visualinfo )
install_library ( glew )
install_header ( include/ )
install_data ( LICENSE.txt README.txt )
