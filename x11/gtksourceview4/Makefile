COMMENT=		text widget that extends the GTK3 GtkTextView widget

GNOME_PROJECT=		gtksourceview
GNOME_VERSION=		4.8.4
PKGNAME=		${GNOME_PROJECT}4-${GNOME_VERSION}
REVISION=		1

SHARED_LIBS += gtksourceview-4           0.0 # 0.0.0

CATEGORIES=		x11

MAJOR_VERSION=		4.0
SUBST_VARS=		MAJOR_VERSION

MAINTAINER=		Antoine Jacoutot <ajacoutot@openbsd.org>

# GPLv2/LGPLv2.1
PERMIT_PACKAGE=	Yes

COMPILER=		base-clang ports-gcc
COMPILER_LANGS=		c

WANTLIB += atk-1.0 cairo fribidi gdk-3 gdk_pixbuf-2.0 gio-2.0
WANTLIB += glib-2.0 gobject-2.0 gtk-3 intl m pango-1.0 pangocairo-1.0
WANTLIB += xml2

MODULES=		devel/meson \
			x11/gnome

LIB_DEPENDS=		textproc/libxml \
			x11/gtk+3

MODGNOME_TOOLS +=	gobject-introspection vala

TEST_IS_INTERACTIVE=	x11

DEBUG_PACKAGES =	${BUILD_PACKAGES}

.include <bsd.port.mk>
