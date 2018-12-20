IF(WIN32)
    ADD_LIBRARY(olm_os STATIC
        os.c
        os-win.c)
ELSE(WIN32)
    ADD_LIBRARY(olm_os STATIC
        os.c
        os-linux.c
        network_id.c)
ENDIF(WIN32)

target_link_libraries(
     olm_os
     olm_base
     ${EXTERNAL_LIBS}
)

install(TARGETS olm_os ARCHIVE DESTINATION lib)
