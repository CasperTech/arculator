set(PODULE_SOURCES
    src/mitsumi.c
    src/ultimatecdrom.c
)

set(PODULE_HEADERS
    src/mitsumi.h
    src/ultimatecdrom.c
)

add_library(ultimatecdrom SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(ultimatecdrom PROPERTIES PREFIX "")
target_include_directories(ultimatecdrom PRIVATE ../../src ../common/cdrom ../common/sound)