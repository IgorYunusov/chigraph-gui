cmake_minimum_required(VERSION 3.0)

project(chigraph-gui)

option(CG_USE_SYSTEM_CHIGRAPH "Try to find chigraph instead of building it here" OFF)

if (WIN32)
    set(GETTEXT_MSGMERGE_EXECUTABLE ${CMAKE_CURRENT_SOURCE_DIR}/third_party/gettext-win64/bin/msgmerge.exe CACHE FILEPATH "")
    set(GETTEXT_MSGFMT_EXECUTABLE ${CMAKE_CURRENT_SOURCE_DIR}/third_party/gettext-win64/bin/msgfmt.exe CACHE FILEPATH "")
endif()

set(BUILD_EXAMPLES OFF CACHE BOOL "")
add_subdirectory(third_party/nodeeditor)

if (CG_USE_SYSTEM_CHIGRAPH)
	find_package(Chigraph REQUIRED)
else()
	add_subdirectory(chigraph)
endif()
add_subdirectory(src)
