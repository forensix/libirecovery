AR := ar
CP := cp
CC := gcc

UNAME := $(shell uname -s)

ifeq ($(UNAME),Darwin)
		CFLAGS = -I../libusbip/libusbip -I./include -I/usr/local/include -I/opt/local/include -I./include/libusb-1.0
		LDFLAGS = -L/usr/lib -L/opt/local/lib 
		LIBS = -lreadline -lusb-1.0 -framework CoreFoundation -framework IOKit
	
		IRECOVERY_TARGET = irecovery
		IRECOVERY_OBJECTS = irecovery.o libirecovery.a
		IRECOVERY_CFLAGS = $(CFLAGS)
		IRECOVERY_LDFLAGS =  $(LDFLAGS)
		IRECOVERY_LIBS = $(LIBS)
	
		LIBIRECOVERY_STATIC_TARGET = libirecovery.a
		LIBIRECOVERY_STATIC_OBJECTS = libirecovery.o
		LIBIRECOVERY_STATIC_CFLAGS = $(CFLAGS)
		LIBIRECOVERY_STATIC_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_STATIC_LIBS = $(LIBS)
	
		LIBIRECOVERY_SHARED_TARGET = libirecovery.dylib
		LIBIRECOVERY_SHARED_OBJECTS = libirecovery.o
		LIBIRECOVERY_SHARED_CFLAGS = $(CFLAGS)
		LIBIRECOVERY_SHARED_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_SHARED_LIBS = $(LIBS)
else
	ifeq ($(UNAME),MINGW32_NT-5.1)
		CFLAGS = -O3 -I include -I c:\mingw\include
		LDFLAGS = -L c:\mingw\lib -lreadline
		LIBS = -lreadline -lusb-1.0 -framework CoreFoundation -framework IOKit
	
		IRECOVERY_TARGET = irecovery.exe
		IRECOVERY_OBJECTS = irecovery.o
		IRECOVERY_CFLAGS = $(CFLAGS)
		IRECOVERY_LDFLAGS = $(LDFLAGS)
		IRECOVERY_LIBS = $(LIBS) libirecovery.a
	
		LIBIRECOVERY_STATIC_TARGET = libirecovery.a
		LIBIRECOVERY_STATIC_OBJECTS = libirecovery.o
		LIBIRECOVERY_STATIC_CFLAGS = $(CFLAGS)
		LIBIRECOVERY_STATIC_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_STATIC_LIBS = $(LIBS)
	
		LIBIRECOVERY_SHARED_TARGET = libirecovery.dll
		LIBIRECOVERY_SHARED_OBJECTS = libirecovery.o
		LIBIRECOVERY_SHARED_CFLAGS = $(CFLAGS)
		LIBIRECOVERY_SHARED_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_SHARED_LIBS = $(LIBS)
	else
		CFLAGS = -O3 -I../libusbip/libusbip -I./include -I/usr/include -I/usr/local/include -I./include/libusb-1.0
		LDFLAGS = -L/usr/lib -L/usr/local/lib
		LIBS = -lusb-1.0 -lreadline
		
		IRECOVERY_TARGET = irecovery
		IRECOVERY_OBJECTS = irecovery.o
		IRECOVERY_CFLAGS = $(CFLAGS)
		IRECOVERY_LDFLAGS = $(LDFLAGS)
		IRECOVERY_LIBS = $(LIBS)
	
		LIBIRECOVERY_STATIC_TARGET = libirecovery.a
		LIBIRECOVERY_STATIC_OBJECTS = libirecovery.o
		LIBIRECOVERY_STATIC_CFLAGS = $(CLFAGS)
		LIBIRECOVERY_STATIC_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_STATIC_LIBS = $(LIBS)
	
		LIBIRECOVERY_SHARED_TARGET = libirecovery.so
		LIBIRECOVERY_SHARED_OBJECTS = libirecovery.o
		LIBIRECOVERY_SHARED_CFLAGS = $(CFLAGS)
		LIBIRECOVERY_SHARED_LDFLAGS = $(LDFLAGS)
		LIBIRECOVERY_SHARED_LIBS = $(LIBS)
	endif
endif

LIBIRECOVERY_OBJECTS = libirecovery.o ../libusbip/libusbip/libusbip.a
IRECOVERY_OBJECTS = irecovery.o libirecovery.a ../libusbip/libusbip/libusbip.a

TARGETS = $(LIBIRECOVERY_STATIC_TARGET) $(IRECOVERY_TARGET)
OBJECTS = libirecovery.o irecovery.o

%.o: %.S
	$(CC) -c $(<) -o $(@) $(CFLAGS)

%.o: %.c
	$(CC) -c $(<) -o $(@) $(CFLAGS) 

$(LIBIRECOVERY_STATIC_TARGET): $(LIBIRECOVERY_STATIC_OBJECTS)
	$(AR) rs $(LIBIRECOVERY_STATIC_TARGET) $(LIBIRECOVERY_STATIC_OBJECTS)
	
$(LIBIRECOVERY_SHARED_TARGET): $(LIBIRECOVERY_SHARED_OBJECTS)

$(IRECOVERY_TARGET): $(IRECOVERY_OBJECTS)
	$(CC) -o $(IRECOVERY_TARGET) $(IRECOVERY_OBJECTS) $(IRECOVERY_CFLAGS) $(IRECOVERY_LDFLAGS) $(IRECOVERY_LIBS)

all: $(TARGETS)
	
		
clean:
	$(RM) $(LIBIRECOVERY_STATIC_TARGET) $(IRECOVERY_TARGET) *.o