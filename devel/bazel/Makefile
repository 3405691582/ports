BROKEN-sparc64 = libsingle_line_formatter.jar failed: Worker process did not return a WorkResponse:

# ./src/tools/singlejar/mapped_file_posix.inc only supports 64-bit UNIX.
ONLY_FOR_ARCHS =	${LP64_ARCHS}

VERSION =		9.0.0

COMMENT =		polyglot build tool
HOMEPAGE =		https://bazel.build/

DISTNAME =		bazel-${VERSION}
EXTRACT_SUFX =		-dist.zip
EXTRACT_CASES =		*.zip) ${UNZIP} -Laq ${FULLDISTDIR}/$$archive -d ${WRKSRC};;

CATEGORIES =		devel

# Apache 2.0
PERMIT_PACKAGE =	Yes

SITES =			https://github.com/bazelbuild/bazel/releases/download/${VERSION}/

RULES_CC_VER = 		0.2.14
DIST_TUPLE =		github bazelbuild rules_cc ${RULES_CC_VER} rules_cc-${RULES_CC_VER}

MODULES =		java
MODJAVA_VER =		21

BUILD_DEPENDS =		archivers/zip \
			shells/bash

# Disable stripping. The `bazel` binary contains an embedded zip file;
# stripping the binary removes this zip file, breaking the binary.
INSTALL_STRIP =

MAKE_ENV =		VERBOSE=yes

do-build:
	cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} \
		EMBED_LABEL="${VERSION}" \
		EXTRA_BAZEL_ARGS="--tool_java_runtime_version=local_jdk_${MODJAVA_VER}" \
		BAZEL_WRKDIR=${WRKDIR}/tmp \
		PATH="${LOCALBASE}/bin:${PATH}" \
		JAVA_HOME=${JAVA_HOME} \
		SOURCE_DATE_EPOCH="0" \
		${LOCALBASE}/bin/bash ./compile.sh
	chmod -R u+w ${WRKDIR}/tmp

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/output/bazel ${PREFIX}/bin
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/bazel/
	${INSTALL_DATA} ${WRKSRC}/scripts/packages/bazel.bazelrc \
		${PREFIX}/share/examples/bazel/bazel.bazelrc

.include <bsd.port.mk>
