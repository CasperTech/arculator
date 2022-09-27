set(ADC_SOURCES
    d7002c.c
)

add_library(adc STATIC ${ADC_SOURCES})
target_link_libraries(adc PRIVATE joystick)
target_include_directories(adc PRIVATE ../../../src)
target_include_directories(adc INTERFACE .)