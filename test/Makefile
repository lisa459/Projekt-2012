#
# Makefile f�r NEO, GNU GCC (g++)
#
# Filkataloger d�r andra delar av programet finns.
NODE = ../Node
EDGE = ../Edge
NETWORK = ../Network
SET = ../Set


# Kompilator
#CCC = g++
CC = g++

# Kompilatorflaggor, l�gg till '-g' om kompilering f�r avlusning ska g�ras.
CCFLAGS += -std=c++11 -pedantic -Wall -Wextra

# Preprocessorflaggor, -I l�gger till en filkatalog i inkluderingss�kv�gen.
CPPFLAGS += -I$(NODE) -I$(SET) -I$(EDGE) -I$(NETWORK)

# L�nkflaggor - Fix f�r att l�sa lokala problem med C++ l�nkbibliotek.
LDFLAGS += -L/sw/gcc-$(GCC4_V)/lib -static-libstdc++

# Objektkodsmoduler som ing�r i den kompletta kalkylatorn.
OBJECTS = $(EDGE)/Edge.o $(NODE)/Node.o $(NETWORK)/Network.o ne_test.o

# Huvudm�l - skapas med kommandot 'make' eller 'make kalkylator'.
ne_test: $(OBJECTS) node edge network Makefile
	$(CC) $(CPPFLAGS) $(CCFLAGS) $(LDFLAGS) -o ne_test $(OBJECTS)

# Delm�l (flaggan -c avbryter innan l�nkning, objektkodsfil erh�lls)
ne_test.o: ne_test.cc $(NODE)/Node.h $(EDGE)/Edge.h $(SET)/Set.h  $(NETWORK)/Network.h
	$(CC) $(CPPFLAGS) $(CCFLAGS) -c ne_test.cc

node:
	cd ../Node; make

edge:
	cd ../Edge; make

network:
	cd ../Network; make

# 'make clean' tar bort objektkodsfiler och 'core' (minnesdump).
clean:
	@ \rm -rf *.o core

# 'make zap' tar �ven bort det k�rbara programmet och reservkopior (filer
# som slutar med tecknet '~').
zap: clean
	@ \rm -rf kalkylator *~

# Se upp vid eventuell �ndring, '*' f�r absolut inte finnas f�r sig!!!
#
# '@' medf�r att kommandot inte skrivs ut p� sk�rmen d� det utf�rs av make.
# 'rm' �r ett alias f�r 'rm -i' p� IDA:s system, '\rm' inneb�r att "original-
# versionen", utan flaggan '-i', anv�nds. 
