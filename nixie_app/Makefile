CROSS_COMPILE ?= arm-angstrom-linux-gnueabi-

CC = $(CROSS_COMPILE)gcc
#CFLAGS = -I/usr/local/include -DDEBUG
CFLAGS = -I/usr/local/include
LDFLAGS = -L/usr/local/lib -lprussdrv -lpthread
PASM = pasm

DATA_PRU = pru0_nixie.bin
LDR = nixie_app

all: $(LDR) $(DATA_PRU)

$(LDR): $(basename $(LDR)).c
	$(CC) $(CFLAGS) -o $@ $^ $(LDFLAGS)

$(DATA_PRU): $(basename $(DATA_PRU)).p
	$(PASM) -b $^

.PHONY: clean

clean:
	rm -f *~ *.o $(LDR) $(DATA_PRU)
