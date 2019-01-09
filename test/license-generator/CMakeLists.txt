
add_executable(
  licensecc_license_generator_test
  license-generator_test.cpp
)

target_link_libraries(
  licensecc_license_generator_test
  licensecc_license_generator_lib
  ${Boost_LIBRARIES}
)

#add_dependencies( licensecc_license_generator_test boost_test boost_filesystem )
#SET_TARGET_PROPERTIES(licensecc_license_generator_test PROPERTIES LINK_SEARCH_START_STATIC ON)
ADD_TEST(NAME licensecc_license_generator_test COMMAND licensecc_license_generator_test WORKING_DIRECTORY ${CMAKE_BINARY_DIR})
