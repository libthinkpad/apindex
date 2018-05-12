cmake_minimum_required(VERSION 2.6)

project(apindex NONE)

set(CPACK_PACKAGE_VENDOR "Ognjen Galic")
set(CPACK_PACKAGE_VERSION_MAJOR 2)
set(CPACK_PACKAGE_VERSION_MINOR 2)
set(CPACK_SOURCE_PACKAGE_FILE_NAME ${PROJECT_NAME}-${CPACK_PACKAGE_VERSION_MAJOR}.${CPACK_PACKAGE_VERSION_MINOR})
set(CPACK_SOURCE_GENERATOR "TGZ")
set(CPACK_SOURCE_IGNORE_FILES ".git;.idea;CMakeLists.txt.user;build;test_data")

configure_file(apindex.py apindex)

install(DIRECTORY share/apindex/
        DESTINATION ${CMAKE_INSTALL_PREFIX}/share/apindex
        PATTERN "share/apindex/*")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/apindex
        DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
        PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ
                    GROUP_EXECUTE GROUP_READ
                    WORLD_EXECUTE WORLD_READ)

include(CPack)
