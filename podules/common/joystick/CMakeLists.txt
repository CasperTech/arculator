set(JOYSTICK_SOURCES
        joystick_sdl2.c
)

find_package(SDL2 REQUIRED)

add_library(joystick STATIC ${JOYSTICK_SOURCES})
target_link_libraries(joystick PRIVATE ${SDL2_LIBRARIES} cdrom)
target_include_directories(joystick PRIVATE ../../../src ${SDL2_INCLUDE_DIRS})
target_include_directories(joystick INTERFACE .)