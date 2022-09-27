set(SCSI_SOURCES
        hdd_file.c
        scsi.c
        scsi_cd.c
        scsi_config.c
        scsi_hd.c
)

add_library(scsi STATIC ${SCSI_SOURCES})
target_link_libraries(scsi PRIVATE cdrom)
target_include_directories(scsi PRIVATE ../../../src)
target_include_directories(scsi INTERFACE .)