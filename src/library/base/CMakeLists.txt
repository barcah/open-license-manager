ADD_LIBRARY(olm_base STATIC
    EventRegistry.cpp
    StringUtils.cpp
    logger.c
)

add_dependencies( olm_base public_key )

install(TARGETS olm_base ARCHIVE DESTINATION lib)
