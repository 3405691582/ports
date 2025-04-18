USE_NOBTCFI =	Yes
USE_WXNEEDED =	Yes
REVISION =	0

COMMENT =	calendar email todo and task application

DISTNAME =	merkuro-${VERSION}

CATEGORIES =	productivity x11

HOMEPAGE =	https://apps.kde.org/merkuro.calendar/

MAINTAINER =	Rafael Sadowski <rsadowski@openbsd.org>

SHARED_LIBS +=	MerkuroComponents         0.0 # 0.0
SHARED_LIBS +=	merkuro_contact           0.0 # 0.0

# GPLv3+, LGPL-2.1+
PERMIT_PACKAGE =	Yes

WANTLIB += ${COMPILER_LIBCXX} GL KF6CalendarCore KF6Codecs KF6ColorScheme
WANTLIB += KF6Completion KF6ConfigCore KF6ConfigGui KF6ConfigWidgets
WANTLIB += KF6Contacts KF6CoreAddons KF6Crash KF6DBusAddons KF6GuiAddons
WANTLIB += KF6I18n KF6I18nQml KF6ItemModels KF6KIOCore KF6Notifications
WANTLIB += KF6TextAutoCorrectionCore KF6TextAutoCorrectionWidgets
WANTLIB += KF6TextCustomEditor KF6TextTemplate KF6WidgetsAddons
WANTLIB += KF6WindowSystem KF6XmlGui KPim6AkonadiCalendar KPim6AkonadiContactCore
WANTLIB += KPim6AkonadiContactWidgets KPim6AkonadiCore KPim6AkonadiMime
WANTLIB += KPim6AkonadiWidgets KPim6CalendarUtils KPim6GrantleeTheme
WANTLIB += KPim6IMAP KPim6IdentityManagementCore KPim6IdentityManagementQuick
WANTLIB += KPim6IdentityManagementWidgets KPim6Libkdepim KPim6Libkleo
WANTLIB += KPim6MailCommon KPim6MailTransport KPim6Mbox KPim6MessageComposer
WANTLIB += KPim6MessageCore KPim6Mime KPim6MimeTreeParserCore
WANTLIB += KPim6PimCommon KPim6PimCommonAkonadi KPim6TextEdit
WANTLIB += KirigamiAddonsStatefulApp Qt6Core Qt6DBus Qt6Gui Qt6Network
WANTLIB += Qt6OpenGL Qt6Qml Qt6QmlMeta Qt6QmlModels Qt6QmlWorkerScript
WANTLIB += Qt6Quick Qt6QuickControls2 Qt6Widgets Qt6Xml X11 assuan
WANTLIB += c gpgme gpgmepp m qgpgmeqt6

BUILD_DEPENDS =	devel/boost \
		devel/gettext,-tools \
		devel/kf6/kiconthemes \
		devel/kf6/kirigami \
		devel/kf6/kitemviews \
		devel/kf6/knotifications \
		devel/kf6/kservice \
		devel/kf6/ktextwidgets \
		x11/kde-plasma/libplasma \
		devel/kf6/qqc2-desktop-style \
		devel/kf6/solid \
		devel/kf6/sonnet \
		misc/shared-mime-info

RUN_DEPENDS =	devel/desktop-file-utils \
		devel/kf6/kirigami \
		x11/kde-plasma/libplasma \
		devel/kf6/qqc2-desktop-style \
		x11/gtk+4,-guic

LIB_DEPENDS =	devel/kf6/kcalendarcore \
		devel/kf6/kcodecs \
		devel/kf6/kcolorscheme \
		devel/kf6/kcompletion \
		devel/kf6/kconfig \
		devel/kf6/kconfigwidgets \
		devel/kf6/kcontacts \
		devel/kf6/kcoreaddons \
		devel/kf6/kdbusaddons \
		devel/kf6/ki18n\
		devel/kf6/kio \
		devel/kf6/kitemmodels \
		devel/kf6/ktexttemplate \
		devel/kf6/kguiaddons \
		devel/kf6/kwidgetsaddons \
		devel/kf6/knotifications \
		graphics/kirigami-addons \
		devel/kf6/kwindowsystem \
		devel/kf6/kxmlgui \
		security/gpgme \
		security/libassuan \
		textproc/ktextaddons \
		devel/kf6/kcrash \
		security/gpgme,-qt \
		x11/kde-applications/akonadi-calendar>=${VERSION} \
		x11/kde-applications/akonadi-contacts>=${VERSION} \
		x11/kde-applications/akonadi-mime>=${VERSION} \
		x11/kde-applications/akonadi>=${VERSION} \
		x11/kde-applications/grantleetheme>=${VERSION} \
		x11/kde-applications/kcalutils>=${VERSION} \
		x11/kde-applications/kidentitymanagement>=${VERSION} \
		x11/kde-applications/kimap>=${VERSION} \
		x11/kde-applications/kmailtransport>=${VERSION} \
		x11/kde-applications/kmbox>=${VERSION} \
		x11/kde-applications/kmime>=${VERSION} \
		x11/kde-applications/kpimtextedit>=${VERSION} \
		x11/kde-applications/libkdepim>=${VERSION} \
		x11/kde-applications/libkleo>=${VERSION} \
		x11/kde-applications/mailcommon>=${VERSION} \
		x11/kde-applications/messagelib>=${VERSION} \
		x11/kde-applications/mimetreeparser>=${VERSION} \
		x11/kde-applications/pimcommon>=${VERSION} \
		x11/qt6/qtdeclarative \

.include <bsd.port.mk>
