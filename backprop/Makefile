include ../common/make.config

# C compiler
CC = g++
## niran CC_FLAGS = -g -O2
CC_FLAGS = -O2 -g -Wall 

# Xilinx OpenCL
## niran XILINX_OPENCL := /opt/Xilinx/SDAccel/2015.4
## niran XILINX_OPENCL_INC := $(XILINX_OPENCL)/runtime/include/1_2
## niran XILINX_OPENCL_LIB := $(XILINX_OPENCL)/runtime/lib/x86_64
## niran INCLUDES = -I$(OPENCL_INC)

OPENCL_INC=/opt/altera_pro/16.0.2/hld/host/include/
OPENCL_LIB=/opt/altera_pro/16.0.2/hld/linux64/lib/

#backprop_gpu.exe: backprop.o imagenet.o facetrain.o
#	$(CC) $(CC_FLAGS) backprop_ocl_gpu.cpp backprop.o imagenet.o facetrain.o -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB) -lOpenCL

backprop_fpga.exe: backprop.o imagenet.o facetrain.o
	$(CC) $(CC_FLAGS) backprop_ocl_fpga.cpp backprop.o imagenet.o facetrain.o -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB) -lOpenCL

%.o: %.[ch]
	$(CC) $(CC_FLAGS) $< -c
	
backprop.o: backprop.c 
	$(CC) $(CC_FLAGS) backprop.c -c
	
facetrain.o: facetrain.c
	$(CC) $(CC_FLAGS) facetrain.c -c

imagenet.o: imagenet.c
	$(CC) $(CC_FLAGS) imagenet.c -c

#niran clean:
#niran	rm -f *.o *~ backprop*.exe *.linkinfo
