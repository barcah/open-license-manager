
if(MSVC)
ADD_LIBRARY(
    olm_tools_base STATIC
    CryptoHelper.cpp
    win/CryptoHelperWindows.cpp
)
else(MSVC)
ADD_LIBRARY(
    olm_tools_base STATIC
    CryptoHelper.cpp
    linux/CryptoHelperLinux.cpp
)
ENDIF(MSVC)

target_link_libraries(
     olm_tools_base
     ${EXTERNAL_LIBS}
)

install(TARGETS olm_tools_base ARCHIVE DESTINATION lib)
