CMAKE_MINIMUM_REQUIRED(VERSION 3.1)

PROJECT(kissnet_tests)

SET(CMAKE_CXX_STANDARD 17)

IF(MSVC)
  # Force to always compile with W4
  IF(CMAKE_CXX_FLAGS MATCHES "/W[0-4]")
    STRING(REGEX REPLACE "/W[0-4]" "/W4" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
  ELSE()
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /W4")
  ENDIF()
ELSEIF(CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
  # Update if necessary
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wno-long-long -pedantic ")
ENDIF()

INCLUDE_DIRECTORIES(..)

ADD_SUBDIRECTORY(simple_test)
ADD_SUBDIRECTORY(endpoint_test)
ADD_SUBDIRECTORY(socket_test)
ADD_SUBDIRECTORY(acceptor_test)
ADD_SUBDIRECTORY(error_handler_test)

