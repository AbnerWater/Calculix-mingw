CFLAGS = -Wall -O3 -g -I ../../SPOOLES.2.2 -DARCH="Linux" -DSPOOLES -DARPACK -DMATRIXSTORAGE -DNETWORKOUT
# CFLAGS = -Wall -O3 -g -DARCH="Linux" -DMATRIXSTORAGE -DNETWORKOUT
FFLAGS = -Wall -O3 -g  

CC=gcc
FC=gfortran

.c.o :
	$(CC) $(CFLAGS) -c $<
.f.o :
	$(FC) $(FFLAGS) -c $<

include Makefile.inc

SCCXMAIN = ccx_2.17.c

OCCXF = $(SCCXF:.f=.o)
OCCXC1 = $(SCCXC1:.c=.o)
OCCXC2 = $(SCCXC2:.c=.o)
OCCXMAIN = $(SCCXMAIN:.c=.o)

DIR=../../SPOOLES.2.2
LIBDIR=c:/msys64/mingw64/x86_64-w64-mingw32/lib
# MKLDIR=C:/Program Files (x86)/IntelSWTools/compilers_and_libraries_2019\windows/mkl/lib/intel64_win
# intelDir=C:/Program Files (x86)/IntelSWTools/compilers_and_libraries_2019.0.117/linux/compiler/lib/intel64_lin

LIBS = \
		$(LIBDIR)/libm.a \
		../../ARPACK/libarpack_MINGW64.a \
		$(DIR)/spooles.a \
	    $(LIBDIR)/libpthread.a\

ccx_2.17.exe: $(OCCXMAIN) ccx_2.17c1.a $(LIBS)
	./date.pl; $(CC) $(CFLAGS) -c ccx_2.17.c; $(FC) -fopenmp -Wall -O3 -o $@ $(OCCXMAIN) ccx_2.17c1.a $(LIBS)

ccx_2.17c1.a: $(OCCXC1) $(OCCXF)
	ar vr $@ $?
ccx_2.17c1.a: ccx_2.17c1.a $(OCCXC2)
	ar r $@ $?
clean:
	rm -f *.o ccx_2.17c1.a ccx_2.17.exe               