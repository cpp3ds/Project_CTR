# Makerom Sources
UTILS_OBJS = utils.o dir.o utf.o keyset.o titleid.o
CIA_OBJS = cia.o cia_read.o certs.o tik.o tmd.o tmd_read.o
NCCH_OBJS = ncch.o exheader.o accessdesc.o exefs.o elf.o romfs.o romfs_import.o romfs_binary.o  
NCSD_OBJS = ncsd.o  
SETTINGS_OBJS = usersettings.o yamlsettings.o
LIB_API_OBJS = crypto.o yaml_ctr.o blz.o

OBJS = makerom.o $(UTILS_OBJS) $(LIB_API_OBJS) $(SETTINGS_OBJS) $(NCSD_OBJS) $(NCCH_OBJS) $(CIA_OBJS)

# Libraries
POLAR_OBJS = polarssl/aes.o polarssl/bignum.o polarssl/rsa.o polarssl/sha1.o polarssl/sha2.o polarssl/padlock.o polarssl/md.o polarssl/md_wrap.o polarssl/md2.o polarssl/md4.o polarssl/md5.o polarssl/sha4.o polarssl/base64.o polarssl/cipher.o polarssl/cipher_wrap.o polarssl/camellia.o polarssl/des.o polarssl/blowfish.o
YAML_OBJS = libyaml/api.o libyaml/dumper.o libyaml/emitter.o libyaml/loader.o libyaml/parser.o libyaml/reader.o libyaml/scanner.o libyaml/writer.o

# Compiler Settings
LIBS = -static-libgcc -static-libstdc++
CXXFLAGS = -I.
CFLAGS = --std=c99 -Wall -I. -DMAKEROM_VER_MAJOR=$(VER_MAJOR) -DMAKEROM_VER_MINOR=$(VER_MINOR) $(MAKEROM_BUILD_FLAGS) -m64
CC = gcc
 
# MAKEROM Build Settings
MAKEROM_BUILD_FLAGS = #-DPUBLIC_BUILD #-DDEBUG
VER_MAJOR = 0
VER_MINOR = 8
OUTPUT = makerom

main: build

rebuild: clean build

build: $(OBJS) $(POLAR_OBJS) $(YAML_OBJS)
	g++ -o $(OUTPUT) $(LIBS) $(OBJS) $(POLAR_OBJS) $(YAML_OBJS) -m64

clean:
	rm -rf $(OUTPUT) $(OBJS) $(POLAR_OBJS) $(YAML_OBJS) *.cci *.cia *.cxi *.cfa
	
# Windows compatibility
rebuildwin: cleanwin build
cleanwin:
	del /Q objs $(OUTPUT).exe *.o polarssl\*.o libyaml\*.o *.cci *.cia *.cxi *.cfa