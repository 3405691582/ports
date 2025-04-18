V =			0.5.11
COMMENT =		document viewer for PDF and other formats with a vi-like UI
DISTNAME =		zathura-${V}
CATEGORIES =		textproc x11
EXTRACT_SUFX =		.tar.xz

HOMEPAGE =		https://pwmt.org/projects/zathura/

# MIT
PERMIT_PACKAGE =	Yes

WANTLIB += c cairo gio-2.0 girara-gtk3 glib-2.0 gmodule-2.0 gobject-2.0
WANTLIB += gdk-3 gtk-3 intl json-glib-1.0 m magic pango-1.0 sqlite3 synctex

SITES =		https://pwmt.org/projects/zathura/download/

MODULES=	devel/meson
BUILD_DEPENDS =	textproc/py-docutils \
		devel/gettext,-tools \
		textproc/py-sphinx
RUN_DEPENDS =	devel/desktop-file-utils \
		x11/gtk+4,-guic
LIB_DEPENDS =	databases/sqlite3 \
		devel/libmagic \
		x11/girara>=0.4.5 \
		print/texlive/base,-synctex

COMPILER =	base-clang ports-gcc
COMPILER_LANGS = c
CONFIGURE_ENV +=	LDFLAGS=-L${LOCALBASE}/lib
CONFIGURE_ARGS +=	-Dsynctex=enabled \
			-Dseccomp=disabled \
			-Dlandlock=disabled \
			-Dtests=disabled

TEST_DEPENDS =	devel/check
TEST_TARGET =	test
TEST_IS_INTERACTIVE =X11

post-install:
	# install placeholder for plugins
	${INSTALL_DATA_DIR} ${PREFIX}/lib/zathura

.include <bsd.port.mk>
