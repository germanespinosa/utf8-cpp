cmake_minimum_required(VERSION 3.13)
project(utf8-cpp CXX)

add_library(utf8-cpp INTERFACE)

target_include_directories(utf8-cpp SYSTEM INTERFACE
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>)

export(TARGETS utf8-cpp FILE Utf8CppConfig.cmake)

###
### LIBRARY INSTALLATION
###

include(GNUInstallDirs)

install(TARGETS utf8-cpp EXPORT Utf8-cppConfig
        ARCHIVE  DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY  DESTINATION ${CMAKE_INSTALL_LIBDIR}
        RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR})

install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(EXPORT Utf8-cppConfig
        DESTINATION ${CMAKE_INSTALL_DATADIR}/cmake/Utf8-cpp)

export(TARGETS utf8-cpp FILE Utf8-cppConfig.cmake)