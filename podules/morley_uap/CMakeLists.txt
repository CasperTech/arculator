set(PODULE_SOURCES
    src/morley_uap.c
)

add_library(morley_uap SHARED ${PODULE_SOURCES})
set_target_properties(morley_uap PROPERTIES PREFIX "")
target_include_directories(morley_uap PRIVATE ../../src ../common/misc ../common/adc ../common/joystick)