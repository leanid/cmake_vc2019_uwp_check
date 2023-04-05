# Just minimal example of failure UWP build configuration

For some reason VC2019 with cmake 3.26.3 with installed UWP developers tools not working.
How I check it out:

```sh
git clone git@github.com:leanid/cmake_vc2019_uwp_check.git
mkdir build
cd build
cmake.exe --log-level=TRACE -G "Visual Studio 16 2019" -A x64 -DCMAKE_TOOLCHAIN_FILE=..\uwp-toolchain.cmake .. >build_log.txt 2>&1
```

# uwp-toolchain.cmake contents

```cmake
set(CMAKE_SYSTEM_NAME WindowsStore)
set(CMAKE_SYSTEM_VERSION 10.0)
```

# CMakeLists.txt contents 

```cmake 
cmake_minimum_required(VERSION 3.22...3.26.3)

project(any_project_name_just_to_test)
```

# build_log.txt contents 
```sh
-- Selecting Windows SDK version 10.0.22000.0 to target Windows 10.0.
-- The C compiler identification is MSVC 19.29.30148.0
-- The CXX compiler identification is MSVC 19.29.30148.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - failed
-- Check for working C compiler: c:/Program Files (x86)/Microsoft Visual Studio/2019/Professional/VC/Tools/MSVC/14.29.30133/bin/Hostx64/x64/cl.exe
-- Check for working C compiler: c:/Program Files (x86)/Microsoft Visual Studio/2019/Professional/VC/Tools/MSVC/14.29.30133/bin/Hostx64/x64/cl.exe - broken
CMake Error at C:/j/client/dava.framework/Bin/CMakeWin32/share/cmake-3.25/Modules/CMakeTestCCompiler.cmake:70 (message):
  The C compiler

    "c:/Program Files (x86)/Microsoft Visual Studio/2019/Professional/VC/Tools/MSVC/14.29.30133/bin/Hostx64/x64/cl.exe"

  is not able to compile a simple test program.

  It fails with the following output:

    Change Dir: D:/j/cmake_vc2019_uwp_check/build/CMakeFiles/CMakeScratch/TryCompile-qu3z9m

    Run Build Command(s):c:/Program Files (x86)/Microsoft Visual Studio/2019/Professional/MSBuild/Current/Bin/MSBuild.exe cmTC_973a4.vcxproj /p:Configuration=Debug /p:Platform=x64 /p:VisualStudioVersion=16.0 /v:m && Microsoft (R) Build Engine version 16.11.2+f32259642 for .NET Framework
    Copyright (C) Microsoft Corporation. All rights reserved.

      Microsoft (R) C/C++ Optimizing Compiler Version 19.29.30148 for x64
      Copyright (C) Microsoft Corporation.  All rights reserved.
      testCCompiler.c
      cl /c /I"D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\\" /I"Generated Files\\" /IcmTC_973a4.dir\Debug\ /Zi /W3 /WX- /diagnostics:column /sdl /MP /Od /Ob0 /Oi /Oy- /D _UNICODE /D UNICODE /D WINAPI_FAMILY=WINAPI_FAMILY_APP /D __WRL_NO_DEFAULT_LIB__ /D WIN32 /D _WINDOWS /D UNICODE /D _UNICODE /D "CMAKE_INTDIR=\"Debug\"" /Gm- /MDd /GS /Gy /fp:precise /Zc:wchar_t /Zc:forScope /Zc:inline /Fo"cmTC_973a4.dir\Debug\\" /Fd"cmTC_973a4.dir\Debug\vc142.pdb" /external:W3 /Gd /TC /FU"c:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\VC\Tools\MSVC\14.29.30133\lib\x86\store\references\platform.winmd" /analyze- /errorReport:queue "D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\testCCompiler.c"
    LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification [D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\cmTC_973a4.vcxproj]
      cmTC_973a4.vcxproj -> D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\Debug\cmTC_973a4.exe
    c:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\MSBuild\Microsoft\VisualStudio\v16.0\AppxPackage\Microsoft.AppXPackage.Targets(2720,5): warning : Publisher name (CN=CMake) does not match signing certificate subject: CN=CMake Test Cert. Updating Publisher name. [D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\cmTC_973a4.vcxproj]
      cmTC_973a4 -> D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\AppPackages\cmTC_973a4\cmTC_973a4_1.0.0.0_x64_Debug_Test\cmTC_973a4_1.0.0.0_x64_Debug.msix
    c:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\MSBuild\Microsoft\VisualStudio\v16.0\AppxPackage\Microsoft.AppXPackage.Targets(3495,5): error APPX1204: Failed to sign 'D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\AppPackages\cmTC_973a4\cmTC_973a4_1.0.0.0_x64_Debug_Test\cmTC_973a4_1.0.0.0_x64_Debug.msix'. SignTool Error: No certificates were found that met all the given criteria. [D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\cmTC_973a4.vcxproj]
    c:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\MSBuild\Microsoft\VisualStudio\v16.0\AppxPackage\Microsoft.AppXPackage.Targets(3495,5): error APPX1204:  [D:\j\cmake_vc2019_uwp_check\build\CMakeFiles\CMakeScratch\TryCompile-qu3z9m\cmTC_973a4.vcxproj]





  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:3 (project)


-- Configuring incomplete, errors occurred!
See also "D:/j/cmake_vc2019_uwp_check/build/CMakeFiles/CMakeOutput.log".
See also "D:/j/cmake_vc2019_uwp_check/build/CMakeFiles/CMakeError.log".
```

