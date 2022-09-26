set(PODULE_SOURCES
    src/midimax.c
)

set(PODULE_HEADERS
    src/midimax.h
)

add_library(midimax SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(midimax PROPERTIES PREFIX "")
target_include_directories(midimax PRIVATE ../../src ../common/uart ../common/midi)
