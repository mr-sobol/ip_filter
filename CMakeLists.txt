cmake_minimum_required(VERSION 3.5)
if(NOT DEFINED ENV{TRAVIS_BUILD_NUMBER})
    set(ENV{TRAVIS_BUILD_NUMBER} 10000)
endif()

project(ip_filter VERSION 0.0.$ENV{TRAVIS_BUILD_NUMBER})


set(CMAKE_CXX_STANDARD 14)

add_executable(ip_filter_main main.cpp)

install(TARGETS ip_filter_main RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)

set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

set(CPACK_PACKAGE_CONTACT mr_sobol@ukr.net)

set(CPACK_DEBIAN_PACKAGE_SHLIBDEPS ON)

include(CPack)