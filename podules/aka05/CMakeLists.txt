set(PODULE_SOURCES
    src/aka05.c
)


add_library(aka05 SHARED ${PODULE_SOURCES})
set_target_properties(aka05 PROPERTIES PREFIX "")
target_include_directories(aka05 PRIVATE ../../src)
