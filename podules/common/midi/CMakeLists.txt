if(WIN32)
    list(APPEND MIDI_SOURCES
            midi_win.c
    )
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    list(APPEND MIDI_SOURCES
            midi_alsa.c
    )
else()
    list(APPEND MIDI_SOURCES
        midi_null.c
    )
endif(WIN32)

add_library(midi STATIC ${MIDI_SOURCES})
target_include_directories(midi PRIVATE ../../../src)
target_include_directories(midi INTERFACE .)
if(WIN32)
    target_link_libraries(midi PRIVATE winmm)
endif()