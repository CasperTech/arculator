set(UART_SOURCES
        6850.c
        16550.c
        scc2691.c
)

add_library(uart STATIC ${UART_SOURCES})
target_include_directories(uart PRIVATE ../../../src)
target_include_directories(uart INTERFACE .)