COMMENT=	Google utilities written in Python

DISTNAME=	goopy-0.1
REVISION=	13
CATEGORIES=	devel
HOMEPAGE=	https://goog-goopy.sourceforge.net/

# BSD
PERMIT_PACKAGE=	Yes

SITES=		${SITE_SOURCEFORGE:=goog-goopy/}

MODULES=	lang/python

MODPY_PYBUILD=	setuptools

do-test:
	@cd ${WRKSRC}/goopy && ${MAKE_ENV} \
		PYTHONPATH=${WRKINST}${MODPY_SITEPKG} \
		${MODPY_BIN} ./functional_unittest.py

.include <bsd.port.mk>
