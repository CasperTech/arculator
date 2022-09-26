set(PODULE_SOURCES
    src/ad1848.c
    src/am7202a.c
    src/lark.c
)

set(PODULE_HEADERS
    src/ad1848.h
    src/am7202a.h
    src/lark.h
)

add_library(lark SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(lark PROPERTIES PREFIX "")
target_include_directories(lark PRIVATE ../../src ../common/uart ../common/midi ../common/sound)
