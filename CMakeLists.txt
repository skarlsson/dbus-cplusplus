cmake_minimum_required(VERSION 3.9)
project(dbus-c++-1 VERSION 1.0.1 DESCRIPTION "dbus-c++-1")
include(GNUInstallDirs)

SET(SRC src/connection.cpp
src/eventloop-integration.cpp  
src/pendingcall.cpp
src/debug.cpp 
#src/glib-integration.cpp
src/property.cpp
src/dispatcher.cpp
src/interface.cpp
src/server.cpp
#src/ecore-integration.cpp
src/introspection.cpp
src/types.cpp
src/error.cpp
src/message.cpp
src/eventloop.cpp
src/object.cpp)
#file(GLOB SRC_FILES src/*.cpp)
#list(REMOVE_ITEM SRC_FILES "src/ecore-integration.cpp")

file(GLOB INC_FILES include/dbus-c++/*.h)

#include_directories(/usr/include/dbus-1.0)
include_directories(${CMAKE_SOURCE_DIR}/include) 

find_package(PkgConfig REQUIRED)
pkg_check_modules(DBUS dbus-1)  # saka fix for ubuntu
include_directories(${DBUS_INCLUDE_DIRS})

add_library(dbus-c++-shiny-1 SHARED ${SRC})

INSTALL(TARGETS dbus-c++-shiny-1
                LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
                ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
                )

INSTALL(DIRECTORY ${CMAKE_SOURCE_DIR}/include/ DESTINATION include)


