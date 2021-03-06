add_executable(
  licensecc_bootstrap
  bootstrap.cpp
)

SET_TARGET_PROPERTIES(licensecc_bootstrap PROPERTIES LINK_SEARCH_START_STATIC ON)
SET_TARGET_PROPERTIES(licensecc_bootstrap PROPERTIES LINK_SEARCH_END_STATIC OFF)

target_link_libraries(
  licensecc_bootstrap
  licensecc_tools_base
  ${EXTERNAL_LIBS}
)

# add the command to generate the source code

if(MINGW)
add_custom_command (
  OUTPUT "${CMAKE_BINARY_DIR}/private-key.h" "${CMAKE_BINARY_DIR}/public-key.h"
  COMMAND ./licensecc_bootstrap.exe "${CMAKE_BINARY_DIR}/private-key.h" "${CMAKE_BINARY_DIR}/public-key.h"
  WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
  DEPENDS licensecc_bootstrap)
else(MINGW)
add_custom_command (
  OUTPUT "${CMAKE_BINARY_DIR}/private-key.h" "${CMAKE_BINARY_DIR}/public-key.h"
  COMMAND licensecc_bootstrap "${CMAKE_BINARY_DIR}/private-key.h" "${CMAKE_BINARY_DIR}/public-key.h"
  WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
  DEPENDS licensecc_bootstrap)
endif(MINGW)


add_custom_target(private_key DEPENDS "${CMAKE_BINARY_DIR}/private-key.h")
add_custom_target(public_key DEPENDS "${CMAKE_BINARY_DIR}/public-key.h")


# add the command to generate the source code
#add_custom_command (
#  OUTPUT "${CMAKE_BINARY_DIR}/public-key.h" 
#  COMMAND bootstrap derive_public "${CMAKE_CURRENT_SOURCE_DIR}/../license-generator/private-key.h" "${CMAKE_BINARY_DIR}/public-key.h"
#  DEPENDS bootstrap private_key
#)
#add_custom_target(public_key DEPENDS "${CMAKE_BINARY_DIR}/public-key.h")

install(TARGETS licensecc_bootstrap RUNTIME DESTINATION tools/licensecc)