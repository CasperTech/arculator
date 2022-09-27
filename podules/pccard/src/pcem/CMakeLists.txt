set(PCEM_SOURCES
        808x.c
        386.c
        386_common.c
        386_dynarec.c
        cpu.c
        cpu_tables.c
        diva.c
        dma.c
        io.c
        lpt.c
        mem.c
        pc.c
        pic.c
        pit.c
        scamp.c
        serial.c
        timer.c
        x86seg.c
        x87.c
        x87_timings.c
)

add_library(pcem STATIC ${PCEM_SOURCES} ${PCEM_HEADERS})
target_link_libraries(pcem PRIVATE libco)
target_include_directories(pcem PRIVATE ../../../../src)
target_include_directories(pcem INTERFACE .)