cmake_minimum_required(VERSION 3.0)
project(
    DLSS
    VERSION 2.4.0
)

set(DLSS_VERSION_STRING "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}.${PROJECT_VERSION_PATCH}")
set(DLSS_ARCHIVE_NAME "libnvsdk_ngx.a")
set(DLSS_SHARED_LIB_NAME "libnvidia-ngx-dlss.so.${DLSS_VERSION_STRING}")
list(APPEND DLSS_LINK_LIBRARIES ld stdc++)

configure_file(
    DLSSConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/DLSSConfig.cmake
    @ONLY
)

install(
    FILES
        "${CMAKE_CURRENT_LIST_DIR}/lib/Linux_x86_64/${DLSS_ARCHIVE_NAME}"
        "${CMAKE_CURRENT_LIST_DIR}/lib/Linux_x86_64/rel/${DLSS_SHARED_LIB_NAME}"
    DESTINATION lib
)

install(
    DIRECTORY "${CMAKE_CURRENT_LIST_DIR}/include/"
    DESTINATION include
)

install(
    FILES
        "${CMAKE_CURRENT_BINARY_DIR}/DLSSConfig.cmake"
    DESTINATION lib/cmake/DLSS
)
