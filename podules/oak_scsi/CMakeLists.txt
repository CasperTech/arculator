set(PODULE_SOURCES
    src/oak_scsi.c
    src/ncr5380.c
)

set(PODULE_HEADERS
    src/oak_scsi.h
    src/ncr5380.h
)

add_library(oak_scsi SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(oak_scsi PROPERTIES PREFIX "")
target_link_libraries(oak_scsi PRIVATE cdrom scsi sound eeprom)
target_include_directories(oak_scsi PRIVATE ../../src)