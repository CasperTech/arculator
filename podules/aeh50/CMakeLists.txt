set(PODULE_SOURCES
    src/aeh50.c
)

set(PODULE_HEADERS
    src/aeh50.h
)

add_library(aeh50 SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(aeh50 PROPERTIES PREFIX "")
target_include_directories(aeh50 PRIVATE ../../src ../common/net)
