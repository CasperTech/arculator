cmake_minimum_required (VERSION 2.8.11)
project (arculator)

set(CMAKE_CXX_FLAGS "-fpermissive")

set(SOURCES
    src/82c711.c
    src/82c711_fdc.c
    src/arm.c
    src/bmu.c
    src/cmos.c
    src/colourcard.c
    src/config.c
    src/cp15.c
    src/ddnoise.c
    src/debugger.c
    src/debugger_swis.c
    src/disc.c
    src/disc_adf.c
    src/disc_apd.c
    src/disc_fdi.c
    src/disc_hfe.c
    src/disc_jfd.c
    src/disc_mfm_common.c
    src/ds2401.c
    src/eterna.c
    src/fdi2raw.c
    src/fpa.c
    src/g16.c
    src/g332.c
    src/hostfs.c
    src/ide.c
    src/ide_a3in.c
    src/ide_config.c
    src/ide_idea.c
    src/ide_riscdev.c
    src/ide_zidefs.c
    src/ide_zidefs_a3k.c
    src/input_sdl2.c
    src/ioc.c
    src/ioeb.c
    src/joystick.c
    src/keyboard.c
    src/lc.c
    src/main.c
    src/mem.c
    src/memc.c
    src/podules.c
    src/printer.c
    src/riscdev_hdfc.c
    src/romload.c
    src/sound.c
    src/soundopenal.c
    src/st506.c
    src/st506_akd52.c
    src/timer.c
    src/vidc.c
    src/video_sdl2.c
    src/wd1770.c
    src/wx-app.cc
    src/wx-config.cc
    src/wx-config_sel.cc
    src/wx-hd_conf.cc
    src/wx-console.cc
    src/wx-hd_new.cc
    src/wx-joystick-config.cc
    src/wx-main.cc
    src/wx-podule-config.cc
    src/wx-resources.cc
    src/wx-sdl2.c
    src/wx-sdl2-joystick.c
)

set(HEADERS
    src/82c711.h
    src/82c711_fdc.h
    src/arm.h
    src/bmu.h
    src/cmos.h
    src/colourcard.h
    src/config.h
    src/cp15.h
    src/ddnoise.h
    src/debugger.h
    src/debugger_swis.h
    src/disc.h
    src/disc_adf.h
    src/disc_apd.h
    src/disc_fdi.h
    src/disc_hfe.h
    src/disc_jfd.h
    src/disc_mfm_common.h
    src/ds2401.h
    src/eterna.h
    src/fdi2raw.h
    src/fpa.h
    src/g16.h
    src/g332.h
    src/hostfs.h
    src/ide.h
    src/ide_a3in.h
    src/ide_config.h
    src/ide_idea.h
    src/ide_riscdev.h
    src/ide_zidefs.h
    src/ide_zidefs_a3k.h
    src/ioc.h
    src/ioeb.h
    src/joystick.h
    src/keyboard.h
    src/lc.h
    src/mem.h
    src/memc.h
    src/podules.h
    src/printer.h
    src/riscdev_hdfc.h
    src/romload.h
    src/sound.h
    src/soundopenal.h
    src/st506.h
    src/st506_akd52.h
    src/timer.h
    src/vidc.h
    src/video_sdl2.h
    src/wd1770.h
    src/wx-app.h
    src/wx-config.h
    src/wx-config_sel.h
    src/wx-hd_conf.h
    src/wx-console.h
    src/wx-hd_new.h
    src/wx-joystick-config.h
    src/wx-podule-config.h
)

if(WIN32)
    list(APPEND SOURCES src/wx-win32.c)
    list(APPEND SOURCES src/hostfs-win.c)
    list(APPEND SOURCES src/podules-win.c)
else()
    if(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
        list(APPEND SOURCES src/podules-linux.c)
    else()
        list(APPEND SOURCES src/podules-macosx.c)
    endif()
    list(APPEND SOURCES src/hostfs-unix.c)
endif(WIN32)

find_package(wxWidgets REQUIRED COMPONENTS core xrc)
include(${wxWidgets_USE_FILE})
find_package(SDL2 REQUIRED)

add_executable (arculator ${SOURCES} ${HEADERS})
target_include_directories(arculator PRIVATE ${SDL2_INCLUDE_DIRS})
target_link_libraries(arculator PRIVATE ${wxWidgets_LIBRARIES} asound openal pthread z ${SDL2_LIBRARIES} X11)

MACRO(subdirlist result curdir)
    FILE(GLOB children RELATIVE ${curdir} ${curdir}/*)
    SET(dirlist "")
    foreach(child ${children})
        if(IS_DIRECTORY ${curdir}/${child})
            LIST(APPEND dirlist ${child})
        endif()
    endforeach()
    SET(${result} ${dirlist})
endmacro()

subdirlist(SUBDIRS ${CMAKE_CURRENT_SOURCE_DIR}/podules)

foreach(subdir ${SUBDIRS})
    add_subdirectory(podules/${subdir})
endforeach()

add_custom_command(TARGET arculator  POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                   ${CMAKE_CURRENT_SOURCE_DIR}/roms
                   ${CMAKE_CURRENT_BINARY_DIR}/roms)

add_custom_command(TARGET arculator  POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                   ${CMAKE_CURRENT_SOURCE_DIR}/configs
                   ${CMAKE_CURRENT_BINARY_DIR}/configs)

add_custom_command(TARGET arculator  POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                   ${CMAKE_CURRENT_SOURCE_DIR}/cmos
                   ${CMAKE_CURRENT_BINARY_DIR}/cmos)

add_custom_command(TARGET arculator  POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                   ${CMAKE_CURRENT_SOURCE_DIR}/ddnoise
                   ${CMAKE_CURRENT_BINARY_DIR}/ddnoise)

add_custom_command(TARGET arculator  POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                   ${CMAKE_CURRENT_SOURCE_DIR}/hostfs
                   ${CMAKE_CURRENT_BINARY_DIR}/hostfs)
