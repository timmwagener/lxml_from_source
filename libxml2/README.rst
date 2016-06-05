=======
libxml2
=======

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

Grab the latest *official* libxml2 and libxslt sources `here <ftp://xmlsoft.org/libxml2/>`_.

*********************
winlibs-libxml2-2.9.3
*********************

Aside from the official source version *2.7.8* you might also decide to build a newer version of *libxml2*. If you do so, the newer official sources downloadable `from here <ftp://xmlsoft.org/libxml2/>`_ can give you headaches. Luckily the maintainers of the winlibs repositories also maintain a `libxml2 repository <https://github.com/winlibs/libxml2>`_ with adjusted sources to build less complicated with *MSVC*. **However, keep in mind that those sources have been modified!**

To build them do the following.

1. Open your MSVC2012 x64 Cross Tools command prompt
2. ``cd`` to ``libxml2\winlibs-libxml2-2.9.3\win32``
3. This package will be compiled through the comamnd line. To do so, we have to run a ``cscript`` command that configures the ``Makefile.msvc``. Type this in the console *(Replace the pathes as appropiate)*::

    cscript configure.js compiler=msvc prefix=c:\src\libxml2 iconv=yes zlib=yes include=C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\source\include lib=C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8\contrib\vstudio\vc11\x64\ZlibDllRelease;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\MSVC11\libiconv_static\x64\Release debug=no vcmanifest=yes

4. Run ``nmake rebuild /f Makefile.msvc``
5. Despite 1 or 2 warnings you should find successful builds in ``libxml2\winlibs-libxml2-2.9.3\win32\bin.msvc``.


**********************
Building libxml2-2.7.8
**********************

This is an official unaltered version downloaded from the official `mirror <ftp://xmlsoft.org/libxml2/>`_. It is also the version mentioned in the official `lxml documentation <http://lxml.de/3.0/installation.html>`_.

1. Open your MSVC2012 x64 Cross Tools command prompt
2. ``cd`` to ``libxml2\libxml2-2.7.8\win32``
3. This package will be compiled through the comamnd line. To do so, we have to run a ``cscript`` command that configures the ``Makefile.msvc``. Type this in the console *(Replace the pathes as appropiate)*::

    cscript configure.js compiler=msvc prefix=c:\src\libxml2 iconv=yes zlib=yes include=C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\source\include lib=C:\symlinks\repos\lxml_from_source_test\zlib\zlib-1.2.8\contrib\vstudio\vc11\x64\ZlibDllRelease;C:\symlinks\repos\lxml_from_source_test\libiconv\winlibs-libiconv-1.14\MSVC11\libiconv_static\x64\Release debug=no vcmanifest=yes

4. Open ``Makefile.msvc`` and go to line 74. Remove all the pluses from line *74-76*::
    
    +!if "$(WITH_ICU)" == "1"
    +LIBS = $(LIBS) icu.lib
    +!endif
    <<<>>>
    !if "$(WITH_ICU)" == "1"
    LIBS = $(LIBS) icu.lib
    !endif

5. Go to line *78* and rename ``LIBS = $(LIBS) zdll.lib`` to ``LIBS = $(LIBS) zlibwapi.lib``
6. Go to line *97* and comment out the line ``LDFLAGS = $(LDFLAGS) /OPT:NOWIN98``
7. Run ``nmake rebuild /f Makefile.msvc``
8. Despite a bunch of warnings you should find successful builds in ``libxml2\libxml2-2.7.8\win32\bin.msvc``.