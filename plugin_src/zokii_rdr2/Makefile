TARGET := zokii_rdr2
TOOLCHAIN := $(OO_PS4_TOOLCHAIN)
GH_SDK := $(GOLDHEN_SDK)
BUILD_DIR := build

CC := clang
LD := ld.lld
CREATE_FSELF := $(TOOLCHAIN)/bin/linux/create-fself

CFLAGS := --target=x86_64-pc-freebsd12-elf -fPIC -funwind-tables -c -D__USE_PRINTF__ \
          -isysroot $(TOOLCHAIN) -isystem $(TOOLCHAIN)/include -I$(GH_SDK)/include
LDFLAGS := -m elf_x86_64 -pie --script $(TOOLCHAIN)/link.x -e _init --eh-frame-hdr \
           -L$(TOOLCHAIN)/lib -L$(GH_SDK) -lSceLibcInternal -lGoldHEN_Hook -lkernel -lSceSysmodule

.PHONY: all clean
all: $(BUILD_DIR)/$(TARGET).prx

$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

$(BUILD_DIR)/main.o: source/main.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) -o $@ $<

$(BUILD_DIR)/$(TARGET).elf: $(BUILD_DIR)/main.o $(GH_SDK)/build/crtprx.o
	$(LD) $(GH_SDK)/build/crtprx.o $(BUILD_DIR)/main.o -o $@ $(LDFLAGS)

$(BUILD_DIR)/$(TARGET).prx: $(BUILD_DIR)/$(TARGET).elf
	$(CREATE_FSELF) -in=$< -out=$@ --lib=$@ --paid 0x3800000000000011

clean:
	rm -rf $(BUILD_DIR)
