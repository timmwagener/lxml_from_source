=========================
Building lxml from source
=========================

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

**************************
Why building from source ?
**************************

Why would you want to build a library like ``lxml`` from source when there are prebuilt binaries available? The reason are Python interpreters compiled with non-standard compilers. Dealing with binary Python libraries in environments that demand Python interpreters built with non-standard C-compilers can be a pain. **Non standard compiled Python interpreters are fairly common for example in the VFX industry, where the embedded interpreters are compiled with the same toolset that is used to compile the main application.** This repository should ease the steps needed to build the ``lxml`` binary python package by going through the building of each individual dependency one-by-one.

*Please note that I am not the author or a contributor to any of these dependency packages. Links to the official resources are provided.*

*********
Guideline
*********

Clone the repository and work through all the dependencies in the order given below. Feel free to try and use a version of *MSVC* you like or substitute one version of a library with a *newer/older* one. Each subfolder contains an own *README* with a specific guide for the current library. The result of all the steps for MSVC11, x64 and lxml-3.6.0 can be found in the */bin* folder.

1. zlib
2. libiconv
3. libxml2
4. libxslt
5. lxml

*********
Good luck
*********