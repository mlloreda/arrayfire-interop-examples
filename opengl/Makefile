INCLUDES=-I/usr/local/include

COMPILER_OPTIONS=-std=c++11 -g
CXX=/usr/bin/g++ $(COMPILER_OPTIONS)

COMMON_LIBS=-lGL -lglfw
CL_LIBS=-lOpenCL -lafopencl

NVCC := /usr/local/cuda/bin/nvcc $(COMPILER_OPTIONS)
CUDA_LIB_PATH := /usr/local/cuda/lib64/
CUDA_NVVM_PATH := /usr/local/cuda/nvvm/lib64/
CUDA_LDFLAGS   += -L$(CUDA_LIB_PATH) -L$(CUDA_NVVM_PATH) -lcudart -lafcuda -lnvvm -Xlinker -rpath,$(CUDA_LIB_PATH),-rpath,$(CUDA_NVVM_PATH)

all: af-gl-opencl af-gl-cuda

af-gl-opencl: main.cpp afopengl-opencl.cpp
	$(CXX) main.cpp afopengl-opencl.cpp -o af-gl-opencl $(INCLUDES) $(CL_LIBS) $(COMMON_LIBS) $(LIB_PATHS)

af-gl-cuda: main.cpp afopengl-cuda.cpp
	$(NVCC) main.cpp afopengl-cuda.cpp -o af-gl-cuda $(INCLUDES) $(CUDA_LDFLAGS) $(COMMON_LIBS) $(LIB_PATHS)

clean:
	rm af-gl-opencl af-gl-cuda
