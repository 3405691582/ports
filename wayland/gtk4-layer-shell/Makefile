COMMENT =	desktop components for Wayland using the Layer Shell proto

GH_TAGNAME =	v1.1.1
GH_ACCOUNT =	wmww
GH_PROJECT =	gtk4-layer-shell

CATEGORIES =	wayland
SHARED_LIBS +=	gtk4-layer-shell 1.0 # 0.0

# MIT
PERMIT_PACKAGE =	Yes

# C11
COMPILER =		base-clang ports-gcc
COMPILER_LANGS =	c

MODULES =	devel/meson
CONFIGURE_ARGS =-Dexamples=true

BUILD_DEPENDS =	devel/gobject-introspection \
		lang/vala \
		wayland/wayland-protocols

LIB_DEPENDS =	x11/gtk+4
WANTLIB +=	c gio-2.0 glib-2.0 gobject-2.0 gtk-4 wayland-client

CFLAGS +=	-L${X11BASE}/lib

.include <bsd.port.mk>
