COMMENT=		library for retro-fitting legacy printer drivers

V=			2.1.1
DISTNAME=		libppd-${V}

SHARED_LIBS +=  ppd                  0.0      # 2.0

CATEGORIES=		print devel

HOMEPAGE=		https://github.com/OpenPrinting/libppd

MAINTAINER=		Antoine Jacoutot <ajacoutot@openbsd.org>

# Apache-2.0
PERMIT_PACKAGE=		Yes

SITES=		https://github.com/OpenPrinting/libppd/releases/download/${V}/

WANTLIB += ${COMPILER_LIBCXX} avahi-client avahi-common c crypto
WANTLIB += cups cupsfilters dbus-1 exif expat fontconfig z
WANTLIB += freetype gmp hogweed iconv idn2 intl jpeg lcms2 m nettle
WANTLIB += p11-kit png poppler-cpp qpdf ssl tasn1 tiff unistring

# -std=gnu11
COMPILER=		base-clang ports-gcc

USE_GMAKE=		Yes

# default is: --with-pdftops=hybrid (pdftops+gs)
BUILD_DEPENDS +=	print/ghostscript/gnu \
			print/poppler,-utils
RUN_DEPENDS +=		print/ghostscript/gnu \
			print/poppler,-utils

LIB_DEPENDS=		print/libcupsfilters

CONFIGURE_STYLE=	gnu

CONFIGURE_ARGS=		--disable-mutool \
			--enable-testppdfile

# XXX conflict with CUPS 2.X; wait for CUPS 3.X
#CONFIGURE_ARGS +=	--enable-ppdc-utils

# default to /usr/bin/pdftops
CONFIGURE_ARGS +=	--with-pdftops-path=${LOCALBASE}/bin/pdftops

DEBUG_PACKAGES=		${BUILD_PACKAGES}

.include <bsd.port.mk>
