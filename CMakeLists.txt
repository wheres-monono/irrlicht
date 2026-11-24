cmake_minimum_required(VERSION 4.2)
project(Irrlicht
	VERSION 1.9.0
	LANGUAGES C CXX
)
include(GNUInstallDirs)
option(BUILD_SHARED_LIBS "Build as a shared library" OFF)
option(IRR_PROFILE "Compile with -pg (gprof)" OFF)
option(IRR_USE_DX9 "Build the Direct3D 9 driver" OFF)
option(IRR_LEGACY_OUTPUT_DIRS "Write the build to lib/<system>/ or bin/Win32-gcc/" OFF)
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
	set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
	set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS Debug Release RelWithDebInfo MinSizeRel)
endif()
if(APPLE)
	enable_language(OBJCXX)
endif()
add_subdirectory(source)
