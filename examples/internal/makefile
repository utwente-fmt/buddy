# --------------------------------
# Makefile for internal tests
# --------------------------------

# --- Compiler flags
CFLAGS = -g -pedantic -Wall -ansi -L../../src -I../../src

# --- C++ compiler
CPP = g++

# --- C compiler
CC = gcc


# --- Do not touch ---

.SUFFIXES: .cxx .c

.cxx.o:
	$(CPP) $(CFLAGS) -c $<

.c.o:
	$(CC) $(CFLAGS) -c $<

bddtest:	bddtest.o bddlib
	$(CPP) $(CFLAGS) bddtest.o -o bddtest -lbdd -lm

bddlib:
	cd ../..; make

clean:
	rm -f *~
	rm -f *.o
	rm -f bddtest

bddtest.o:	../../src/bdd.h


