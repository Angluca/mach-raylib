.PHONY: all clean run

MAKE ?= make
ifeq ($(PLATFORM_OS),WINDOWS)
    MAKE = mingw32-make
endif

#LIBS_PATH ?= -L ../../libs
ARGS ?= -L ../../libs

MFLAGS = $(ARGS)
SRCS = $(wildcard src/*.mach)

TARGETS = $(notdir $(SRCS:.mach=))
all: $(TARGETS)

%: src/%.mach
	mach build . $(MFLAGS) -v --bin $@

RUN_TARGET = $(filter-out run, $(MAKECMDGOALS))
run: $(RUN_TARGET)
	mach run . --bin $(RUN_TARGET)

clean:
	@rm -rf ./out

