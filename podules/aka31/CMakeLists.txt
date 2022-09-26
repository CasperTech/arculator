set(PODULE_SOURCES
    src/aka31.c
    src/d71071l.c
    src/wd33c93a.c
)

set(PODULE_HEADERS
    src/aka31.h
    src/d71071l.h
    src/wd33c93a.h
)

add_library(aka31 SHARED ${PODULE_SOURCES} ${PODULE_HEADERS})
set_target_properties(aka31 PROPERTIES PREFIX "")
target_include_directories(aka31 PRIVATE ../../src ../common/scsi ../common/cdrom ../common/sound)
