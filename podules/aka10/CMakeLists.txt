set(PODULE_SOURCES
    src/aka10.c
    ../common/adc/d7002c.c
    ../common/misc/6522.c
    ../common/joystick/joystick_sdl2.c
)

add_library(aka10 SHARED ${PODULE_SOURCES})
set_target_properties(aka10 PROPERTIES PREFIX "")
target_link_libraries(aka10 PRIVATE uart midi joystick)
target_include_directories(aka10 PRIVATE ../../src ../common/misc ../common/adc)
