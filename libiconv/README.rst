========
libiconv
========

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

Sources used in this repository are from `the winlibs-libiconv repository <https://github.com/winlibs/libiconv>`_. (Basically a repository that has done the wild adjustments to the source, needed for a build with MSVC, already. You find the myriad of changes that were needed in the provided `.diff file <https://github.com/winlibs/libiconv/blob/master/libiconv.diff>`_)

Grab the latest *official* GNU sources `here <https://savannah.gnu.org/projects/libiconv/>`_.

******************************
Building winlibs-libiconv-1.14
******************************

Luckily the real hard part has already been taken care of through the *winlibs-libiconv* maintainers.

1. Go to ``libiconv\winlibs-libiconv-1.14\MSVC11`` and open ``libiconv.sln`` with Visual Studio 2012.
2. Change the **solution platform** to **x64** and the **Solution Configuration** to **Release**.
3. When compiling for *Win7 x64* change the platform toolset to **Visual Studio 2012 - Windows XP (v110_xp)** for both projects in the solution explorer ``libiconv_static`` and ``libiconv_dll``. (The default of **Visual Studio 2012 (v110)** will result in runtime errors).
4. Rebuild the both projects and, despite some warnings, you should get a successful build in ``libiconv\winlibs-libiconv-1.14\MSVC11\libiconv_static\x64\Release``.
5. In this build folder copy the file ``libiconv_a.lib`` two times and rename the copies to ``iconv_a.lib`` and ``iconv.lib``