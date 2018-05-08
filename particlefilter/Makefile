include ../common/make.config
#OPENCL_DIR = /af21/den4gr/NVIDIA_GPU_Computing_SDK/

# C compiler
CC = g++
CC_FLAGS = -O2 -Wall -I/opt/altera/16.0/hld/host/include
#INCLUDES = -I$(OPENCL_DIR)/OpenCL/common/inc -I$(OPENCL_DIR)/shared/inc/
INCLUDES = -I$(OPENCL_INC)

OPENCL_INC=/opt/altera_pro/16.0.2/hld/host/include/

OPENCL_LIB=/opt/altera_pro/16.0.2/hld/linux64/lib/

ALL: OCL_particlefilter_naive OCL_particlefilter_double OCL_particlefilter_single \
     OCL_particlefilter_naive_fpga \
     

OCL_particlefilter_naive: ex_particle_OCL_naive_seq.o
	$(CC) $(CC_FLAGS) ex_particle_OCL_naive_seq.o $(INCLUDES) -L$(OPENCL_LIB) -lOpenCL -o OCL_particlefilter_naive

OCL_particlefilter_double: ex_particle_OCL_double_seq.o
	$(CC) $(CC_FLAGS) ex_particle_OCL_double_seq.o $(INCLUDES)  -L$(OPENCL_LIB) -lOpenCL -o OCL_particlefilter_double 

OCL_particlefilter_single: ex_particle_OCL_single_seq.o
	$(CC) $(CC_FLAGS) ex_particle_OCL_single_seq.o $(INCLUDES)  -L$(OPENCL_LIB) -lOpenCL -o OCL_particlefilter_single 

OCL_particlefilter_naive_fpga: ex_particle_OCL_naive_seq_fpga.o
	$(CC) $(CC_FLAGS) ex_particle_OCL_naive_seq_fpga.o -o $@ -I$(OPENCL_INC) -L$(OPENCL_LIB) -lOpenCL


%.o: %.[ch]
	$(CC) $(CC_FLAGS) $< -c

ex_particle_OCL_naive_seq.o: ex_particle_OCL_naive_seq.cpp
	$(CC) $(CC_FLAGS) $(INCLUDES) ex_particle_OCL_naive_seq.cpp -c

ex_particle_OCL_double_seq.o: ex_particle_OCL_double_seq.cpp
	$(CC) $(CC_FLAGS) $(INCLUDES) ex_particle_OCL_double_seq.cpp -c

ex_particle_OCL_single_seq.o: ex_particle_OCL_single_seq.cpp
	$(CC) $(CC_FLAGS) $(INCLUDES) ex_particle_OCL_single_seq.cpp -c

ex_particle_OCL_naive_seq_fpga.o: ex_particle_OCL_naive_seq_fpga.cpp
	$(CC) $(CC_FLAGS) $(INCLUDES) ex_particle_OCL_naive_seq_fpga.cpp -c

clean:
	rm -f *.o *~ *~ OCL_particlefilter_naive OCL_particlefilter_double OCL_particlefilter_single *.linkinfo
