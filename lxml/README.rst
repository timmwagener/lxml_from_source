====
lxml
====

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

Grab the latest *official* lxml sources from `PyPI <https://pypi.python.org/pypi/lxml>`_. Make sure you get the **.tar.gz** files.

**********
lxml-3.6.0
**********

Finally, after we finished all the dependencies, we are going to build `lxml` itself. We are building it for *Python27* compiled with *MSVC11/2012*. This is the setup that is used for example in the 3D application *Maya 2015*.

1. Open your MSVC2012 x64 Cross Tools command prompt
2. ``cd`` to ``lxml\lxml-3.6.0``
3. Open the file ``setup.py`` and modify like this *(of course substitute appropiate pathes)*::

    # override these and pass --static for a static build. See
    # doc/build.txt for more information. If you do not pass --static
    # changing this will have no effect.
    STATIC_INCLUDE_DIRS = [
        r"C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8",
        r"C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\source\include",
        r"C:\symlinks\repos\lxml_from_source_test\libxml2\winlibs-libxml2-2.9.3\include",
        r"C:\symlinks\repos\lxml_from_source_test\libxslt\libxslt-1.1.29",
    ]
    STATIC_LIBRARY_DIRS = [
        r"C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8\contrib\vstudio\vc11\x64\ZlibDllRelease",
        r"C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\MSVC11\libiconv_static\x64\Release",
        r"C:\symlinks\repos\lxml_from_source_test\libxml2\winlibs-libxml2-2.9.3\win32\bin.msvc",
        r"C:\symlinks\repos\lxml_from_source_test\libxslt\libxslt-1.1.29\win32\bin.msvc",
    ]

4. In the command prompt run ``set DISTUTILS_USE_SDK=1`` and ``set MSSdk=1`` to make ``distutils`` use the correct MSVC version.
5. Run ``c:\Python27\python.exe setup.py build --static`` *(Substitute the concrete path of the interpreter you want to use)*.
6. Despite a bunch of warnings you should find a successful build in ``lxml\lxml-3.6.0\build\lib.win-amd64-2.7``.
7. Go to the dependency build folders and copy the files ``zlibwapi.dll``, ``libexslt.dll``, ``libxml2.dll`` and ``libxslt.dll`` into the ``lxml`` package.

*********
That's it
*********

You should now hopefully have an ``lxml`` Python package which you can use in Python interpreters compiled with *MSVC2012*.