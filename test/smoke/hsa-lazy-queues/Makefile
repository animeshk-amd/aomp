include ../../Makefile.defs

TESTNAME     = AsyncEvents
TESTSRC_MAIN = async-events.cpp
TESTSRC_AUX  = empty-sink.c
TESTSRC_ALL  = $(TESTSRC_MAIN) $(TESTSRC_AUX)

AOMPROCM ?= $(AOMP)
ifneq (,$(wildcard $(AOMPROCM)/bin/rocprof))
	RUNPROF   = $(AOMPROCM)/bin/rocprof
else
	RUNPROF   = $(AOMPROCM)/../bin/rocprof
endif

RUNPROF_FLAGS = --hsa-trace

RUNENV      = OMP_NUM_THREADS=2 LIBOMPTARGET_AMDGPU_HSA_QUEUE_BUSY_TRACKING=1
RUNCMD      = ./$(TESTNAME) && python3 countQueueCreateEvents.py 2

CLANG        ?= clang++
OMP_BIN      = $(AOMP)/bin/$(CLANG)
CC           = $(OMP_BIN) $(VERBOSE)
#-ccc-print-phases
#"-\#\#\#"

include ../Makefile.rules
