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

Now let's try uninstalling (the default package name for the debian
file seems to be `project` (dpkg mentioned this when installing it)).

    sean:~/pg/cpackfirst/build % sudo dpkg -r Project-0.1.1-Linux.deb
    dpkg: error: you must specify packages by their own names, not by quoting the names of the files they come in

    Type dpkg --help for help about installing and deinstalling packages [*];
    Use 'apt' or 'aptitude' for user-friendly package management;
    Type dpkg -Dhelp for a list of dpkg debug flag values;
    Type dpkg --force-help for a list of forcing options;
    Type dpkg-deb --help for help about manipulating *.deb files;

    Options marked [*] produce a lot of output - pipe it through 'less' or 'more' !
    zsh: exit 2     sudo dpkg -r Project-0.1.1-Linux.deb
    sean:~/pg/cpackfirst/build % sudo dpkg -r project
    (Reading database ... 584545 files and directories currently installed.)
    Removing project (0.1.1) ...
    sean:~/pg/cpackfirst/build % main
    zsh: command not found: main
    zsh: exit 127   main
