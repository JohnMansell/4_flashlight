cmake_minimum_required(VERSION 3.22)

set(LDFLAGS += -L/usr/lib/x86_64-linux-gnu)
set(LDFLAGS += -lglut -lGL -lGLU -lGLEW)

set(CMAKE_CUDA_COMPILER /usr/local/cuda/bin/nvcc)
set(NVCC_FLAGS = -g -G -Xcompiler "-Wall -Wno-deprecated-declarations")

project(4_flashlight CUDA)

set(CMAKE_CUDA_STANDARD 23)

add_executable(flashlight main.cu kernel.cuh kernel.cu interactions.cuh)

set_target_properties(flashlight PROPERTIES
        CUDA_SEPARABLE_COMPILATION ON)
