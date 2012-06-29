cmake_minimum_required (VERSION 2.8)
project (jsoncpp)

add_library (SharedTarget SHARED src/lib_json/json_reader.cpp src/lib_json/json_value.cpp src/lib_json/json_writer.cpp)
add_library (StaticTarget STATIC src/lib_json/json_reader.cpp src/lib_json/json_value.cpp src/lib_json/json_writer.cpp)

set_target_properties(SharedTarget PROPERTIES OUTPUT_NAME jsoncpp)
set_target_properties(StaticTarget PROPERTIES OUTPUT_NAME jsoncpp)

INSTALL(TARGETS SharedTarget DESTINATION lib)
INSTALL(TARGETS StaticTarget DESTINATION lib)

INSTALL(FILES json/autolink.h  include/json/features.h  include/json/json.h   include/json/value.h include/json/config.h include/json/forwards.h  include/json/reader.h  include/json/writer.h  DESTINATION include/json)

SET(CXXSTANDARD "-Iinclude")
SET(CMAKE_CXX_FLAGS ${CXXSTANDARD})

MESSAGE(STATUS "<<< Gentoo configuration >>>
Build type      ${CMAKE_BUILD_TYPE}
Install path    ${CMAKE_INSTALL_PREFIX}
Compiler flags:
C               ${CMAKE_C_FLAGS}
C++             ${CMAKE_CXX_FLAGS}
Linker flags:
Executable      ${CMAKE_EXE_LINKER_FLAGS}
Module          ${CMAKE_MODULE_LINKER_FLAGS}
Shared          ${CMAKE_SHARED_LINKER_FLAGS}\n")
