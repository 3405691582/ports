PORTROACH=		limit:^2\.28

COMMENT=		Python bindings for glib2 gobject (deprecated)

GNOME_PROJECT=		pygobject
GNOME_VERSION=		2.28.7

PKGNAME=		py-gobject-${GNOME_VERSION}
EPOCH=			0
REVISION=		1

CATEGORIES=		devel

SHARED_LIBS +=  pyglib-2.0-python${MODPY_VERSION} 2.0      # .0.0

HOMEPAGE=		http://www.pygtk.org/

MAINTAINER=		Antoine Jacoutot <ajacoutot@openbsd.org>

# LGPLv2.1
PERMIT_PACKAGE=	Yes

WANTLIB =  ffi gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0 gthread-2.0
WANTLIB += iconv intl pcre2-8 pthread z

MODULES=		lang/python \
			x11/gnome
MODPY_VERSION =	${MODPY_DEFAULT_VERSION_2}

LIB_DEPENDS=		devel/glib2

CONFIGURE_STYLE=	gnu

TEST_DEPENDS=		${FULLPKGNAME}:${BUILD_PKGPATH}
TEST_IS_INTERACTIVE=	x11

post-install:
	${MODPY_COMPILEALL} ${PREFIX}/share/pygobject/2.0/codegen
	rm ${WRKINST}/${MODPY_SITEPKG}/*/{,*}/*.{a,la}

.include <bsd.port.mk>
