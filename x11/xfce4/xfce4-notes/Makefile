COMMENT=	Xfce4 sticky notes panel plugin

XFCE_VERSION=	1.11.2
XFCE_PLUGIN=	notes

# GPLv2
PERMIT_PACKAGE=	Yes

MODULES=	x11/xfce4
LIB_DEPENDS +=	x11/gtksourceview4
MODXFCE_DESKTOP_FILE =	Yes
MODXFCE_ICON_CACHE=	Yes

WANTLIB += ${COMPILER_LIBCXX} ICE SM X11 X11-xcb Xcomposite Xcursor
WANTLIB += Xdamage Xext Xfixes Xi Xinerama Xrandr Xrender atk-1.0
WANTLIB += atk-bridge-2.0 c cairo cairo-gobject epoxy expat ffi
WANTLIB += fontconfig freetype fribidi gdk-3 gdk_pixbuf-2.0 gio-2.0
WANTLIB += glib-2.0 gmodule-2.0 gobject-2.0 graphite2 gthread-2.0
WANTLIB += gtk-3 harfbuzz iconv intl m pango-1.0 pangocairo-1.0
WANTLIB += pangoft2-1.0 pcre2-8 pixman-1 png startup-notification-1
WANTLIB += xcb xcb-render xcb-shm xcb-util xfce4ui-2 xfce4util
WANTLIB += epoll-shim wayland-client wayland-cursor wayland-egl
WANTLIB += xkbcommon xfconf-0 z Xau Xdmcp jpeg atspi dbus-1
WANTLIB += gtk-layer-shell gtksourceview-4 lzma xml2

FAKE_FLAGS =	autostartdir=${PREFIX}/share/examples/xfce4-notes

.include <bsd.port.mk>
