COMMENT =		library for processing panoramic images
DISTNAME =		libpano13-2.9.22

SHARED_LIBS +=		pano13               3.0

CATEGORIES =		graphics
HOMEPAGE =		https://panotools.sourceforge.net/

# GPLv2+
PERMIT_PACKAGE =	Yes

WANTLIB +=		c jpeg m png tiff z

SITES =			${SITE_SOURCEFORGE:=panotools/}

MODULES =		devel/cmake

LIB_DEPENDS =		graphics/jpeg \
			graphics/png \
			graphics/tiff

FIX_CRLF_FILES =	CMakeLists.txt

.include <bsd.port.mk>
