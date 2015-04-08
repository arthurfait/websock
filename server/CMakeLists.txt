cmake_minimum_required(VERSION 2.8)
project(services)
            add_definitions (-D_WEBSOCKETPP_CPP11_STL_)

        set (WEBSOCKETPP_PLATFORM_LIBS pthread rt)
        set (WEBSOCKETPP_PLATFORM_TSL_LIBS ssl crypto)

        set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
find_package( Boost REQUIRED COMPONENTS system thread )
include_directories( ${Boost_INCLUDE_DIRS} 
                    ../websocketpp)
add_executable( ${PROJECT_NAME} echo_server.cpp ) 

target_link_libraries( ${PROJECT_NAME} ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY} ${WEBSOCKETPP_PLATFORM_LIBS} )