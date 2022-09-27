set(PODULE_SOURCES
    src/aka16.c
    ../common/uart/scc2691.c
)

add_library(aka16 SHARED ${PODULE_SOURCES})
set_target_properties(aka16 PROPERTIES PREFIX "")
target_link_libraries(aka16 PRIVATE midi uart)
target_include_directories(aka16 PRIVATE ../../src)
