if(WIN32)
    list(APPEND CDROM_SOURCES
            cdrom-windows-ioctl.c
    )
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    list(APPEND CDROM_SOURCES
            cdrom-linux-ioctl.c
    )
else()
    list(APPEND CDROM_SOURCES
            cdrom-osx-ioctl.c
    )
endif()

add_library(cdrom STATIC ${CDROM_SOURCES})
target_include_directories(cdrom PRIVATE ../../../src)
target_include_directories(cdrom INTERFACE .)