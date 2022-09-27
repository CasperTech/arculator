set(SLIRP_SOURCES
        bootp.c
        cksum.c
        debug.c
        if.c
        ip_icmp.c
        ip_input.c
        ip_output.c
        mbuf.c
        misc.c
        queue.c
        sbuf.c
        slirp.c
        socket.c
        tcp_input.c
        tcp_output.c
        tcp_subr.c
        tcp_timer.c
        tftp.c
        udp.c
)

add_library(slirp STATIC ${SLIRP_SOURCES})

if(WIN32)
target_link_libraries(slirp PRIVATE Iphlpapi ws2_32)
endif()

