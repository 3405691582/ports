COMMENT=	MS-Explorer like file manager for X

DISTNAME=	xfe-1.46.2
EXTRACT_SUFX=	.tar.xz
REVISION=	1
CATEGORIES=	x11

HOMEPAGE=	http://roland65.free.fr/xfe/
MAINTAINER=	Brian Callahan <bcallah@openbsd.org>

# GPLv2+
PERMIT_PACKAGE=	Yes

WANTLIB += ${COMPILER_LIBCXX} FOX-1.6 X11 X11-xcb Xft Xrandr c
WANTLIB += fontconfig freetype iconv intl m png util xcb xcb-util

COMPILER =		base-clang ports-gcc base-gcc

SITES=		${SITE_SOURCEFORGE:=xfe/}

MODULES=	textproc/intltool

BUILD_DEPENDS =	sysutils/polkit

LIB_DEPENDS=	devel/fox

RUN_DEPENDS=	devel/desktop-file-utils \
		x11/gtk+4,-guic

USE_GMAKE=	Yes

CONFIGURE_STYLE=gnu
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include \
			-I${LOCALBASE}/include/fox-1.6 \
			-I${X11BASE}/include \
			-I${X11BASE}/include/freetype2" \
		LDFLAGS="-L${LOCALBASE}/lib \
			-L${X11BASE}/lib -lXft -pthread"

pre-configure:
	sed -i "s,-O2,,g" ${WRKSRC}/configure

.include <bsd.port.mk>
