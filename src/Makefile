BUILD			:= build
LIB				:= ninty-233.a
VPATH			:= sha1 sha256 ecc bigint/src
SOURCEFILES		:= sha1.c sha256.c ninty-233.cpp ecc.cpp BigIntegerUtils.cpp BigUnsignedInABase.cpp BigIntegerAlgorithms.cpp BigUnsigned.cpp BigInteger.cpp
OFILES			:= sha1.o sha256.o ninty-233.o ecc.o BigIntegerUtils.o BigUnsignedInABase.o BigIntegerAlgorithms.o BigUnsigned.o BigInteger.o

all: $(BUILD) $(OFILES) $(LIB)

%.o: %.c
	$(CXX) -Wno-deprecated -c $^ -o $(BUILD)/$@

%.o: %.cpp
	$(CXX) -Wno-deprecated -c $^ -o $(BUILD)/$@

$(BUILD):
	mkdir -p $@

$(LIB):
	cd $(BUILD) && ar rcs $@ $(OFILES)

clean:
	@echo clean ...
	@rm -rf $(BUILD)