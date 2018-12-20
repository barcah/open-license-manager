add_subdirectory("os")
add_subdirectory("base")
add_subdirectory("ini")

ADD_LIBRARY(olm_licensepp_static STATIC
    licensepp.cpp
    LicenseReader.cpp
    pc-identifiers.c
)

target_link_libraries(
     olm_licensepp_static
     olm_ini
     olm_os
)

install(TARGETS olm_licensepp_static ARCHIVE DESTINATION lib)
install(FILES api/datatypes.h api/licensepp.h DESTINATION include/olm/api)
install(FILES base/base.h DESTINATION include/olm/base)
install(FILES pc-identifiers.h DESTINATION include/olm)
