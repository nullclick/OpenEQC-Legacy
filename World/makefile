APP=world
SF= ../Common/Source/classes.o ../Common/Source/database.o ../Common/Source/EQFragment.o ../Common/Source/EQPacket.o \
	../Common/Source/EQPacketManager.o ../Common/Source/MiscFunctions.o ../Common/Source/moremath.o \
	../Common/Source/Mutex.o ../Common/Source/packet_dump.o ../Common/Source/packet_dump_file.o ../Common/Source/races.o \
	../Common/Source/packet_functions.o ../Common/Source/timer.o ../Common/Source/unix.o \
	./Source/client.o ./Source/console.o ./Source/LoginServer.o ./Source/net.o ./Source/zoneserver.o \
	../PEQEmu/Source/PEQException.o	../PEQEmu/Source/PEQUtils.o

CC=gcc
LINKER=gcc
DFLAGS=-DDEBUG=5 -DEQDEBUG=5 -DSHAREMEM -DCATCH_CRASH -DNO_PIDLOG -DFIELD_ITEMS -DIRC -Di386 -DAPP_OPCODE_SIZE=2
WFLAGS=-Wall -Wuninitialized -Wwrite-strings -Wcast-qual -Wcomment -Wcast-align -Wno-deprecated
COPTS=$(WFLAGS) -g -march=i686 -O -pthread -pipe -DFX -D_GNU_SOURCE -DINVERSEXY -DWORLD $(DFLAGS) -I/usr/include/mysql -I/usr/mysql/include -I../Common/Include/ -I../PEQEmu/Include
LINKOPTS=-rdynamic -L. -lstdc++ -lm -lz -L/usr/lib/mysql -L/usr/mysql/lib -lmysqlclient -ldl
all: $(APP)

$(APP): $(SF)
	$(LINKER) $(COPTS) $(OBJS) $^ $(LINKOPTS) -o $@

clean:
	rm -f $(SF) $(APP)

%.o: %.cpp
	$(CC) -c $(COPTS) $< -o $@

.obj/%.o: ../Common/Source/%.cpp ../Common/Source/%.h
	mkdir -p .obj
	$(CC) $(COPTS) -c $< -o $@
	

