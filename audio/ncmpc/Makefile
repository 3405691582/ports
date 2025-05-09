BROKEN-sparc64= SocketAddress.hxx:16:10: fatal error: span: No such file or directory

COMMENT=		curses based frontend for mpd

VER=			0.52
DISTNAME=		ncmpc-${VER}
EPOCH=			0
CATEGORIES=		audio

MAINTAINER =		Landry Breuil <landry@openbsd.org>
HOMEPAGE=		https://www.musicpd.org/clients/ncmpc/

# GPLv2
PERMIT_PACKAGE=	Yes

# make sure to regen WANTLIB on ld.lld arches (-Wl,--as-needed)
WANTLIB +=	${COMPILER_LIBCXX} c curses iconv intl m mpdclient>=1
WANTLIB +=	pcre2-8 fmt

SITES=			https://www.musicpd.org/download/ncmpc/${VER:R}/

EXTRACT_SUFX=		.tar.xz

# c++17
COMPILER =		base-clang ports-gcc

MODULES=		devel/meson

BUILD_DEPENDS=		devel/boost \
			devel/gettext,-tools \
			textproc/py-sphinx

LIB_DEPENDS=		audio/libmpdclient>=2.20 \
			devel/fmt \
			devel/gettext,-runtime \
			devel/pcre2

CONFIGURE_ARGS=		-Dlirc=disabled \
			-Dhtml_manual=false \
			-Dlocale=enabled \
			-Dmouse=enabled

# disable meson's default of using "-Wl,--as-needed" on ld.bfd arches;
# build failures due to undefined references are often seen.
.include <bsd.port.arch.mk>
.if !${PROPERTIES:Mlld}
CONFIGURE_ARGS +=	-Db_asneeded=false
.endif

CONFIGURE_ENV=		CPP=${CPP} \
			CPPFLAGS="-D_GNU_SOURCE \
				  -D_DEFAULT_SOURCE \
				  -I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib -lintl"

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/ncmpc
	mv ${PREFIX}/share/doc/ncmpc/{config.sample,keys.sample,ncmpc.lirc} \
		${PREFIX}/share/examples/ncmpc/

.include <bsd.port.mk>
