# centroidal-power-diagram
This is a private cpd test program(so far)

This repository contains the code used for this paper:
[paper title](111.231.57.188)
This paper aims to generate centroidal power diagram by gradient, newton method and BLST


This program only support Windows, which needs several libraries(We recommend to use version we wrote. We had't ran it based on other version)

# 1.Download and compile CGAL
## 1.1 Install tools
* Install *Visual Studio 2017*
* Install *CMake 3.15.3*
* Install *CGAL 4.14(32bit)*
* Install *boost_1_59_0-msvc-14.0-32.exe*

## 1.2 set enviroment variable
* **Path** += 
* **BOOST_LIBRARYDIR** = 
* **BOOST_INCLUDEDIR** = 

## 1.3 compile CGAL
1.3.1 open *cmake-gui.exe*
1.3.2 set **Where is source code** = C:/dev/CGAL-4.14, **Where build the binaries** = C:/dev/CGAL-4.14/build
1.3.3 Click **Configure**,** Generate**, **Open Project** alternately
1.3.4 Open CGAL.sln, Generate project **CGAL**(not the solution, solution CGAL includes 10 projects) in **Debug** and **Release** *alternately

# 2.Download and compile SuiteSparse
## 2.1 Download [SuiteSparse](https://github.com/jlblancoc/suitesparse-metis-for-windows)
unzip to C:/dev/suitesparse
\set **SP_ROOT** = C:/dev/suitesparse
## 2.2 compile SuiteSparse



