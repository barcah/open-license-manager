IF(WIN32)
    ADD_LIBRARY(licensecc_os STATIC
        os.c
        os-win.c)
ELSE(WIN32)
    ADD_LIBRARY(licensecc_os STATIC
        os.c
        os-linux.c
        network_id.c)
ENDIF(WIN32)

target_link_libraries(
    licensecc_os
    licensecc_base
    ${EXTERNAL_LIBS}
)

install(TARGETS licensecc_os ARCHIVE DESTINATION lib)
