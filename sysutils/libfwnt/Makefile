COMMENT =	library for Windows NT data types

VERSION = 	20191222
DISTNAME =	libfwnt-alpha-${VERSION}
PKGNAME =	${DISTNAME:S/-alpha//}
REVISION =	5

SHARED_LIBS +=  fwnt                       0.0 # 1.0

CATEGORIES =	sysutils security

HOMEPAGE =	https://github.com/libyal/libfwnt/wiki

SITES =		https://github.com/libyal/libfwnt/releases/download/${VERSION}/

MAINTAINER =	Remi Pointel <rpointel@openbsd.org>

# LGPLv3+
PERMIT_PACKAGE =	Yes

WANTLIB += iconv intl m pthread util ${MODPY_WANTLIB}

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS +=	--enable-python3 --disable-nls

WRKDIST =	${WRKDIR}/${PKGNAME}

MODULES +=	lang/python

BUILD_DEPENDS =	devel/py-setuptools

TEST_DEPENDS += shells/bash

pre-test:
	sed -i s,#!/bin/bash,#!/${LOCALBASE}/bin/bash, ${WRKSRC}/tests/test_*.sh


.include <bsd.port.mk>
