SHARED_LIBS +=  srtp2                     6.0

COMMENT=	secure RTP library

GH_ACCOUNT=	cisco
GH_PROJECT=	libsrtp
GH_TAGNAME=	v2.7.0

CATEGORIES=	security telephony

# BSD
PERMIT_PACKAGE=	Yes

CONFIGURE_STYLE= gnu

MAKE_FLAGS=	SHAREDLIBVERSION=${LIBsrtp2_VERSION}
DEBUG_PACKAGES=	${BUILD_PACKAGES}

USE_GMAKE=	Yes
ALL_TARGET=	all shared_library
TEST_TARGET=	runtest

post-install:
	rm ${PREFIX}/lib/libsrtp2.so

.include <bsd.port.mk>
