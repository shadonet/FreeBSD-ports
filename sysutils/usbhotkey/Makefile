# Created by: Nikos Ntarmos <ntarmos@ceid.upatras.gr>

PORTNAME=	usbhotkey
PORTVERSION=	0.4
PORTREVISION=	2
CATEGORIES=	sysutils
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Utility to remap USB keyboards under X11

LICENSE=	GPLv2

DEPRECATED=	Uses EOL Python 2.7 via devel/libhid
EXPIRATION_DATE=2021-06-23

LIB_DEPENDS=	libhid.so:devel/libhid \
		libXtst.so:x11/libXtst

USES=		compiler:c11 gmake localbase:ldflags
USE_RUBY=	yes
GNU_CONFIGURE=	yes

CPPFLAGS+=	-I${LOCALBASE}/include/ruby-${RUBY_VER} \
		-I${LOCALBASE}/include/ruby-${RUBY_VER}/${RUBY_ARCH}
LIBS+=		-lX11

CONFIGURE_ARGS=	--without-Imlib

.include <bsd.port.mk>
