COMMENT =	wallpaper setting utility for X

V =		0.7.6
DISTNAME =	xwallpaper-${V}

CATEGORIES =	x11 graphics

HOMEPAGE =	https://github.com/stoeckmann/xwallpaper

MAINTAINER =	Rafael Sadowski <rsadowski@openbsd.org>

# ISC
PERMIT_PACKAGE =	Yes

# uses pledge()
WANTLIB += X11 Xpm c jpeg pixman-1 png xcb xcb-image xcb-randr
WANTLIB += xcb-shm xcb-util

SITES =	https://github.com/stoeckmann/xwallpaper/releases/download/v${V}/

DISTFILES =	${DISTNAME}_1{${DISTNAME}}${EXTRACT_SUFX}
EXTRACT_SUFX =	.tar.xz

LIB_DEPENDS +=	graphics/jpeg \
		graphics/png

CONFIGURE_STYLE =	gnu

CONFIGURE_ENV +=	CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"

NO_TEST = 	Yes

.include <bsd.port.mk>
