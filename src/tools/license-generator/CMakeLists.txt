
include_directories(${Boost_INCLUDE_DIR})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
link_directories ( ${Boost_LIBRARY_DIR} )


ADD_LIBRARY(
    olm_license_generator_lib STATIC
    license-generator.cpp
)

target_link_libraries(
     olm_license_generator_lib
     olm_tools_base
     olm_licensepp_static
	 $<$<CONFIG:Debug>:${Boost_PROGRAM_OPTIONS_LIBRARY_DEBUG}>
     $<$<NOT:$<CONFIG:Debug>>:${Boost_PROGRAM_OPTIONS_LIBRARY_RELEASE}>	 
	 $<$<CONFIG:Debug>:${Boost_SYSTEM_LIBRARY_DEBUG}>
     $<$<NOT:$<CONFIG:Debug>>:${Boost_SYSTEM_LIBRARY_RELEASE}>	 
     ${EXTERNAL_LIBS}
)

add_executable(
 olm_license_generator
 license-generator-main.cpp
)

target_link_libraries(
    olm_license_generator
    olm_license_generator_lib
)
add_dependencies( olm_license_generator private_key )

install(TARGETS olm_license_generator RUNTIME DESTINATION tools/olm)

#SET_TARGET_PROPERTIES(olm_license_generator PROPERTIES LINK_SEARCH_START_STATIC ON)
#SET_TARGET_PROPERTIES(olm_license_generator PROPERTIES LINK_SEARCH_END_STATIC ON)
