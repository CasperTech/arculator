# This module appears to require windows
if(WIN32)
set(PODULE_SOURCES
    src/aeh54.c
    src/seeq8005.c
    ../common/net/net_slirp.c
)

set(PODULE_HEADERS
    src/aeh54.h
    src/seeq8005.h
)

add_library(aeh54 SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
target_link_libraries(aeh54 PRIVATE slirp) # Iphlpapi ws2_32
set_target_properties(aeh54 PROPERTIES PREFIX "")
target_include_directories(aeh54 PRIVATE ../../src ../common/net)
endif(WIN32)