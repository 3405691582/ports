COMMENT-main =		swift programming language
COMMENT-stdlib =	swift standard libraries
COMMENT-libdispatch =	swift dispatch library
COMMENT-foundation =	swift foundation library
COMMENT-swiftpm =	swift package manager
COMMENT-xctest =	swift xctest library
COMMENT-testing =	swift testing library
V =			6.2.0
PKGNAME-main = 		swift-${V}
PKGNAME-stdlib = 	swift-stdlib-${V}
PKGNAME-libdispatch = 	swift-libdispatch-${V}
PKGNAME-foundation = 	swift-foundation-${V}
PKGNAME-swiftpm = 	swift-swiftpm-${V}
PKGNAME-xctest = 	swift-xctest-${V}
PKGNAME-testing = 	swift-testing-${V}
CATEGORIES =		lang
HOMEPAGE =		https://swift.org

PERMIT_PACKAGE =	Yes
PERMIT_DISTFILES =	Yes

MULTI_PACKAGES =	-main -stdlib -libdispatch -foundation -swiftpm -xctest -testing

FLAVOR ?=
PSEUDO_FLAVORS =	hosttools

DIST_SUBDIR =		swift

BUILD_DEPENDS +=	shells/bash
#BUILD_DEPENDS +=	devel/cmake
BUILD_DEPENDS +=	devel/ninja
BUILD_DEPENDS +=	lang/python/3
BUILD_DEPENDS +=	sysutils/e2fsprogs
BUILD_DEPENDS +=	textproc/libxml
BUILD_DEPENDS +=	net/curl

.if ${FLAVOR} == hosttools
BUILD_DEPENDS +=	lang/swift
.endif

RUN_DEPENDS +=		sysutils/e2fsprogs
RUN_DEPENDS += 		archivers/zstd
RUN_DEPENDS +=		databases/sqlite3
RUN_DEPENDS += 		textproc/libxml

SEPARATE_BUILD =	Yes
ONLY_FOR_ARCHS = 	amd64 arm64

WRKDIST = 		${WRKDIR}/dist
DPB_PROPERTIES =        parallel

LLVM_SPELLING_ARCH =	${MACHINE_ARCH}
.if "${MACHINE_ARCH}" == "amd64"
LLVM_SPELLING_ARCH =	x86_64
.endif
SWIFT_TRIPLE =		${LLVM_SPELLING_ARCH}-unknown-openbsd${OSREV}
SUBST_VARS +=		LLVM_SPELLING_ARCH SWIFT_TRIPLE

DISTNAME =		swift-${V}
TAGNAME = 		release/${V}
LLVM_TAGNAME =		stable/20240723
DISPATCH_TAGNAME = 	swift-DEVELOPMENT-SNAPSHOT-2025-10-02-a
ARGPARSER_TAGNAME = 	1.4.0
COLLECTIONS_TAGNAME = 	1.2.0
CRYPTO_TAGNAME = 	3.13.0
CERTIFICATES_TAGNAME = 	1.10.0
ASN1_TAGNAME = 		1.3.2
SYSTEM_TAGNAME = 	1.5.0
SQLITE_TAGNAME = 	1.0.1
CMAKE_TAGNAME = 	3.30.2
SITES =			https://github.com/
DISTFILES = 		swiftlang/swift/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/llvm-project/archive/refs/heads/swift/${TAGNAME}.tar.gz \
			swiftlang/swift-cmark/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-llbuild/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-build/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-driver/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-tools-support-core/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-package-manager/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-syntax/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-corelibs-xctest/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-corelibs-foundation/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-corelibs-libdispatch/archive/refs/tags/${DISPATCH_TAGNAME}.tar.gz \
			swiftlang/swift-foundation-icu/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-foundation/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-experimental-string-processing/archive/refs/heads/${TAGNAME}.tar.gz \
			swiftlang/swift-toolchain-sqlite/archive/refs/tags/${SQLITE_TAGNAME}.tar.gz \
			swiftlang/swift-testing/archive/refs/heads/${TAGNAME}.tar.gz \
			apple/swift-argument-parser/archive/refs/tags/${ARGPARSER_TAGNAME}.tar.gz \
			apple/swift-collections/archive/refs/tags/${COLLECTIONS_TAGNAME}.tar.gz \
			apple/swift-crypto/archive/refs/tags/${CRYPTO_TAGNAME}.tar.gz \
			apple/swift-certificates/archive/refs/tags/${CERTIFICATES_TAGNAME}.tar.gz \
			apple/swift-asn1/archive/refs/tags/${ASN1_TAGNAME}.tar.gz \
			apple/swift-system/archive/refs/tags/${SYSTEM_TAGNAME}.tar.gz

