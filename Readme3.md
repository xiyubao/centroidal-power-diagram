# centroidal-power-diagram
This is a private cpd test program(so far)

This repository contains the code used for this paper:
[paper title](http://111.231.57.188:81)  
This paper aims to generate centroidal power diagram by gradient, newton method and BLST


This program only support Windows, which needs several libraries(We recommend to use version we wrote. We had't ran it based on other version)

# 1.Download and compile CGAL
## 1.1 Install tools
* Install *Visual Studio 2017*
* Install *CMake 3.15.3*
* Install *CGAL 4.14(32bit)*
* Install *boost_1_59_0-msvc-14.0-32.exe*

## 1.2 set enviroment variable
* **Path** += C:\dev\boost_1_59_0\lib32-msvc-14.0;C:\dev\CGAL-4.14\build\bin;C:\dev\CGAL-4.14\auxiliary\gmp\lib;C:\dev\CGAL-4.14\lib;C:\dev\CGAL-4.14\build\bin\Debug;C:\dev\CGAL-4.14\build\bin\Release;
* **BOOST_LIBRARYDIR** = C:\dev\boost_1_59_0\lib32-msvc-14.0
* **BOOST_INCLUDEDIR** = C:\dev\boost_1_59_0

## 1.3 compile CGAL
1 Open *cmake-gui.exe*  
2 Set **Where is source code** = C:/dev/CGAL-4.14, **Where build the binaries** = C:/dev/CGAL-4.14/build  
3 Click **Configure**, **Generate**, **Open Project** alternately  
4 Open *CGAL.sln*, Generate project **CGAL**(not the solution, solution CGAL includes 10 projects) in **Debug** and **Release** alternately  

# 2.Download and compile SuiteSparse
## 2.1 Download [SuiteSparse](https://github.com/jlblancoc/suitesparse-metis-for-windows)
Unzip to C:/dev/suitesparse  
Set **SP_ROOT** = C:/dev/suitesparse
## 2.2 compile SuiteSparse
1 Open *cmake-gui.exe*  
2 Set **Where is source code** = C:/dev/suitesparse, **Where build the binaries** = C:/dev/suitesparse/build  
3.Set **LAPACK_DIR**=C:/dev/suitesparse/lapack_windows/x32
4 Click *Configure*, *Generate*, *Open Project* alternately  
5 Open *SuiteSparseProject.sln*, Generate project **INSTALL** in **Debug** and **Release** alternately 

# 3.Set Visual Studio enviroment
## 3.1 Debug
* **Additional Include directories** += C:\dev\boost_1_59_0;C:\dev\CGAL-4.14\include;C:\dev\CGAL-4.14\build\include;C:\dev\CGAL-4.14\auxiliary\gmp\include;C:\dev\suitesparse\build\install\include;C:\dev\suitesparse\build\install\include\suitesparse;%(AdditionalIncludeDirectories)
* **Additional Library derectories** += C:\dev\suitesparse\build\lib\Debug;C:\dev\CGAL-4.14\build\lib\Debug;C:\dev\boost_1_59_0\lib32-msvc-14.0;C:\dev\boost_1_59_0\stage\lib;C:\dev\CGAL-4.14\build\lib;C:\dev\CGAL-4.14\auxiliary\gmp\lib;C:\dev\suitesparse\lapack_windows\x32;C:\dev\suitesparse\build\install\lib\lapack_blas_windows;%(AdditionalLibraryDirectories) 
* **Additional Dependencies** += kernel32.lib;user32.lib;gdi32.lib;winspool.lib;comdlg32.lib;advapi32.lib;shell32.lib;ole32.lib;oleaut32.lib;uuid.lib;odbc32.lib;odbccp32.lib;libboost_atomic-vc140-mt-1_59.lib;libboost_atomic-vc140-mt-gd-1_59.lib;libboost_chrono-vc140-mt-1_59.lib;libboost_chrono-vc140-mt-gd-1_59.lib;libboost_container-vc140-mt-1_59.lib;libboost_container-vc140-mt-gd-1_59.lib;libboost_context-vc140-mt-1_59.lib;libboost_context-vc140-mt-gd-1_59.lib;libboost_coroutine-vc140-mt-1_59.lib;libboost_coroutine-vc140-mt-gd-1_59.lib;libboost_date_time-vc140-mt-1_59.lib;libboost_date_time-vc140-mt-gd-1_59.lib;libboost_exception-vc140-mt-1_59.lib;libboost_exception-vc140-mt-gd-1_59.lib;libboost_filesystem-vc140-mt-1_59.lib;libboost_filesystem-vc140-mt-gd-1_59.lib;libboost_graph-vc140-mt-1_59.lib;libboost_graph-vc140-mt-gd-1_59.lib;libboost_iostreams-vc140-mt-1_59.lib;libboost_iostreams-vc140-mt-gd-1_59.lib;libboost_locale-vc140-mt-1_59.lib;libboost_locale-vc140-mt-gd-1_59.lib;libboost_log_setup-vc140-mt-1_59.lib;libboost_log_setup-vc140-mt-gd-1_59.lib;libboost_log-vc140-mt-1_59.lib;libboost_log-vc140-mt-gd-1_59.lib;libboost_math_c99f-vc140-mt-1_59.lib;libboost_math_c99f-vc140-mt-gd-1_59.lib;libboost_math_c99l-vc140-mt-1_59.lib;libboost_math_c99l-vc140-mt-gd-1_59.lib;libboost_math_c99-vc140-mt-1_59.lib;libboost_math_c99-vc140-mt-gd-1_59.lib;libboost_math_tr1f-vc140-mt-1_59.lib;libboost_math_tr1f-vc140-mt-gd-1_59.lib;libboost_math_tr1l-vc140-mt-1_59.lib;libboost_math_tr1l-vc140-mt-gd-1_59.lib;libboost_math_tr1-vc140-mt-1_59.lib;libboost_math_tr1-vc140-mt-gd-1_59.lib;libboost_prg_exec_monitor-vc140-mt-1_59.lib;libboost_prg_exec_monitor-vc140-mt-gd-1_59.lib;libboost_program_options-vc140-mt-1_59.lib;libboost_program_options-vc140-mt-gd-1_59.lib;libboost_random-vc140-mt-1_59.lib;libboost_random-vc140-mt-gd-1_59.lib;libboost_regex-vc140-mt-1_59.lib;libboost_regex-vc140-mt-gd-1_59.lib;libboost_serialization-vc140-mt-1_59.lib;libboost_serialization-vc140-mt-gd-1_59.lib;libboost_signals-vc140-mt-1_59.lib;libboost_signals-vc140-mt-gd-1_59.lib;libboost_system-vc140-mt-1_59.lib;libboost_system-vc140-mt-gd-1_59.lib;libboost_test_exec_monitor-vc140-mt-1_59.lib;libboost_test_exec_monitor-vc140-mt-gd-1_59.lib;libboost_thread-vc140-mt-1_59.lib;libboost_thread-vc140-mt-gd-1_59.lib;libboost_timer-vc140-mt-1_59.lib;libboost_timer-vc140-mt-gd-1_59.lib;libboost_unit_test_framework-vc140-mt-1_59.lib;libboost_unit_test_framework-vc140-mt-gd-1_59.lib;libboost_wave-vc140-mt-1_59.lib;libboost_wave-vc140-mt-gd-1_59.lib;libboost_wserialization-vc140-mt-1_59.lib;libboost_wserialization-vc140-mt-gd-1_59.lib;libgmp-10.lib;libmpfr-4.lib;CGAL_Core-vc140-mt-gd-4.14.lib;CGAL_ImageIO-vc140-mt-gd-4.14.lib;CGAL-vc140-mt-gd-4.14.lib;
libcholmodd.lib;
libamdd.lib;
libcamdd.lib;
libcolamdd.lib;
libccolamdd.lib;
libcxsparsed.lib;
libklud.lib;
libldld.lib;
libspqrd.lib;
libumfpackd.lib;
metisd.lib;
suitesparseconfigd.lib;
;libblas.lib;liblapack.lib;%(AdditionalDependencies)  

## 3.2 Release
* **Additional Include directories** += C:\dev\boost_1_59_0;C:\dev\CGAL-4.14\include;C:\dev\CGAL-4.14\build\include;C:\dev\CGAL-4.14\auxiliary\gmp\include;C:\dev\suitesparse\build\install\include;C:\dev\suitesparse\build\install\include\suitesparse;%(AdditionalIncludeDirectories)
* **Additional Library derectories** += C:\dev\suitesparse\build\lib\Release;C:\dev\CGAL-4.14\build\lib\Release;C:\dev\boost_1_59_0\lib32-msvc-14.0;C:\dev\boost_1_59_0\stage\lib;C:\dev\CGAL-4.14\build\lib;C:\dev\CGAL-4.14\auxiliary\gmp\lib;C:\dev\suitesparse\lapack_windows\x32;C:\dev\suitesparse\build\install\lib\lapack_blas_windows;%(AdditionalLibraryDirectories) 
* **Additional Dependencies** += kernel32.lib;user32.lib;gdi32.lib;winspool.lib;comdlg32.lib;advapi32.lib;shell32.lib;ole32.lib;oleaut32.lib;uuid.lib;odbc32.lib;odbccp32.lib;libboost_atomic-vc140-mt-1_59.lib;libboost_atomic-vc140-mt-gd-1_59.lib;libboost_chrono-vc140-mt-1_59.lib;libboost_chrono-vc140-mt-gd-1_59.lib;libboost_container-vc140-mt-1_59.lib;libboost_container-vc140-mt-gd-1_59.lib;libboost_context-vc140-mt-1_59.lib;libboost_context-vc140-mt-gd-1_59.lib;libboost_coroutine-vc140-mt-1_59.lib;libboost_coroutine-vc140-mt-gd-1_59.lib;libboost_date_time-vc140-mt-1_59.lib;libboost_date_time-vc140-mt-gd-1_59.lib;libboost_exception-vc140-mt-1_59.lib;libboost_exception-vc140-mt-gd-1_59.lib;libboost_filesystem-vc140-mt-1_59.lib;libboost_filesystem-vc140-mt-gd-1_59.lib;libboost_graph-vc140-mt-1_59.lib;libboost_graph-vc140-mt-gd-1_59.lib;libboost_iostreams-vc140-mt-1_59.lib;libboost_iostreams-vc140-mt-gd-1_59.lib;libboost_locale-vc140-mt-1_59.lib;libboost_locale-vc140-mt-gd-1_59.lib;libboost_log_setup-vc140-mt-1_59.lib;libboost_log_setup-vc140-mt-gd-1_59.lib;libboost_log-vc140-mt-1_59.lib;libboost_log-vc140-mt-gd-1_59.lib;libboost_math_c99f-vc140-mt-1_59.lib;libboost_math_c99f-vc140-mt-gd-1_59.lib;libboost_math_c99l-vc140-mt-1_59.lib;libboost_math_c99l-vc140-mt-gd-1_59.lib;libboost_math_c99-vc140-mt-1_59.lib;libboost_math_c99-vc140-mt-gd-1_59.lib;libboost_math_tr1f-vc140-mt-1_59.lib;libboost_math_tr1f-vc140-mt-gd-1_59.lib;libboost_math_tr1l-vc140-mt-1_59.lib;libboost_math_tr1l-vc140-mt-gd-1_59.lib;libboost_math_tr1-vc140-mt-1_59.lib;libboost_math_tr1-vc140-mt-gd-1_59.lib;libboost_prg_exec_monitor-vc140-mt-1_59.lib;libboost_prg_exec_monitor-vc140-mt-gd-1_59.lib;libboost_program_options-vc140-mt-1_59.lib;libboost_program_options-vc140-mt-gd-1_59.lib;libboost_random-vc140-mt-1_59.lib;libboost_random-vc140-mt-gd-1_59.lib;libboost_regex-vc140-mt-1_59.lib;libboost_regex-vc140-mt-gd-1_59.lib;libboost_serialization-vc140-mt-1_59.lib;libboost_serialization-vc140-mt-gd-1_59.lib;libboost_signals-vc140-mt-1_59.lib;libboost_signals-vc140-mt-gd-1_59.lib;libboost_system-vc140-mt-1_59.lib;libboost_system-vc140-mt-gd-1_59.lib;libboost_test_exec_monitor-vc140-mt-1_59.lib;libboost_test_exec_monitor-vc140-mt-gd-1_59.lib;libboost_thread-vc140-mt-1_59.lib;libboost_thread-vc140-mt-gd-1_59.lib;libboost_timer-vc140-mt-1_59.lib;libboost_timer-vc140-mt-gd-1_59.lib;libboost_unit_test_framework-vc140-mt-1_59.lib;libboost_unit_test_framework-vc140-mt-gd-1_59.lib;libboost_wave-vc140-mt-1_59.lib;libboost_wave-vc140-mt-gd-1_59.lib;libboost_wserialization-vc140-mt-1_59.lib;libboost_wserialization-vc140-mt-gd-1_59.lib;libgmp-10.lib;libmpfr-4.lib;CGAL_Core-vc140-mt-gd-4.14.lib;CGAL_ImageIO-vc140-mt-gd-4.14.lib;CGAL-vc140-mt-gd-4.14.lib;
libcholmod.lib;
libam.lib;
libcam.lib;
libcolam.lib;
libccolam.lib;
libcxsparse.lib;
libklu.lib;
libldl.lib;
libspqr.lib;
libumfpack.lib;
metis.lib;
suitesparseconfig.lib;
;libblas.lib;liblapack.lib;%(AdditionalDependencies)  

## 3.3 Other
1. Copy **libmpfr-4.dll** and **libgmp-10.dll** from C:\dev\CGAL-4.14\auxiliary\gmp\lib to this project
2. Copy **CGAL-vc140-mt-gd-4.14.dll** from C:\dev\CGAL-4.14\build\bin to this project
3. **Path** += C:\dev\CGAL-4.14\build\bin;C:\dev\CGAL-4.14\auxiliary\gmp\lib;C:\dev\CGAL-4.14\lib;C:\dev\CGAL-4.14\build\bin\Debug;
4. Run this project. If error C2589 happened, Open project properties->C/C++->preprocessor->preprocessor definition->Add NOMINMAX

