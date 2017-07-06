
CMAKE_MINIMUM_REQUIRED(VERSION 3.5)
PROJECT(beast-test CXX)

FIND_PACKAGE(Boost 1.58.0 REQUIRED COMPONENTS system coroutine context filesystem program_options thread)

ADD_SUBDIRECTORY(beast)

ADD_SUBDIRECTORY(src)

