BASE=../../../..

LOCAL_CFLAGS=$(shell pkg-config --cflags shout libmpg123)
LOCAL_LDFLAGS=$(shell pkg-config --libs shout libmpg123) -lmp3lame

include $(BASE)/build/modmake.rules
