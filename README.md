# centroidal-power-diagram
This is a private cpd test program with multiple itration method (Newton method, L-BFGS mthod and L-BFGS-B method)
(This L-BFG-B method is a parallel program)

This repository contains the code used for this paper:
[paper title](http://111.231.57.188:81)  
This paper aims to generate centroidal power diagram by gradient, newton method and BLST
additionly,  This program support generating voronoi treemap based on cpd

This program only support Windows and only run in 64 bit, which needs several libraries(We recommend to use version we wrote. We had't ran it based on other version)

# 1.Download and compile CGAL
## 1.1 Install tools
* Install *Visual Studio 2017* or higher
* Install *CMake 3.15.3*
* Install *CGAL 4.8(64bit)*
* Install *boost_1_59_0-msvc-14.0-64.exe*

## 1.2 set enviroment variable
* **Path** += C:\dev\boost_1_59_0_64\lib64-msvc-14.0;C:\dev\CGAL-4.8_64\build\bin;C:\dev\CGAL-4.8_64\auxiliary\gmp\lib;C:\dev\CGAL-4.8_64\lib;C:\dev\CGAL-4.8_64\build\bin\Debug;C:\dev\CGAL-4.8_64\build\bin\Release;
* **BOOST_LIBRARYDIR** = C:\dev\boost_1_59_0_64\lib64-msvc-14.0
* **BOOST_INCLUDEDIR** = C:\dev\boost_1_59_0_64

## 1.3 compile CGAL
1 Open *cmake-gui.exe*  
2 Set **Where is source code** = C:/dev/CGAL-4.8, **Where build the binaries** = C:/dev/CGAL-4.8/build  
3 Click **Configure**, **Generate**, **Open Project** alternately  
4 Open *CGAL.sln*, Generate project **CGAL**(not the solution, solution CGAL includes 10 projects) in **Debug** and **Release** alternately  

# 2.Download CUDA
## 2.1 Download [CUDA Toolkit](https://developer.nvidia.com/cuda-downloads)
We here use version 10.1  
Unzip to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1  
Set **CUDA_PATH** = C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1  
Set **CUDA_BIN_PATH** = %CUDA_PATH%\bin  
Set **CUDA_LIB_PATH** = %CUDA_PATH%\lib\x64  

## 2.2 Download [NVIDIA Cg Toolkit](https://developer.nvidia.com/cg-toolkit)
We here use version 3.1  
Auto unzip to C:\Program Files(x86)\NVIDIA Corporation\Cg  
**Attention!** When you install Cg Toolkit, you should click on the 64bit plugin because the default mode only install the 32 bit Cg

# 3.Download Other Libraries
## 3.1 [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page)
We here use version 3.3.1  
unzip to C:\dev\eigen\eigen-eigen-323c052e1731
## 3.2 [Freeglut](https://nchc.dl.sourceforge.net/project/freeglut/freeglut/3.2.1/freeglut-3.2.1.tar.gz)
We here use version 3.2.1  
unzip to C:\dev\freeglut

## 3.3 [Glew](https://nchc.dl.sourceforge.net/project/glew/glew/2.1.0/glew-2.1.0-win32.zip)
We here use version 2.1.0  
unzup to C:\dev\glew-2.1.0


# 4.Set Visual Studio enviroment
* **Additional Include directories** += C:\dev\eigen\eigen-eigen-323c052e1731;include;C:\dev\CGAL-4.8_64\include;C:\dev\CGAL-4.8_64\auxiliary\gmp\include;C:\dev\CGAL-4.8_64\build\include;C:\dev\boost_1_59_0_64;C:\dev\freeglut\include;C:\dev\glew-2.1.0\include;$(NVCUDASAMPLES_ROOT)\common\inc;$(IncludePath)
* **Additional Library derectories** += C:\dev\CGAL-4.8_64\build\lib;C:\dev\CGAL-4.8_64\auxiliary\gmp\lib;C:\dev\boost_1_59_0_64\lib64-msvc-14.0;C:\dev\freeglut\lib\x64;C:\dev\glew-2.1.0\lib\Release\x64;$(NVCUDASAMPLES_ROOT)\common\lib\x64;$(LibraryPath) 
* **Additional Dependencies** += cublas.lib;cudart.lib;odbc32.lib;odbccp32.lib;opengl32.lib;cg.lib;cgGL.lib;glew32.lib;freeglut.lib;kernel32.lib;user32.lib;gdi32.lib;winspool.lib;shell32.lib;ole32.lib;oleaut32.lib;uuid.lib;comdlg32.lib;advapi32.lib;C:\dev\CGAL-4.8_64\auxiliary\gmp\lib\libmpfr-4.lib;C:\dev\CGAL-4.8_64\auxiliary\gmp\lib\libgmp-10.lib;C:\dev\CGAL-4.8_64\build\lib\Release\CGAL_Core-vc140-mt-4.8.lib;C:\dev\CGAL-4.8_64\build\lib\Release\CGAL-vc140-mt-4.8.lib

## 5 Other
1. **Path** += C:\Program Files (x86)\NVIDIA Corporation\Cg\bin;C:\Program Files (x86)\NVIDIA Corporation\Cg\bin.x64
2. Put *Cg.dll, CgGL.dll, freeglut.dll* and *glew32.dll* to C:\windows\system32
3. Run this project. If error C2589 happened, Open project properties->C/C++->preprocessor->preprocessor definition->Add NOMINMAX
