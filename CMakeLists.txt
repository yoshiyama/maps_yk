# Copyright (C) 2022 The Qt Company Ltd.
# SPDX-License-Identifier: BSD-3-Clause
set(CMAKE_PREFIX_PATH "C:/Qt/6.5.0/msvc2019_64")
set(CMAKE_INCLUDE_CURRENT_DIR ON)
cmake_minimum_required(VERSION 3.16)
project(maps LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
#set(CMAKE_PREFIX_PATH ="C:/Qt/6.5.0/msvc2019_64")


if(NOT DEFINED INSTALL_EXAMPLESDIR)
    set(INSTALL_EXAMPLESDIR "examples")
endif()

set(INSTALL_EXAMPLEDIR "${INSTALL_EXAMPLESDIR}/webenginewidgets/maps")

find_package(Qt6 REQUIRED COMPONENTS Core Gui WebEngineWidgets)

qt_add_executable(maps
    main.cpp
    mainwindow.cpp mainwindow.h
)

set_target_properties(maps PROPERTIES
    WIN32_EXECUTABLE TRUE
    MACOSX_BUNDLE TRUE
)

target_link_libraries(maps PUBLIC
    Qt::Core
    Qt::Gui
    Qt::WebEngineWidgets
)

install(TARGETS maps
    RUNTIME DESTINATION "${INSTALL_EXAMPLEDIR}"
    BUNDLE DESTINATION "${INSTALL_EXAMPLEDIR}"
    LIBRARY DESTINATION "${INSTALL_EXAMPLEDIR}"
)
