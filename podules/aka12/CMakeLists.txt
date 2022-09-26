set(PODULE_SOURCES
    src/aka12.c
)

set(PODULE_HEADERS
    src/aka12.h
)

add_library(aka12 SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(aka12 PROPERTIES PREFIX "")
target_include_directories(aka12 PRIVATE ../../src  ../common/misc ../common/uart ../common/midi)
