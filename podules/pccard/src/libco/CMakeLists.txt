set(LIBCO_SOURCES
    libco.c
)

add_library(libco STATIC ${LIBCO_SOURCES})
target_include_directories(libco INTERFACE .)