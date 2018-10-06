BUILD			:= build
LIB			:= ninty-233.a
VPATH			:= sha1 sha256 ecc bigint/src
SOURCEFILES		:= sha1.c sha256.c ninty-233.cpp ecc.cpp BigIntegerUtils.cpp BigUnsignedInABase.cpp BigIntegerAlgorithms.cpp BigUnsigned.cpp BigInteger.cpp
OFILES			:= sha1.o sha256.o ninty-233.o ecc.o BigIntegerUtils.o BigUnsignedInABase.o BigIntegerAlgorithms.o BigUnsigned.o BigInteger.o
CFLAGS			:= -c
CXXFLAGS		:= $(CFLAGS) -Wno-deprecated -std=c++17

ifeq ($(3DS), 1)
CC	:= /opt/devkitpro/devkitARM/bin/arm-none-eabi-gcc
CXX	:= /opt/devkitpro/devkitARM/bin/arm-none-eabi-g++
CFLAGS += -march=armv6k -mtune=mpcore -mfloat-abi=hard -mtp=soft -mword-relocations -fomit-frame-pointer -ffunction-sections -DARM11 -D_3DS
CXXFLAGS += -march=armv6k -mtune=mpcore -mfloat-abi=hard -mtp=soft -mword-relocations -fomit-frame-pointer -ffunction-sections -DARM11 -D_3DS
endif

all: $(BUILD) $(OFILES) $(LIB)

%.o: %.c
	@echo [$^]
	@$(CC) $(CFLAGS) $^ -o $(BUILD)/$@

%.o: %.cpp
	@echo [$^]
	@$(CXX) $(CXXFLAGS) $^ -o $(BUILD)/$@

$(BUILD):
	@echo CXX == $(CXX)
	@echo CXXFLAGS == $(CXXFLAGS)
	@mkdir -p $@

$(LIB):
	@echo Archiving library...
	@cd $(BUILD) && ar rcs $@ $(OFILES)

clean:
	@echo clean ...
	@rm -rf $(BUILD)