
include_directories(${Boost_INCLUDE_DIR})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
link_directories ( ${Boost_LIBRARY_DIR} )


ADD_LIBRARY(
    licensecc_license_generator_lib STATIC
    license-generator.cpp
)

target_link_libraries(
    licensecc_license_generator_lib
    licensecc_tools_base
    licensecc_static
	 $<$<CONFIG:Debug>:${Boost_PROGRAM_OPTIONS_LIBRARY_DEBUG}>
     $<$<NOT:$<CONFIG:Debug>>:${Boost_PROGRAM_OPTIONS_LIBRARY_RELEASE}>	 
	 $<$<CONFIG:Debug>:${Boost_SYSTEM_LIBRARY_DEBUG}>
     $<$<NOT:$<CONFIG:Debug>>:${Boost_SYSTEM_LIBRARY_RELEASE}>	 
     ${EXTERNAL_LIBS}
)

add_executable(
    licensecc_license_generator
    license-generator-main.cpp
)

target_link_libraries(
    licensecc_license_generator
    licensecc_license_generator_lib
)
add_dependencies( licensecc_license_generator private_key )

install(TARGETS licensecc_license_generator RUNTIME DESTINATION tools/licensecc)

#SET_TARGET_PROPERTIES(licensecc_license_generator PROPERTIES LINK_SEARCH_START_STATIC ON)
#SET_TARGET_PROPERTIES(licensecc_license_generator PROPERTIES LINK_SEARCH_END_STATIC ON)
