cmake_minimum_required(VERSION 3.9)

project(siam-trackers LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 14)

set(CMAKE_PREFIX_PATH /home/xlsun/libtorch/share/cmake)
find_package(OpenCV REQUIRED)
find_package(Torch REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS}")

add_executable(${PROJECT_NAME} main.cpp)

target_sources(${PROJECT_NAME} PRIVATE Tracker.cpp TrackerSiamMask.cpp TrackerSiamRPNPP.cpp)

target_link_libraries(${PROJECT_NAME} PRIVATE ${OpenCV_LIBS} ${TORCH_LIBRARIES})
