add_subdirectory("os")
add_subdirectory("base")
add_subdirectory("ini")

ADD_LIBRARY(licensecc_static STATIC
    licensecc.cpp
    LicenseReader.cpp
    pc-identifiers.c
)

target_link_libraries(
    licensecc_static
    licensecc_ini
    licensecc_os
)

install(TARGETS licensecc_static ARCHIVE DESTINATION lib)
install(FILES api/datatypes.h api/licensecc.h DESTINATION include/licensecc/api)
install(FILES base/base.h DESTINATION include/licensecc/base)
install(FILES pc-identifiers.h DESTINATION include/licensecc)
