set(EEPROM_SOURCES
    93c06.c
)

add_library(eeprom STATIC ${EEPROM_SOURCES})
target_include_directories(eeprom PRIVATE ../../../src)
target_include_directories(eeprom INTERFACE .)