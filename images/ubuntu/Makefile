.MAKEFLAGS: -I${../../share:L:tA}

.ifndef VERSION
.error "You need to define VERSION="
.endif

PARENT_IMAGE =	ubuntu/cloudimg:${VERSION}
BUILD_COMMAND =	./build.sh ${VERSION}
CLEAN_FILES +=	_bin manifest.json

prepare: udev.deb

udev.deb:
	rm -rf _bin
	mkdir _bin
	ln -s `which gtar` _bin/tar
	env PATH=${.CURDIR}/_bin:$$PATH fpm -a all -p $@ -t deb -s empty -n ${@:R} --version 0 --epoch 99

.include "jetpack.image.mk"
