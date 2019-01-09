ADD_LIBRARY(licensecc_base STATIC
    EventRegistry.cpp
    StringUtils.cpp
    logger.c
)

add_dependencies( licensecc_base public_key )

install(TARGETS licensecc_base ARCHIVE DESTINATION lib)
