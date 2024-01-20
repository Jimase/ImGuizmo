cmake_minimum_required(VERSION 3.16)

project(vcpkg-example)

add_definitions(-DSTB_IMAGE_IMPLEMENTATION)
# find_path(STB_INCLUDE_DIRS "stb.h")

find_package(Stb REQUIRED) # 这将设置 Stb_INCLUDE_DIR

# Find the required packages
find_package(imgui CONFIG REQUIRED)
find_package(imguizmo CONFIG REQUIRED)

add_executable(example-app)

target_sources(example-app PRIVATE main.cpp)

target_compile_options(example-app PRIVATE "/std:c++17")

# Include the directories
target_include_directories(example-app PRIVATE ${Stb_INCLUDE_DIR}) # 使用 ${Stb_INCLUDE_DIR}

# Link the libraries
target_link_libraries(example-app PRIVATE
    imgui::imgui
    imguizmo::imguizmo
)
