COMMENT =		text-based audio player
DISTNAME =		siren-0.11
CATEGORIES =		audio
HOMEPAGE =		https://www.kariliq.nl/siren/
MAINTAINER =		Alexandre Ratchov <alex@caoua.org>

# ISC
PERMIT_PACKAGE =	Yes

SITES =			${HOMEPAGE}/dist/

# uses pledge()
WANTLIB +=		FLAC c curses faad mp4v2 mpg123 opusfile pthread sndfile
WANTLIB +=		sndio vorbisfile wavpack

LIB_DEPENDS =		audio/faad \
			audio/flac \
			audio/mpg123 \
			audio/libsndfile \
			audio/libvorbis \
			audio/opusfile \
			audio/wavpack \
			multimedia/libmp4v2

CONFIGURE_STYLE =	simple
CONFIGURE_ARGS =	prefix=${PREFIX} \
			ao=no \
			ffmpeg=no \
			mad=no \
			oss=no \
			portaudio=no \
			pulse=no \
			sun=no
CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"

NO_TEST =		Yes

.include <bsd.port.mk>
