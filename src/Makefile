VERSION=unknown

# Device build
STAGING_DIR=/srv/preware/build/staging/armv7
ifeq ($(shell uname -s),Darwin)
CC=/opt/PalmPDK/arm-gcc/bin/arm-none-linux-gnueabi-gcc
else
CC=/srv/preware/build/toolchain/cs07q3armel/build/arm-2007q3/bin/arm-none-linux-gnueabi-gcc
endif

# Emulator build
# STAGING_DIR=/srv/preware/build/staging/i686
# CC=/srv/preware/build/toolchain/i686-unknown-linux-gnu/build/i686-unknown-linux-gnu/bin/i686-unknown-linux-gnu-gcc

CPPFLAGS := -g -DVERSION=\"${VERSION}\" -I${STAGING_DIR}/usr/include/glib-2.0 -I${STAGING_DIR}/usr/lib/glib-2.0/include -I${STAGING_DIR}/usr/include
LDFLAGS  := -g -L${STAGING_DIR}/usr/lib -llunaservice -lmjson -lglib-2.0 -lpthread

gehrpelcg: gehrpelcg.o luna_service.o luna_methods.o

HOST = cdma-pre

install: gehrpelcg
#	- ssh root@${HOST} killall org.webosinternals.gehrpelcg
#	scp gehrpelcg root@${HOST}:/var/usr/sbin/org.webosinternals.gehrpelcg.new
#	ssh root@${HOST} mv /var/usr/sbin/org.webosinternals.gehrpelcg.new /var/usr/sbin/org.webosinternals.gehrpelcg
	novacom put file://home/root/luna_methods.c < luna_methods.c
	novacom put file://home/root/gehrpelcg < gehrpelcg

clobber:
	rm -rf *.o gehrpelcg
