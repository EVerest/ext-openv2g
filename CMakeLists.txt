#
# Copyright (c) 2017 Michael Heimpold <mhei@heimpold.de>
#

cmake_minimum_required(VERSION 3.14)

project(openv2g
    VERSION 0.9.5
    DESCRIPTION "OpenV2G library for ISO IEC 15118 protocol"
    LANGUAGES C
)

find_package(everest-cmake 0.1 REQUIRED
    PATHS ../everest-cmake
)

# options
option(OPENV2G_INSTALL "Install the library (shared data might be installed anyway)" ${EVC_MAIN_PROJECT})
set(SOVERSION 1)

# logging library
add_subdirectory(lib)

install(
    TARGETS openv2g
    EXPORT openv2g-targets
    LIBRARY
)

# packaging
if (OPENV2G_INSTALL)
    install(
        DIRECTORY include/
        TYPE INCLUDE
    )

    evc_setup_package(
        NAME everest-openv2g
        NAMESPACE everest
        EXPORT openv2g-targets
    )
endif()
