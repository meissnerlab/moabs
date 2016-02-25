CC=	g++

ifndef SAMTOOLS
	SAMTOOLS=$(MOABS_ROOT)/src/bsmap/samtools
endif

ifndef HTSLIB
	HTSLIB=$(MOABS_ROOT)/src/bsmap/htslib
endif

##The corresponding files are $(MOABS_ROOT)/src/bsmap/boost/boost/*hpp
ifndef BOOSTINC
	BOOSTINC=$(MOABS_ROOT)/src/bsmap/boost
endif

##The corresponding files are $(MOABS_ROOT)/src/bsmap/boost/lib/libboost*
ifndef BOOSTLIB
	BOOSTLIB=$(MOABS_ROOT)/src/bsmap/boost/lib
endif



CPPFLAGS := -Wall -w -I/usr/local/include -I${BOOSTINC} -I${SAMTOOLS} -I${HTSLIB} -g -O3

LDLIBS :=-L${BOOSTLIB} -lboost_program_options -Wl,-rpath=${BOOSTLIB} -L${BOOSTLIB} -lboost_system -L${BOOSTLIB} -lboost_filesystem -L${BOOSTLIB} -lboost_thread -L${BOOSTLIB} -lboost_date_time  -L${SAMTOOLS} -lbam -L${HTSLIB} -lhts -lz -lrt -lpthread

SOURCE = mcall.cpp
PRG=mcall

all: mcall

OBJ=mcall.o

mcall: $(OBJ)
	$(CC) -o $(PRG) $(OBJ) $(CPPFLAGS) $(LDLIBS)
	rm -f *.o
mcall.o: mcall.cpp
	$(CC) -c mcall.cpp $(CPPFLAGS)

clean:
	rm -f *.o mcall

install: $(PRG)
	@mkdir -p $(SRC_ROOT)/bin
	@install -m 755 $(PRG) $(SRC_ROOT)/bin
