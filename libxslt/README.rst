=======
libxslt
=======

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

Grab the latest *official* libxml2 and libxslt sources `here <ftp://xmlsoft.org/libxml2/>`_.

**************
libxslt-1.1.29
**************

This is an official unaltered version downloaded from the official `mirror <ftp://xmlsoft.org/libxml2/>`_.

1. Open your MSVC2012 x64 Cross Tools command prompt
2. ``cd`` to ``libxslt\libxslt-1.1.29\win32``
3. This package will be compiled through the comamnd line. To do so, we have to run a ``cscript`` command that configures the ``Makefile.msvc``. Type this in the console *(Replace the pathes as appropiate)*::

    cscript configure.js compiler=msvc iconv=yes zlib=yes include=C:\symlinks\repos\lxml_from_source_test\libxml2\winlibs-libxml2-2.9.3\include;C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\source\include lib=C:\symlinks\repos\lxml_from_source_test\libxml2\winlibs-libxml2-2.9.3\win32\bin.msvc;C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8\contrib\vstudio\vc11\x64\ZlibDllRelease;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\MSVC11\libiconv_static\x64\Release debug=no

4. Run ``nmake rebuild /f Makefile.msvc``
5. Despite a bunch of warnings you should find successful builds in ``libxslt\libxslt-1.1.29\win32\bin.msvc``.