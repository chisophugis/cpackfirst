# Notes


Basic usage seems simple.
https://cmake.org/Wiki/CMake:Packaging_With_CPack

CPack has multiple generators. It has deb an rpm which is nice. Also
NSIS installer.
https://cmake.org/Wiki/CMake:CPackPackageGenerators

CMake's "install" capabilities seem pretty comprehensive:
https://cmake.org/cmake/help/v3.2/command/install.html


Default install prefix from CMakeCache.txt:
    //Install path prefix, prepended onto install directories.
    CMAKE_INSTALL_PREFIX:PATH=/usr/local


Interesting CPACK_PACKAGE_EXECUTABLES for e.g. adding start menu
components.


Interesting that this uses ./usr/ instead of the CMAKE_INSTALL_PREFIX.
I guess it makes sense: if you are making a real package, you don't
want to install in an arbitrary place but actually want to be in usr/.
    sean:~/pg/cpackfirst/build % dpkg -c Project-0.1.1-Linux.deb
    drwxrwxr-x root/root         0 2016-06-25 05:01 ./usr/
    drwxrwxr-x root/root         0 2016-06-25 05:01 ./usr/bin/
    -rwxr-xr-x root/root      7416 2016-06-25 05:00 ./usr/bin/main

    sean:~/pg/cpackfirst/build % sudo dpkg -i Project-0.1.1-Linux.deb
    [sudo] password for sean: 
    Selecting previously unselected package project.
    (Reading database ... 584545 files and directories currently installed.)
    Preparing to unpack Project-0.1.1-Linux.deb ...
    Unpacking project (0.1.1) ...
    Setting up project (0.1.1) ...

    sean:~/pg/cpackfirst/build % main
    Hello world!


Success!
