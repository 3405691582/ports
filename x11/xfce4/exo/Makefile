COMMENT=	Xfce4 extension library

XFCE_PROJECT=	exo
REVISION=	0

SHARED_LIBS=	exo-2	1.1 # 1.0

# GPLv2/LGPLv2
PERMIT_PACKAGE=	Yes

MODULES=	x11/xfce4
MODXFCE_DESKTOP_FILE=	Yes

CONFIGURE_ENV=	ac_cv_header_sys_ucred_h=yes \
		ac_cv_header_sys_mount_h=yes

LIB_DEPENDS=	x11/xfce4/libxfce4ui>=4.15.1 \
		x11/xfce4/libxfce4util>=4.17.2

FAKE_FLAGS=	defaultsdir=${PREFIX}/share/examples/exo

WANTLIB=	ICE SM X11 Xcomposite Xcursor Xdamage Xext Xau Xdmcp jpeg \
		Xfixes Xi Xinerama Xrandr Xrender fribidi atk-1.0 atspi c cairo \
		dbus-1 expat fontconfig freetype gdk_pixbuf-2.0 gio-2.0 glib-2.0 \
		gmodule-2.0 gobject-2.0 gthread-2.0 xcb-util xfce4ui-2 \
		m pango-1.0 pangocairo-1.0 pangoft2-1.0 pcre2-8 pixman-1 \
		png pthread z xcb X11-xcb startup-notification-1 \
		xcb-render xfce4util xcb-shm ffi harfbuzz graphite2 iconv intl \
		epoll-shim wayland-client wayland-cursor wayland-egl xfconf-0 xkbcommon \
		atk-bridge-2.0 cairo-gobject epoxy gdk-3 gtk-3 ${COMPILER_LIBCXX}

.include <bsd.port.mk>
