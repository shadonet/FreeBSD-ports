PORTNAME=	minio-client
PORTVERSION=	${GH_TAGNAME:S/RELEASE.//:S/Z//:S/T/-/:S/-/./g}
CATEGORIES=	www

MAINTAINER=	jhixson@FreeBSD.org
COMMENT=	Replacement for ls, cp, mkdir, diff and rsync commands for filesystems

LICENSE=	APACHE20

BROKEN_i386=	fails to build

BUILD_DEPENDS=	bash:shells/bash

USES=		go:modules

OPTIONS_DEFINE=	MC

MC_DESC=	Install as mc

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMC}
MC=	mc
.else
MC=	${PORTNAME}
.endif

USE_GITHUB=	yes
GHTAG=		RELEASE.2021-05-26T19-19-26Z
COMMIT_ID=	8d65ee71302e662669bbbf57b834a4aa38c94bdc
GH_TUPLE=	minio:mc:${GHTAG}:DEFAULT \
		BurntSushi:toml:v0.3.1:burntsushi_toml/vendor/github.com/BurntSushi/toml \
		StackExchange:wmi:cbe66965904d:stackexchange_wmi/vendor/github.com/StackExchange/wmi \
		beorn7:perks:v1.0.1:beorn7_perks/vendor/github.com/beorn7/perks \
		cespare:xxhash:v2.1.1:cespare_xxhash_v2/vendor/github.com/cespare/xxhash/v2 \
		cheggaaa:pb:v1.0.29:cheggaaa_pb/vendor/github.com/cheggaaa/pb \
		coreos:go-semver:v0.2.0:coreos_go_semver/vendor/github.com/coreos/go-semver \
		coreos:go-systemd:39ca1b05acc7:coreos_go_systemd/vendor/github.com/coreos/go-systemd \
		coreos:pkg:3ac0863d7acf:coreos_pkg/vendor/github.com/coreos/pkg \
		dgrijalva:jwt-go:v3.2.0:dgrijalva_jwt_go/vendor/github.com/dgrijalva/jwt-go \
		dominikh:go-tools:v0.0.1-2019.2.3:dominikh_go_tools/vendor/honnef.co/go/tools \
		dustin:go-humanize:v1.0.0:dustin_go_humanize/vendor/github.com/dustin/go-humanize \
		etcd-io:etcd:8a03d2e9614b:etcd_io_etcd/vendor/go.etcd.io/etcd \
		fatih:color:v1.10.0:fatih_color/vendor/github.com/fatih/color \
		fatih:structs:v1.1.0:fatih_structs/vendor/github.com/fatih/structs \
		go-check:check:038fdea0a05b:go_check_check/vendor/gopkg.in/check.v1 \
		go-ini:ini:v1.57.0:go_ini_ini/vendor/gopkg.in/ini.v1 \
		go-ole:go-ole:v1.2.4:go_ole_go_ole/vendor/github.com/go-ole/go-ole \
		go-yaml:yaml:v2.3.0:go_yaml_yaml/vendor/gopkg.in/yaml.v2 \
		gogo:protobuf:v1.3.2:gogo_protobuf/vendor/github.com/gogo/protobuf \
		golang:crypto:83a5a9bb288b:golang_crypto/vendor/golang.org/x/crypto \
		golang:lint:16217165b5de:golang_lint/vendor/golang.org/x/lint \
		golang:mod:v0.3.0:golang_mod/vendor/golang.org/x/mod \
		golang:net:4e50805a0758:golang_net/vendor/golang.org/x/net \
		golang:protobuf:v1.4.3:golang_protobuf/vendor/github.com/golang/protobuf \
		golang:sys:93ed5bcd2bfe:golang_sys/vendor/golang.org/x/sys \
		golang:term:7de9c90e9dd1:golang_term/vendor/golang.org/x/term \
		golang:text:v0.3.6:golang_text/vendor/golang.org/x/text \
		golang:tools:v0.1.0:golang_tools/vendor/golang.org/x/tools \
		golang:xerrors:5ec99f83aff1:golang_xerrors/vendor/golang.org/x/xerrors \
		google:go-genproto:24fa4b261c55:google_go_genproto/vendor/google.golang.org/genproto \
		google:uuid:v1.1.2:google_uuid/vendor/github.com/google/uuid \
		grpc:grpc-go:v1.26.0:grpc_grpc_go/vendor/google.golang.org/grpc \
		h2non:filetype:v1.0.5:h2non_filetype/vendor/gopkg.in/h2non/filetype.v1 \
		hashicorp:errwrap:v1.0.0:hashicorp_errwrap/vendor/github.com/hashicorp/errwrap \
		hashicorp:go-multierror:v1.0.0:hashicorp_go_multierror/vendor/github.com/hashicorp/go-multierror \
		inconshreveable:go-update:8152e7eb6ccf:inconshreveable_go_update/vendor/github.com/inconshreveable/go-update \
		json-iterator:go:v1.1.11:json_iterator_go/vendor/github.com/json-iterator/go \
		klauspost:compress:v1.12.2:klauspost_compress/vendor/github.com/klauspost/compress \
		klauspost:cpuid:v1.3.1:klauspost_cpuid/vendor/github.com/klauspost/cpuid \
		klauspost:cpuid:v2.0.4:klauspost_cpuid_v2/vendor/github.com/klauspost/cpuid/v2 \
		kr:text:v0.2.0:kr_text/vendor/github.com/kr/text \
		mattn:go-colorable:v0.1.8:mattn_go_colorable/vendor/github.com/mattn/go-colorable \
		mattn:go-ieproxy:v0.0.1:mattn_go_ieproxy/vendor/github.com/mattn/go-ieproxy \
		mattn:go-isatty:v0.0.12:mattn_go_isatty/vendor/github.com/mattn/go-isatty \
		mattn:go-runewidth:v0.0.4:mattn_go_runewidth/vendor/github.com/mattn/go-runewidth \
		matttproud:golang_protobuf_extensions:v1.0.1:matttproud_golang_protobuf_extensions/vendor/github.com/matttproud/golang_protobuf_extensions \
		minio:argon2:v1.0.0:minio_argon2/vendor/github.com/minio/argon2 \
		minio:cli:v1.22.0:minio_cli/vendor/github.com/minio/cli \
		minio:colorjson:v1.0.0:minio_colorjson/vendor/github.com/minio/colorjson \
		minio:filepath:v1.0.0:minio_filepath/vendor/github.com/minio/filepath \
		minio:madmin-go:v1.0.2:minio_madmin_go/vendor/github.com/minio/madmin-go \
		minio:md5-simd:v1.1.1:minio_md5_simd/vendor/github.com/minio/md5-simd \
		minio:minio-go:f0518ca447d6:minio_minio_go_v7/vendor/github.com/minio/minio-go/v7 \
		minio:minio:3455f786faf0:minio_minio/vendor/github.com/minio/minio \
		minio:sha256-simd:v1.0.0:minio_sha256_simd/vendor/github.com/minio/sha256-simd \
		mitchellh:go-homedir:v1.1.0:mitchellh_go_homedir/vendor/github.com/mitchellh/go-homedir \
		modern-go:concurrent:bacd9c7ef1dd:modern_go_concurrent/vendor/github.com/modern-go/concurrent \
		modern-go:reflect2:v1.0.1:modern_go_reflect2/vendor/github.com/modern-go/reflect2 \
		montanaflynn:stats:v0.5.0:montanaflynn_stats/vendor/github.com/montanaflynn/stats \
		ncw:directio:v1.0.5:ncw_directio/vendor/github.com/ncw/directio \
		niemeyer:pretty:a10e7caefd8e:niemeyer_pretty/vendor/github.com/niemeyer/pretty \
		philhofer:fwd:v1.1.1:philhofer_fwd/vendor/github.com/philhofer/fwd \
		pkg:profile:v1.3.0:pkg_profile/vendor/github.com/pkg/profile \
		pkg:xattr:v0.4.1:pkg_xattr/vendor/github.com/pkg/xattr \
		posener:complete:v1.2.3:posener_complete/vendor/github.com/posener/complete \
		prometheus:client_golang:v1.8.0:prometheus_client_golang/vendor/github.com/prometheus/client_golang \
		prometheus:client_model:v0.2.0:prometheus_client_model/vendor/github.com/prometheus/client_model \
		prometheus:common:v0.14.0:prometheus_common/vendor/github.com/prometheus/common \
		prometheus:procfs:v0.6.0:prometheus_procfs/vendor/github.com/prometheus/procfs \
		protocolbuffers:protobuf-go:v1.23.0:protocolbuffers_protobuf_go/vendor/google.golang.org/protobuf \
		rjeczalik:notify:v0.9.2:rjeczalik_notify/vendor/github.com/rjeczalik/notify \
		rs:xid:v1.2.1:rs_xid/vendor/github.com/rs/xid \
		secure-io:sio-go:v0.3.1:secure_io_sio_go/vendor/github.com/secure-io/sio-go \
		shirou:gopsutil:v3.21.3:shirou_gopsutil_v3/vendor/github.com/shirou/gopsutil \
		tidwall:gjson:v1.7.5:tidwall_gjson/vendor/github.com/tidwall/gjson \
		tidwall:match:v1.0.3:tidwall_match/vendor/github.com/tidwall/match \
		tidwall:pretty:v1.1.0:tidwall_pretty/vendor/github.com/tidwall/pretty \
		tinylib:msgp:v1.1.3:tinylib_msgp/vendor/github.com/tinylib/msgp \
		tklauser:go-sysconf:v0.3.4:tklauser_go_sysconf/vendor/github.com/tklauser/go-sysconf \
		tklauser:numcpus:v0.2.1:tklauser_numcpus/vendor/github.com/tklauser/numcpus \
		uber-go:atomic:v1.5.0:uber_go_atomic/vendor/go.uber.org/atomic \
		uber-go:multierr:v1.3.0:uber_go_multierr/vendor/go.uber.org/multierr \
		uber-go:tools:2cfd321de3ee:uber_go_tools/vendor/go.uber.org/tools \
		uber-go:zap:v1.13.0:uber_go_zap/vendor/go.uber.org/zap

PLIST_FILES=	bin/${MC}
GO_BUILDFLAGS=	-ldflags=" \
		-X github.com/minio/mc/cmd.Version=${GH_TAGNAME:C/RELEASE\.//:C|(..)-(..)-(..)Z|\1:\2:\3Z|} \
		-X github.com/minio/mc/cmd.ReleaseTag=${GH_TAGNAME} \
		-X github.com/minio/mc/cmd.CommitID=${COMMIT_ID} \
		-X github.com/minio/mc/cmd.GOPATH=${WRKSRC} -s -w"
GO_TARGET=	:${MC}

post-extract:
	${RM} ${WRKSRC}/cmd/client-fs_freebsd_netbsd.go
	${RM} ${WRKSRC}/pkg/disk/stat_freebsd_netbsd.go
	${MKDIR} ${WRKSRC}/vendor/maze.io/x/duration
	${CP} ${FILESDIR}/duration.go ${WRKSRC}/vendor/maze.io/x/duration/duration.go

.include <bsd.port.mk>
