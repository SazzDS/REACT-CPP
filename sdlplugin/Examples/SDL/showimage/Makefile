#
# SDL application Makefile
# type without args to build
# type run to execute
# type clean to clean sources
# type log to check application log
#

TARGET = showimage

all: $(TARGET)

CFLAGS = -Os -Wall -DANDROID -I${EXTERNAL_STORAGE}/CCPlusPlusNIDE/SDL/include

LDFLAGS = -shared ${EXTERNAL_STORAGE}/CCPlusPlusNIDE/SDL/lib/SDL_android_main.o -L${EXTERNAL_STORAGE}/CCPlusPlusNIDE/SDL/lib -lSDL2 -lSDL2_image -llog -lm

SDLRUN = am start $(shell am 2>&1| grep -q '\-\-user' && echo '--user 0') -n com.duy.c.cpp.compiler.sdlplugin/.sdlpluginActivity -e sdlmain

OBJS = $(TARGET).o

$(TARGET): $(OBJS)
	$(CC) -o lib$@.so $^ $(LDFLAGS)

clean:
		rm -f $(OBJS) lib$(TARGET).so

run: $(TARGET)
		$(SDLRUN) $(PWD)/lib$(TARGET).so

log:
	logcat -d | grep SDL
