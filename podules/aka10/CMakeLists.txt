set(PODULE_SOURCES
    src/aka10.c
)

add_library(aka10 SHARED ${PODULE_SOURCES})
set_target_properties(aka10 PROPERTIES PREFIX "")
target_include_directories(aka10 PRIVATE ../../src ../common/misc ../common/uart ../common/adc ../common/joystick ../common/midi)
