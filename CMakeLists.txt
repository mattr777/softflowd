cmake_minimum_required(VERSION 3.3)
project(softflowd)

add_definitions(-DFLOW_SPLAY)
add_definitions(-DEXPIRY_RB)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES
    closefrom.c
    common.h
    convtime.c
    convtime.h
    daemon.c
    freelist.c
    freelist.h
    ipfix.c
    log.c
    log.h
    netflow1.c
    netflow5.c
    netflow9.c
    softflowd.c
    softflowd.h
    strlcat.c
    strlcpy.c
    sys-tree.h
    treetype.h)

add_executable(softflowd ${SOURCE_FILES})

target_link_libraries (softflowd pcap)

#sudo ./softflowd -i eth0 -v 10 -D -n 127.0.0.1:2055 -t tcp=60 -t udp=60
#sudo bin/logstash -f /etc/logstash/conf.d/logstash-netflow.conf --debug