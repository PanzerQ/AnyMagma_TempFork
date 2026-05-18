
#  --------------------
#  程序设置
#  --------------------
CC        = gcc
CXX       = g++
FORT      = gfortran

ARCH      = ar
ARCHFLAGS = cr
RANLIB    = ranlib

#  --------------------
#  编译与链接标志
#  --------------------
# 生成共享库所需的PIC标志
FPIC      = -fPIC

# CFLAGS: -fopenmp 启用多核并行
CFLAGS    = -O3 $(FPIC) -DADD_ -Wall -fopenmp -DCL_TARGET_OPENCL_VERSION=120
CXXFLAGS  = $(CFLAGS) -std=c++11
FFLAGS    = -O3 $(FPIC) -DADD_ -Wall -Wno-unused-dummy-argument
F90FLAGS  = -O3 $(FPIC) -DADD_ -Wall -Wno-unused-dummy-argument -x f95-cpp-input
LDFLAGS   = $(FPIC) -fopenmp

#  --------------------
#  链接库设置 (关键修改点)
#  --------------------
# 1. CPU BLAS/LAPACK: 使用 OpenBLAS (自带 LAPACK 功能)
LIB       = -lopenblas

# 2. GPU OpenCL BLAS: 使用 clBLAST 替换 clBLAS
LIB      += -lclblast

# 3. OpenCL 运行时库
LIB      += -lOpenCL

# 如果使用 NVIDIA GPU 且安装了 CUDA 工具包，请移除上一行的 -lOpenCL，改用下面的方式：
# LIB      += -L/usr/local/cuda/lib64 -lOpenCL

#  --------------------
#  头文件与库文件路径设置
#  --------------------
# 定义库的安装路径（使用 apt 安装后的默认路径）
OPENBLASDIR ?= /usr/lib/x86_64-linux-gnu
clBLAST     ?= /usr/lib/x86_64-linux-gnu

# 库文件目录
LIBDIR     = -L$(OPENBLASDIR) \
             -L$(clBLAST)

# 头文件目录
INC        = -I$(OPENBLASDIR)/include \
             -I/usr/include
