BROKEN-sparc64 = Cannot determine how to allocate aligned memory on the target platform.

V =		2.15.2
COMMENT =	fast, compressed, persistent binary data store library for C
PKGNAME =	blosc2-${V}
CATEGORIES =	archivers

SHARED_LIBS +=	blosc2                     4.0 # 0.0

GH_ACCOUNT =	Blosc
GH_PROJECT =	c-blosc2
GH_TAGNAME =	v${V}
REVISION =	0

HOMEPAGE =	https://blosc.org/
MAINTAINER =	Martin Reindl <martin@catai.org>

# BSD
PERMIT_PACKAGE =	Yes

WANTLIB +=	m lz4 pthread z zstd

COMPILER =	base-clang ports-gcc
COMPILER_LANGS = c

MODULES =	devel/cmake

LIB_DEPENDS =	archivers/lz4 \
		archivers/zstd

CONFIGURE_ARGS =	-DPREFER_EXTERNAL_LZ4=ON \
			-DPREFER_EXTERNAL_ZLIB=ON \
			-DPREFER_EXTERNAL_ZSTD=ON

.include <bsd.port.mk>
