====
zlib
====

::
    
    All the examples are built with MSVC2012 in Release mode for x64. The same steps might (or might not) apply aswell
    for different MSVC versions, different bitness or optimization modes. The sources do have *README* files from the
    authors aswell. If you get stuck using the fast-lane I am providing here, please have a look at those files.

Grab the latest official sources `here <http://zlib.net/>`_.

*******************
Building zlib-1.2.8
*******************

Building zlib is not amongst the hardest tasks, however there are some slight traps.

1. Go to ``zlib\zlib-1.2.8\contrib\vstudio\vc11`` and open ``zlibvc.sln`` with Visual Studio 2012.
2. Change the **solution platform** to **x64** and the **Solution Configuration** to **Release**.
3. Open the file ``zlibvc.def`` in the solution *zlibvc* project in Solution Explorer and change the line ``VERSION		1.2.8`` to ``VERSION		1.2``
4. When compiling for *Win7 x64* change the platform toolset to **Visual Studio 2012 - Windows XP (v110_xp)**. (The default of **Visual Studio 2012 (v110)** will result in runtime errors).
5. Rebuild the **zlibvc** project and you should get a successful build.
6. Go to ``zlib\zlib-1.2.8\contrib\vstudio\vc11\x64\ZlibDllRelease`` and in this build folder copy the file ``zlibwapi.lib`` and rename the copy to ``zlib.lib``