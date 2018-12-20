ADD_LIBRARY(olm_license_generator_snippet STATIC
 	generate-license.cpp
)

target_link_libraries(
	olm_license_generator_snippet
 	olm_license_generator_lib
)

add_executable(
 olm_standard_license_test
 standard-license_test.cpp
)

target_link_libraries(
 olm_standard_license_test
 olm_licensepp_static
 olm_license_generator_snippet
 ${Boost_LIBRARIES}
)
#SET_TARGET_PROPERTIES(olm_standard_license_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( olm_standard_license_test boost_test boost_filesystem )

add_executable(
 olm_date_test
 date_test.cpp
)

target_link_libraries(
 olm_date_test
 olm_licensepp_static
 olm_license_generator_snippet
 ${Boost_LIBRARIES}
)
#SET_TARGET_PROPERTIES(olm_date_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( olm_date_test boost_test boost_filesystem )

add_executable(
 olm_volid_test
 volid_test.cpp
)

target_link_libraries(
 olm_volid_test
 olm_licensepp_static
 olm_license_generator_snippet
 ${Boost_LIBRARIES}
)

#SET_TARGET_PROPERTIES(olm_volid_test PROPERTIES LINK_SEARCH_START_STATIC ON)
#add_dependencies( olm_volid_test boost_test boost_filesystem )

ADD_TEST(NAME olm_standard_license_test COMMAND olm_standard_license_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
ADD_TEST(NAME olm_date_test COMMAND olm_date_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
ADD_TEST(NAME olm_volid_test COMMAND olm_volid_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})

