COMMENT =	easy-to-use minimalistic disassembler library

DISTNAME =	udis86-1.7.2
CATEGORIES =	devel
REVISION =	12

SHARED_LIBS=	udis86		1.0

HOMEPAGE =	https://udis86.sourceforge.net/

MAINTAINER =	Paul Irofti <paul@irofti.net>

# BSD
PERMIT_PACKAGE =		Yes

SITES =		${SITE_SOURCEFORGE:=udis86/}

WANTLIB +=	c

MODULES =	lang/python

BUILD_DEPENDS =	devel/yasm \
		textproc/py-sphinx

CONFIGURE_STYLE =	autoconf
AUTOCONF_VERSION =	2.69
MAKE_ENV =		LIBudis86_VERSION=${LIBudis86_VERSION}

FAKE_FLAGS =	docdir=${PREFIX}/share/doc/udis86/x86

post-build:
	@cd ${WRKBUILD}/docs/manual \
		&& exec ${SETENV} ${MAKE_ENV} ${MAKE_PROGRAM} html-local

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/udis86/manual
	cd ${WRKBUILD}/docs/manual/html && \
		pax -rw * ${PREFIX}/share/doc/udis86/manual

.include <bsd.port.mk>