CMAKE_BIN = 		${WRKDIR}/bin/cmake
NINJA_BIN = 		${WRKDIR}/bin/ninja

post-extract:
	ln -fs `which cmake` ${CMAKE_BIN}
	ln -fs `which ninja` ${NINJA_BIN}
	rm -rf ${WRKDIST} && mkdir ${WRKDIST}
	mv ${WRKDIR}/llvm-* ${WRKSRC}
	mv ${WRKDIR}/swift-* ${WRKSRC}
	mv ${WRKSRC}/llvm-project-swift-${TAGNAME:S/\//-/} ${WRKSRC}/llvm-project
	mv ${WRKSRC}/swift-build-${TAGNAME:S/\//-/} ${WRKSRC}/swift-build
	mv ${WRKSRC}/swift-cmark-${TAGNAME:S/\//-/} ${WRKSRC}/cmark
	mv ${WRKSRC}/swift-corelibs-foundation-${TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-foundation
	mv ${WRKSRC}/swift-corelibs-libdispatch-${DISPATCH_TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-libdispatch
	mv ${WRKSRC}/swift-corelibs-xctest-${TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-xctest
	mv ${WRKSRC}/swift-driver-${TAGNAME:S/\//-/} ${WRKSRC}/swift-driver
	mv ${WRKSRC}/swift-experimental-string-processing-${TAGNAME:S/\//-/} ${WRKSRC}/swift-experimental-string-processing
	mv ${WRKSRC}/swift-foundation-icu-${TAGNAME:S/\//-/} ${WRKSRC}/swift-foundation-icu
	mv ${WRKSRC}/swift-foundation-${TAGNAME:S/\//-/} ${WRKSRC}/swift-foundation
	mv ${WRKSRC}/swift-llbuild-${TAGNAME:S/\//-/} ${WRKSRC}/llbuild
	mv ${WRKSRC}/swift-syntax-${TAGNAME:S/\//-/} ${WRKSRC}/swift-syntax
	mv ${WRKSRC}/swift-tools-support-core-${TAGNAME:S/\//-/} ${WRKSRC}/swift-tools-support-core
	mv ${WRKSRC}/swift-testing-${TAGNAME:S/\//-/} ${WRKSRC}/swift-testing
	mv ${WRKSRC}/swift-argument-parser-${ARGPARSER_TAGNAME:S/\//-/} ${WRKSRC}/swift-argument-parser
	mv ${WRKSRC}/swift-asn1-${ASN1_TAGNAME:S/\//-/} ${WRKSRC}/swift-asn1
	mv ${WRKSRC}/swift-certificates-${CERTIFICATES_TAGNAME:S/\//-/} ${WRKSRC}/swift-certificates
	mv ${WRKSRC}/swift-collections-${COLLECTIONS_TAGNAME:S/\//-/} ${WRKSRC}/swift-collections
	mv ${WRKSRC}/swift-crypto-${CRYPTO_TAGNAME:S/\//-/} ${WRKSRC}/swift-crypto
	mv ${WRKSRC}/swift-system-${SYSTEM_TAGNAME:S/\//-/} ${WRKSRC}/swift-system
	mv ${WRKSRC}/swift-toolchain-sqlite-${SQLITE_TAGNAME:S/\//-/} ${WRKSRC}/swift-toolchain-sqlite
	mv ${WRKSRC}/swift-package-manager-${TAGNAME:S/\//-/} ${WRKSRC}/swiftpm
	mv ${WRKSRC}/swift-${TAGNAME:S/\//-/} ${WRKSRC}/swift

do-build:
.if ${FLAVOR} != hosttools
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage0_openbsd \
	      build_subdir=stage0 install_destdir=${WRKBUILD}/install0
	mkdir -p ${WRKBUILD}/stage1 && \
	    [ ! -e ${WRKBUILD}/stage1/llvm-openbsd-${LLVM_SPELLING_ARCH} ] && \
	    ln -s ${WRKBUILD}/stage0/llvm-openbsd-${LLVM_SPELLING_ARCH}/ ${WRKBUILD}/stage1/llvm-openbsd-${LLVM_SPELLING_ARCH} || true
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install0/usr/local/bin/:${PATH} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage1_openbsd \
	      build_subdir=stage1 install_destdir=${WRKBUILD}/install1
	mkdir -p ${WRKBUILD}/stage2 && \
	    [ ! -e ${WRKBUILD}/stage2/llvm-openbsd-${LLVM_SPELLING_ARCH} ] && \
	    ln -s ${WRKBUILD}/stage0/llvm-openbsd-${LLVM_SPELLING_ARCH}/ ${WRKBUILD}/stage2/llvm-openbsd-${LLVM_SPELLING_ARCH} || true
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install1/usr/local/bin/:${PATH} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage2_openbsd \
	      build_subdir=stage2 install_destdir=${WRKBUILD}/install2

	${WRKSRC}/swift-driver/Utilities/build-script-helper.py build \
	    --package-path ${WRKSRC}/swift-driver \
	    --build-path ${WRKBUILD}/stage2/swiftdriver-openbsd-aarch64 \
	    --configuration release \
	    --toolchain ${WRKBUILD}/install2/usr/local \
	    --ninja-bin ${WRKDIR}/bin/ninja \
	    --cmake-bin ${CMAKE_BIN} \
	    --dispatch-build-dir ${WRKBUILD}/stage2/libdispatch-openbsd-${LLVM_SPELLING_ARCH}
.else
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --native-clang-tools-path=${WRKDIR}/bin \
	      --build-subdir=stage2 \
	      --extra-cmake-options=-DBRIDGING_MODE=PURE \
	      --llvm-install-components=IndexStore \
	      --llvm-targets-to-build=host \
	      --release -A \
	      --foundation --xctest \
	      --swift-driver \
	      --llbuild \
	      --swift-testing \
	      --swift-testing-macros \
	      --swiftpm \
	      --install-swift \
	      --install-foundation \
	      --install-libdispatch \
	      --install-xctest \
	      --install-swift-driver \
	      --install-swift-testing \
	      --install-swift-testing-macros \
	      --install-swiftpm
.endif

do-install:
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/swift-openbsd-${LLVM_SPELLING_ARCH} -- install-swift-components
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/libdispatch-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/libdispatch_static-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/foundation_macros-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/foundation-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/foundation_static-openbsd-${LLVM_SPELLING_ARCH} -- install
	cp ${WRKBUILD}/stage2/llvm-openbsd-${LLVM_SPELLING_ARCH}/lib/libIndexStore.so \
	    ${DESTDIR}/usr/local/lib
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/xctest-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/llbuild-openbsd-${LLVM_SPELLING_ARCH} -- install-swift-build-tool
	env DESTDIR=${DESTDIR}/usr/local ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/swifttestingmacros-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR}/usr/local ${CMAKE_BIN} \
	    --build ${WRKBUILD}/stage2/swifttesting-openbsd-${LLVM_SPELLING_ARCH} -- install
	${WRKDIST}/swiftpm/Utilities/bootstrap install --install-only --release \
	    --swiftc-path ${DESTDIR}/usr/local/bin/swiftc \
	    --clang-path /usr/bin/clang \
	    --cmake-path ${CMAKE_BIN} \
	    --ninja-path ${NINJA_BIN} \
	    --build-dir ${WRKBUILD}/stage2/swiftpm-openbsd-${LLVM_SPELLING_ARCH} \
	    --llbuild-build-dir ${WRKBUILD}/stage2/llbuild-openbsd-${LLVM_SPELLING_ARCH} \
	    --dispatch-build-dir ${WRKBUILD}/stage2/libdispatch-openbsd-${LLVM_SPELLING_ARCH} \
	    --prefix ${DESTDIR}/usr/local \
	    --verbose
	${WRKSRC}/swift-driver/Utilities/build-script-helper.py install \
	    --package-path ${WRKSRC}/swift-driver \
	    --build-path ${WRKBUILD}/stage2/swiftdriver-openbsd-aarch64 \
	    --configuration release \
	    --toolchain ${DESTDIR}/usr/local \
	    --ninja-bin ${NINJA_BIN} \
	    --cmake-bin ${CMAKE_BIN} \
	    --dispatch-build-dir ${WRKBUILD}/stage2/libdispatch-openbsd-${LLVM_SPELLING_ARCH}

.include <bsd.port.mk>
