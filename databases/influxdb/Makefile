PORTNAME=	influxdb
DISTVERSIONPREFIX=	v
DISTVERSION=	1.8.6
CATEGORIES=	databases net-mgmt

MAINTAINER=	driesm.michiels@gmail.com
COMMENT=	Open-source distributed time series database

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

ONLY_FOR_ARCHS=	aarch64 amd64 armv6 armv7 i386
ONLY_FOR_ARCHS_REASON=	depends on go which is not supported in this architecture

USES=		go:modules

USE_RC_SUBR=	influxd

GO_MODULE=	github.com/influxdata/influxdb
GO_BUILDFLAGS=	-ldflags "-X main.version=${DISTVERSION}"
GO_TARGET=	./cmd/influxd \
		./cmd/influx \
		./cmd/influx_inspect \
		./cmd/influx_tsm \
		./cmd/influx_stress

SUB_LIST=	INFLUXD_USER=${INFLUXD_USER} \
		INFLUXD_GROUP=${INFLUXD_GROUP} \
		INFLUXD_DBDIR=${INFLUXD_DBDIR} \
		INFLUXD_PIDDIR=${INFLUXD_PIDDIR} \
		INFLUXD_LOGDIR=${INFLUXD_LOGDIR}

USERS=		${INFLUXD_USER}
GROUPS=		${INFLUXD_GROUP}

PLIST_SUB=	INFLUXD_USER=${INFLUXD_USER} \
		INFLUXD_GROUP=${INFLUXD_GROUP} \
		INFLUXD_DBDIR=${INFLUXD_DBDIR} \
		INFLUXD_PIDDIR=${INFLUXD_PIDDIR} \
		INFLUXD_LOGDIR=${INFLUXD_LOGDIR}

OPTIONS_DEFINE=	MANPAGES
OPTIONS_DEFAULT=MANPAGES
OPTIONS_SUB=	yes

MANPAGES_BUILD_DEPENDS=	xmlto:textproc/xmlto \
			asciidoc:textproc/asciidoc \
			docbook-xml>0:textproc/docbook-xml
MANPAGES_USES=	gmake

INFLUXD_DBDIR=	/var/db/${PORTNAME}/
INFLUXD_LOGDIR=	/var/log/${PORTNAME}/
INFLUXD_PIDDIR=	/var/run/${PORTNAME}/

INFLUXD_USER=	influxd
INFLUXD_GROUP=	influxd

.include <bsd.port.pre.mk>

.if ${OPSYS} == "FreeBSD"
SUB_LIST+=	INFLUXD_LOGCMD="daemon"
.else
SUB_LIST+=	INFLUXD_LOGCMD="logger"
.endif

do-build-MANPAGES-on:
	@cd ${WRKSRC}/man && ${SETENV} ${MAKE_ENV} ${MAKE_CMD}

do-install-MANPAGES-on:
	${INSTALL_MAN} ${WRKSRC}/man/*.1 ${STAGEDIR}${MANPREFIX}/man/man1

post-install:
	${MKDIR} ${STAGEDIR}${INFLUXD_DBDIR} \
	${STAGEDIR}${INFLUXD_PIDDIR} \
	${STAGEDIR}${INFLUXD_LOGDIR}
	@${SED} -i .bak -e \
		"s|/var/lib/influxdb|/var/db/influxdb|g" \
		${WRKSRC}/etc/config.sample.toml
	${INSTALL_DATA} \
		${WRKSRC}/etc/config.sample.toml \
		${STAGEDIR}${PREFIX}/etc/influxd.conf.sample

.include <bsd.port.post.mk>
