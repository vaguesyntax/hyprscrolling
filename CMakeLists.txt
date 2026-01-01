cmake_minimum_required(VERSION 3.27)
project(hyprland-plugins
    DESCRIPTION "hyprscrolling plugin for hyprland"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(hyprscrolling)
