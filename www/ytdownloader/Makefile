PORTNAME=	YTDownloader
DISTVERSIONPREFIX=	v
DISTVERSION=	3.18.1_2
CATEGORIES=	www
MASTER_SITES=	https://github.com/nxjosephofficial/ytDownloader/releases/download/${DISTVERSIONPREFIX}${DISTVERSION}/:0
DISTNAME=	${PORTNAME}_Linux_x86_64
DISTFILES=	${DISTNAME}${EXTRACT_SUFX}:0
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	nxjoseph@protonmail.com
COMMENT=	GUI video downloader supporting hundreds of sites
WWW=		https://github.com/aandrew-me/ytDownloader

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

ONLY_FOR_ARCHS=	amd64
LIB_DEPENDS=	libatk-1.0.so:accessibility/at-spi2-core \
		libatk-bridge-2.0.so:accessibility/at-spi2-core \
		libatspi.so:accessibility/at-spi2-core \
		libcups.so:print/cups \
		libdav1d.so:multimedia/dav1d \
		libdbus-1.so:devel/dbus \
		libdrm.so:graphics/libdrm \
		libepoll-shim.so:devel/libepoll-shim \
		libevent.so:devel/libevent \
		libexpat.so:textproc/expat2 \
		libffi.so:devel/libffi \
		libFLAC.so:audio/flac \
		libfontconfig.so:x11-fonts/fontconfig \
		libharfbuzz-subset.so:print/harfbuzz \
		libharfbuzz.so:print/harfbuzz \
		libicudata.so:devel/icu \
		libicui18n.so:devel/icu \
		libicuuc.so:devel/icu \
		libnspr4.so:devel/nspr \
		libnss3.so:security/nss \
		libnssutil3.so:security/nss \
		libopenh264.so:multimedia/openh264 \
		libopus.so:audio/opus \
		libpci.so:devel/libpci \
		libpipewire-0.3.so:multimedia/pipewire \
		libplc4.so:devel/nspr \
		libplds4.so:devel/nspr \
		libpng16.so:graphics/png \
		libsmime3.so:security/nss \
		libsndio.so:audio/sndio \
		libwayland-client.so:graphics/wayland \
		libwebp.so:graphics/webp \
		libwebpdemux.so:graphics/webp \
		libwebpmux.so:graphics/webp \
		libxkbcommon.so:x11/libxkbcommon \
		libxshmfence.so:x11/libxshmfence
RUN_DEPENDS=	ffmpeg:multimedia/ffmpeg \
		yt-dlp:www/yt-dlp

USES=		desktop-file-utils electronfix:30 gettext-runtime gl gnome jpeg \
		motif xorg zip
USE_GL=		egl gbm gl
USE_GNOME=	cairo gdkpixbuf2 glib20 gtk30 libxml2 libxslt pango
USE_XORG=	x11 xcb xcomposite xdamage xext xfixes xi xrandr xrender xtst

NO_BUILD=	yes
SUB_FILES=	ytdownloader

NO_WRKSUBDIR=	yes

ELECTRONFIX_MAIN_EXECUTABLE=	ytdownloader

do-install:
	cd ${WRKSRC} && \
		${COPYTREE_SHARE} \* ${STAGEDIR}${DATADIR}
	${INSTALL_SCRIPT} ${WRKDIR}/ytdownloader \
		${STAGEDIR}${PREFIX}/bin/ytdownloader
	${INSTALL_DATA} ${PATCHDIR}/ytdownloader.desktop \
		${STAGEDIR}${DESKTOPDIR}/ytdownloader.desktop
	${INSTALL_DATA} ${WRKSRC}/resources/app/resources/icon.png \
		${STAGEDIR}${PREFIX}/share/pixmaps/${PORTNAME}.png

.include <bsd.port.mk>
