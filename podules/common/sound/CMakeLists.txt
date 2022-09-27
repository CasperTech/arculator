set(SOUND_SOURCES
        sound_openal.c
)

if(WIN32)
    list(APPEND SOUND_SOURCES
        sound_wavein.c
    )
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    list(APPEND SOUND_SOURCES
        sound_alsain.c
    )
else()
    list(APPEND SOUND_SOURCES
        sound_in_null.c
    )
endif()

add_library(sound STATIC ${SOUND_SOURCES})
target_link_libraries(sound PRIVATE openal)
target_include_directories(sound PRIVATE ../../../src)
target_include_directories(sound INTERFACE .)