set(PODULE_SOURCES
    src/pccard_podule.c
)

set(PODULE_HEADERS
    src/pccard_podule.h
)

add_library(pccard SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(pccard PROPERTIES PREFIX "")

add_subdirectory(./src/libco)
add_subdirectory(./src/pcem)

target_link_libraries(pccard PRIVATE pcem)
target_include_directories(pccard PRIVATE ../../src)