
add_executable(
 olm_license_generator_test
 license-generator_test.cpp
)

target_link_libraries(
 olm_license_generator_test
 olm_license_generator_lib
  ${Boost_LIBRARIES}
)

#add_dependencies( olm_license_generator_test boost_test boost_filesystem )
#SET_TARGET_PROPERTIES(olm_license_generator_test PROPERTIES LINK_SEARCH_START_STATIC ON)
ADD_TEST(NAME olm_license_generator_test COMMAND olm_license_generator_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
