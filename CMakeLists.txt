cmake_minimum_required(VERSION 3.14)

project(imgui LANGUAGES CXX)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

add_library(imgui STATIC
    imgui.cpp
    imgui_widgets.cpp
    imgui_demo.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_opengl3.cpp)

set_target_properties(imgui PROPERTIES FOLDER "ImGUI")
target_compile_definitions(imgui PRIVATE IMGUI_IMPL_OPENGL_LOADER_CUSTOM)

target_include_directories(imgui PUBLIC . backends)
target_link_libraries(imgui glfw glad::GL)

add_library(imgui::imgui ALIAS imgui)
