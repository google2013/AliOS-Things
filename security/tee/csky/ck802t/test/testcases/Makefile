#
# Copyright (C) 2015 The YunOS Project. All rights reserved.
#

TEST_BED_TOP := ../test_bed/
TW_TOP := ../../src/tw/
CURRENT_BUILD := NTW
include $(TW_TOP)/tee.cfg
include $(TW_TOP)/Make.rules

SAMP_DIRS  := mem/ntw asc/ntw hash/ntw id2/ntw aes/ntw rsa/ntw rng/ntw

OBJS += ./mem/ntw/built-in.o    \
        ./asc/ntw/built-in.o    \
        ./hash/ntw/built-in.o  \
        ./aes/ntw/built-in.o    \
        ./rsa/ntw/built-in.o   \
        ./id2/ntw/built-in.o \
        ./rng/ntw/built-in.o


LIBS := test_stub.o

all: $(OBJS) $(LIBS)

$(LIBS): $(OBJS)
	$(LD) -r -o $(LIBS) $(OBJS)
	@ echo "Finish building $(LIBS)..."

$(OBJS):
	for dir in $(SAMP_DIRS); do $(MAKE) -C $$dir; done

clean:
	echo "Cleaning $(LIBS)..."
	for dir in $(SAMP_DIRS); do $(MAKE) clean -C $$dir; done
	rm -f $(OBJS) $(LIBS)

