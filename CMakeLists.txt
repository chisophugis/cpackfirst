# CMake told me to put this here. Lower probably works too.
cmake_minimum_required(VERSION 3.2)

add_executable(main main.cpp)

# This enables `ninja install` which will install the binary `main` to
# the location `${CMAKE_INSTALL_PREFIX}/bin/main`.
install(TARGETS main
        RUNTIME DESTINATION bin/)

set(CPACK_GENERATOR "DEB")
set(CPACK_PACKAGE_CONTACT "chisophugis@gmail.com")
include(CPack)
