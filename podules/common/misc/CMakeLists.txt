set(MISC_SOURCES
    6522.c
)

add_library(misc STATIC ${MISC_SOURCES})
target_include_directories(misc PRIVATE ../../../src)
target_include_directories(misc INTERFACE .)