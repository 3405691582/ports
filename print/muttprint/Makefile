COMMENT =	pretty printing of your mails

DISTNAME =	muttprint-0.73
REVISION =	2

CATEGORIES =	print mail

HOMEPAGE =	https://muttprint.sourceforge.net

# GPLv2+
PERMIT_PACKAGE =	Yes

WANTLIB += c

SITES =			${SITE_SOURCEFORGE:=muttprint/}

RUN_DEPENDS =		converters/p5-Text-Iconv \
			devel/p5-Time-TimeDate \
			graphics/ImageMagick \
			print/psutils \
			print/texlive/base \
			print/texlive/texmf,-full

SEPARATE_BUILD =	Yes
CONFIGURE_STYLE =	autoreconf

AUTOCONF_VERSION =	2.69
AUTOMAKE_VERSION =	1.15

post-patch:
	perl -pi -e 'print "=encoding latin1\n" if $$. == 1; close ARGV if eof;' \
		${WRKSRC}/doc/manpages/{de,en,es,it}/muttprint.pod

.include <bsd.port.mk>
