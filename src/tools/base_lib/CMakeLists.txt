
if(MSVC)
ADD_LIBRARY(
    licensecc_tools_base STATIC
    CryptoHelper.cpp
    win/CryptoHelperWindows.cpp
)
else(MSVC)
ADD_LIBRARY(
    licensecc_tools_base STATIC
    CryptoHelper.cpp
    linux/CryptoHelperLinux.cpp
)
ENDIF(MSVC)

target_link_libraries(
    licensecc_tools_base
     ${EXTERNAL_LIBS}
)

install(TARGETS licensecc_tools_base ARCHIVE DESTINATION lib)
install(FILES CryptoHelper.h DESTINATION include/licensecc/crypto)