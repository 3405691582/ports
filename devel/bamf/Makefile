V =		0.5
P =		4
COMMENT =	application matching library
DISTNAME =	bamf-${V}.${P}
CATEGORIES =	devel
REVISION =	1

SHARED_LIBS +=	bamf3                     0.0 # 2.0

HOMEPAGE =	https://launchpad.net/bamf
MAINTAINER =	Brian Callahan <bcallah@openbsd.org>

# LGPLv3+
PERMIT_PACKAGE =	Yes

WANTLIB =  X11 X11-xcb Xau Xcomposite Xcursor Xdamage Xext Xfixes Xi
WANTLIB += Xinerama Xrandr Xrender atk-1.0 atk-bridge-2.0 c cairo
WANTLIB += cairo-gobject epoxy execinfo expat fontconfig freetype
WANTLIB += fribidi gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0 gmodule-2.0
WANTLIB += gobject-2.0 graphite2 gtk-3 gtop-2.0 harfbuzz iconv intl kvm
WANTLIB += m pango-1.0 pangocairo-1.0 pangoft2-1.0 pixman-1 png pthread
WANTLIB += startup-notification-1 wnck-3 xcb xcb-render xcb-shm xcb-util
WANTLIB += z

SITES =		https://launchpad.net/bamf/${V}/${V}.${P}/+download/

COMPILER =	base-clang ports-gcc
COMPILER_LANGS = c

BUILD_DEPENDS =	devel/gobject-introspection \
		lang/vala

LIB_DEPENDS =	devel/libgtop2 \
		devel/libwnck3 \
		devel/startup-notification

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS =	--disable-gtk-doc \
			--disable-gtk-doc-html \
			--disable-gtk-doc-pdf \
			--disable-gtktest \
			--without-html-dir

USE_GMAKE =	Yes

# Does not work with base libtool.
USE_LIBTOOL =	gnu

# Tests use a deprecated framework.
NO_TEST =	Yes

# We don't need systemd or upstart scripts.
post-install:
	@rm -rf ${DESTDIR}/usr/lib
	@rm -rf ${PREFIX}/share/upstart

.include <bsd.port.mk>
