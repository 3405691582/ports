COMMENT=	Python bindings for Qt5

MODPY_DISTV=	5.15.11
DISTNAME=	PyQt5-${MODPY_DISTV}
PKGNAME=	py-qt5-${MODPY_DISTV}
REVISION=	0

CATEGORIES=	x11 devel

HOMEPAGE=	https://www.riverbankcomputing.com/software/pyqt/intro

# GPLv3 (or commercial)
# https://www.riverbankcomputing.com/commercial/license-faq
PERMIT_PACKAGE=	Yes

WANTLIB += ${COMPILER_LIBCXX} GL Qt5Bluetooth Qt5Core Qt5DBus
WANTLIB += Qt5Designer Qt5Gui Qt5Help Qt5Location Qt5Multimedia
WANTLIB += Qt5MultimediaWidgets Qt5Network Qt5Nfc Qt5OpenGL Qt5Positioning
WANTLIB += Qt5PositioningQuick Qt5PrintSupport Qt5Qml Qt5QmlModels
WANTLIB += Qt5Quick Qt5QuickWidgets Qt5RemoteObjects Qt5Sensors
WANTLIB += Qt5SerialPort Qt5Sql Qt5Svg Qt5Test Qt5TextToSpeech
WANTLIB += Qt5WebChannel Qt5WebKit Qt5WebKitWidgets Qt5WebSockets
WANTLIB += Qt5Widgets Qt5X11Extras Qt5Xml Qt5XmlPatterns dbus-1
WANTLIB += m ${MODPY_WANTLIB}

BUILD_DEPENDS=	devel/py-qt-builder \
		devel/py-ply \
		devel/py-setuptools \
		x11/dbus-python

RUN_DEPENDS=	devel/py-sip>=5.5.0v0 \
		x11/py-sip-qt5>=12.12 \
		devel/py-ply \
		x11/dbus-python

LIB_DEPENDS=	${MODPY_LIB_DEPENDS} \
		x11/qt5/qtconnectivity \
		x11/qt5/qtdeclarative \
		x11/qt5/qtlocation \
		x11/qt5/qtmultimedia \
		x11/qt5/qtremoteobjects \
		x11/qt5/qtsensors \
		x11/qt5/qtserialport \
		x11/qt5/qtspeech \
		x11/qt5/qtsvg \
		x11/qt5/qttools \
		x11/qt5/qtwebchannel \
		x11/qt5/qtwebkit \
		x11/qt5/qtwebsockets \
		x11/qt5/qtx11extras \
		x11/qt5/qtxmlpatterns

NO_TEST=	Yes

MODULES=	lang/python \
		x11/qt5
MODPY_PI=	Yes

# https://www.riverbankcomputing.com/static/Docs/PyQt5/installation.html#building-pyqt5
CONFIGURE_STYLE= simple
CONFIGURE_SCRIPT= ${LOCALBASE}/bin/sip-build
CONFIGURE_ARGS =	--verbose --confirm-license

MAKE_FLAGS=	-C build \
		CC=${CC} \
		CXX=${CXX} \
		COPTS="${CFLAGS}" \
		CXXOPTS="${CXXFLAGS}"

FAKE_FLAGS=	INSTALL_ROOT=${DESTDIR}

post-extract:
	# Needed to run sip-6.5+ sip-build
	ln -sf ${MODQT5_QMAKE} ${WRKDIR}/bin/qmake

post-install:
	${MODPY_COMPILEALL} \
	    ${WRKINST}/${MODPY_SITEPKG}/PyQt5/uic/port_v3

.include <bsd.port.mk>
