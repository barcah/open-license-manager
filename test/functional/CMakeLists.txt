ADD_LIBRARY(licensecc_license_generator_snippet STATIC
 	generate-license.cpp
)

target_link_libraries(
	licensecc_license_generator_snippet
	licensecc_license_generator_lib
)

add_executable(
	licensecc_standard_license_test
 	standard-license_test.cpp
)

target_link_libraries(
	licensecc_standard_license_test
	licensecc_static
	licensecc_license_generator_snippet
 ${Boost_LIBRARIES}
)
#SET_TARGET_PROPERTIES(licensecc_standard_license_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( licensecc_standard_license_test boost_test boost_filesystem )

add_executable(
	licensecc_date_test
 	date_test.cpp
)

target_link_libraries(
	licensecc_date_test
	licensecc_static
	licensecc_license_generator_snippet
 	${Boost_LIBRARIES}
)
#SET_TARGET_PROPERTIES(licensecc_date_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( licensecc_date_test boost_test boost_filesystem )

add_executable(
	licensecc_volid_test
 	volid_test.cpp
)

target_link_libraries(
	licensecc_volid_test
	licensecc_static
	licensecc_license_generator_snippet
 	${Boost_LIBRARIES}
)

#SET_TARGET_PROPERTIES(licensecc_volid_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( licensecc_volid_test boost_test boost_filesystem )

ADD_TEST(NAME licensecc_standard_license_test COMMAND licensecc_standard_license_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
ADD_TEST(NAME licensecc_date_test COMMAND licensecc_date_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
ADD_TEST(NAME licensecc_volid_test COMMAND licensecc_volid_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})

