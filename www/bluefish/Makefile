COMMENT=		HTML editor for experienced web designers

DISTNAME=		bluefish-2.2.16

CATEGORIES=		www editors

HOMEPAGE=		https://bluefish.openoffice.nl/

# GPLv3
PERMIT_PACKAGE=	Yes

WANTLIB += ${COMPILER_LIBCXX} X11 Xau Xcomposite Xcursor Xdamage
WANTLIB += Xdmcp Xext Xfixes Xi Xinerama Xrandr Xrender aspell
WANTLIB += atk-1.0 atk-bridge-2.0 atspi c cairo cairo-gobject
WANTLIB += dbus-1 enchant-2 epoll-shim epoxy expat ffi fontconfig
WANTLIB += freetype fribidi gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 graphite2 gthread-2.0 gtk-3
WANTLIB += gucharmap_2_90 harfbuzz iconv intl jpeg lzma m pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre2-8 pixman-1 png python3.12
WANTLIB += util wayland-client wayland-cursor wayland-egl xcb
WANTLIB += xcb-render xcb-shm xkbcommon xml2 z

SITES=			https://www.bennewitz.com/bluefish/stable/source/

COMPILER=		base-clang ports-gcc base-gcc

MODULES=		lang/python \
			textproc/intltool

RUN_DEPENDS=		devel/desktop-file-utils \
			misc/shared-mime-info \
			x11/gtk+4,-guic

LIB_DEPENDS=		textproc/enchant2 \
			x11/gnome/gucharmap

CONFIGURE_STYLE=	autoreconf
AUTOCONF_VERSION=	2.69
AUTOMAKE_VERSION=	1.16

CONFIGURE_ENV=		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"
CONFIGURE_ARGS=		--with-freedesktop_org-menu='${PREFIX}/share/applications/' \
			--disable-update-databases

USE_GMAKE=		Yes

post-install:
	rm ${PREFIX}/lib/bluefish/*.{a,la}
# XXX not fully py3 ready although it needs it
# (checking whether /usr/local/bin/python2.7 version is >= 3.3... no)
	${MODPY_COMPILEALL} ${PREFIX}/share/bluefish || true

.include <bsd.port.mk>
