COMMENT =		swift programming language
DISTNAME =		release/6.2
PKGNAME = 		swift-6.2
CATEGORIES =		lang
HOMEPAGE =		https://swift.org

PERMIT_PACKAGE =	Yes
PERMIT_DISTFILES =	Yes

TAGNAME = 		release/6.2
LLVM_TAGNAME =		stable/20240723
DISPATCH_TAGNAME = 	main
ARGPARSER_TAGNAME = 	1.4.0
COLLECTIONS_TAGNAME = 	1.2.0
CRYPTO_TAGNAME = 	3.12.3
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
			swiftlang/swift-corelibs-libdispatch/archive/refs/heads/${DISPATCH_TAGNAME}.tar.gz \
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
			apple/swift-system/archive/refs/tags/${SYSTEM_TAGNAME}.tar.gz \
			Kitware/CMake/archive/refs/tags/v${CMAKE_TAGNAME}.tar.gz

DIST_SUBDIR =		swift

BUILD_DEPENDS +=	shells/bash
BUILD_DEPENDS +=	devel/ninja
BUILD_DEPENDS +=	lang/python/3
BUILD_DEPENDS +=	sysutils/e2fsprogs
BUILD_DEPENDS +=	textproc/libxml
BUILD_DEPENDS +=	net/curl

SEPARATE_BUILD =	Yes
ONLY_FOR_ARCHS = 	amd64 arm64

LLVM_SPELLING_ARCH =	${MACHINE_ARCH}
.if "${MACHINE_ARCH}" == "amd64"
LLVM_SPELLING_ARCH =	x86_64
.endif
SWIFT_TRIPLE =		${LLVM_SPELLING_ARCH}-unknown-openbsd${OSREV}
SUBST_VARS +=		LLVM_SPELLING_ARCH SWIFT_TRIPLE

WRKDIST = 		${WRKDIR}/dist
DPB_PROPERTIES =        parallel


post-extract:
	mkdir -p ${WRKDIST}
	mv ${WRKDIR}/CMake-* ${WRKSRC}
	mv ${WRKDIR}/llvm-* ${WRKSRC}
	mv ${WRKDIR}/swift-* ${WRKSRC}
	ln -fs ${WRKSRC}/CMake-${CMAKE_TAGNAME:S/\//-/} ${WRKSRC}/cmake
	ln -fs ${WRKSRC}/llvm-project-swift-${TAGNAME:S/\//-/} ${WRKSRC}/llvm-project
	ln -fs ${WRKSRC}/swift-build-${TAGNAME:S/\//-/} ${WRKSRC}/swift-build
	ln -fs ${WRKSRC}/swift-cmark-${TAGNAME:S/\//-/} ${WRKSRC}/cmark
	ln -fs ${WRKSRC}/swift-corelibs-foundation-${TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-foundation
	ln -fs ${WRKSRC}/swift-corelibs-libdispatch-${DISPATCH_TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-libdispatch
	ln -fs ${WRKSRC}/swift-corelibs-xctest-${TAGNAME:S/\//-/} ${WRKSRC}/swift-corelibs-xctest
	ln -fs ${WRKSRC}/swift-driver-${TAGNAME:S/\//-/} ${WRKSRC}/swift-driver
	ln -fs ${WRKSRC}/swift-experimental-string-processing-${TAGNAME:S/\//-/} ${WRKSRC}/swift-experimental-string-processing
	ln -fs ${WRKSRC}/swift-foundation-icu-${TAGNAME:S/\//-/} ${WRKSRC}/swift-foundation-icu
	ln -fs ${WRKSRC}/swift-foundation-${TAGNAME:S/\//-/} ${WRKSRC}/swift-foundation
	ln -fs ${WRKSRC}/swift-llbuild-${TAGNAME:S/\//-/} ${WRKSRC}/llbuild
	ln -fs ${WRKSRC}/swift-syntax-${TAGNAME:S/\//-/} ${WRKSRC}/swift-syntax
	ln -fs ${WRKSRC}/swift-tools-support-core-${TAGNAME:S/\//-/} ${WRKSRC}/swift-tools-support-core
	ln -fs ${WRKSRC}/swift-testing-${TAGNAME:S/\//-/} ${WRKSRC}/swift-testing
	ln -fs ${WRKSRC}/swift-argument-parser-${ARGPARSER_TAGNAME:S/\//-/} ${WRKSRC}/swift-argument-parser
	ln -fs ${WRKSRC}/swift-asn1-${ASN1_TAGNAME:S/\//-/} ${WRKSRC}/swift-asn1
	ln -fs ${WRKSRC}/swift-certificates-${CERTIFICATES_TAGNAME:S/\//-/} ${WRKSRC}/swift-certificates
	ln -fs ${WRKSRC}/swift-collections-${COLLECTIONS_TAGNAME:S/\//-/} ${WRKSRC}/swift-collections
	ln -fs ${WRKSRC}/swift-crypto-${CRYPTO_TAGNAME:S/\//-/} ${WRKSRC}/swift-crypto
	ln -fs ${WRKSRC}/swift-system-${SYSTEM_TAGNAME:S/\//-/} ${WRKSRC}/swift-system
	ln -fs ${WRKSRC}/swift-toolchain-sqlite-${SQLITE_TAGNAME:S/\//-/} ${WRKSRC}/swift-toolchain-sqlite
	ln -fs ${WRKSRC}/swift-package-manager-${TAGNAME:S/\//-/} ${WRKSRC}/swiftpm
	mv ${WRKSRC}/swift-${TAGNAME:S/\//-/} ${WRKSRC}/swift

do-build:
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage0_openbsd \
	      build_subdir=bootstrap0 install_destdir=${WRKBUILD}/install0
	mkdir -p ${WRKBUILD}/bootstrap1 && \
	    [ ! -e ${WRKBUILD}/bootstrap1/llvm-openbsd-${LLVM_SPELLING_ARCH} ] && \
	    ln -s ${WRKBUILD}/bootstrap0/llvm-openbsd-${LLVM_SPELLING_ARCH}/ ${WRKBUILD}/bootstrap1/llvm-openbsd-${LLVM_SPELLING_ARCH} || true
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install0/usr/local/bin/:${PATH} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage1_openbsd \
	      build_subdir=bootstrap1 install_destdir=${WRKBUILD}/install1
	mkdir -p ${WRKBUILD}/bootstrap2 && \
	    [ ! -e ${WRKBUILD}/bootstrap2/llvm-openbsd-${LLVM_SPELLING_ARCH} ] && \
	    ln -s ${WRKBUILD}/bootstrap0/llvm-openbsd-${LLVM_SPELLING_ARCH}/ ${WRKBUILD}/bootstrap2/llvm-openbsd-${LLVM_SPELLING_ARCH} || true
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install1/usr/local/bin/:${PATH} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --preset=bootstrap_stage2_openbsd \
	      build_subdir=bootstrap2 install_destdir=${WRKBUILD}/install2

do-install:
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/swift-openbsd-${LLVM_SPELLING_ARCH} -- install-swift-components
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/libdispatch-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/libdispatch_static-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/foundation_macros-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/foundation-openbsd-${LLVM_SPELLING_ARCH} -- install
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/foundation_static-openbsd-${LLVM_SPELLING_ARCH} -- install
	cp ${WRKBUILD}/bootstrap0/llvm-openbsd-${LLVM_SPELLING_ARCH}/lib/libIndexStore.so ${DESTDIR}/usr/local/lib
	env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/xctest-openbsd-${LLVM_SPELLING_ARCH} -- install
	echo env DESTDIR=${DESTDIR} ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/llbuild-openbsd-${LLVM_SPELLING_ARCH} -- install-swift-build-tool
	echo env DESTDIR=${DESTDIR}/usr/local ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/swifttestingmacros-openbsd-${LLVM_SPELLING_ARCH} -- install
	echo env DESTDIR=${DESTDIR}/usr/local ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --build ${WRKBUILD}/bootstrap2/swifttesting-openbsd-${LLVM_SPELLING_ARCH} -- install
	${WRKDIST}/swiftpm/Utilities/bootstrap install --install-only --release --swiftc-path ${DESTDIR}/usr/local/bin/swiftc --clang-path /usr/bin/clang --cmake-path ${WRKBUILD}/cmake-openbsd-${LLVM_SPELLING_ARCH}/bin/cmake --ninja-path /usr/local/bin/ninja --build-dir ${WRKBUILD}/bootstrap2/swiftpm-openbsd-${LLVM_SPELLING_ARCH} --llbuild-build-dir ${WRKBUILD}/bootstrap2/llbuild-openbsd-${LLVM_SPELLING_ARCH} --dispatch-build-dir ${WRKBUILD}/bootstrap2/libdispatch-openbsd-${LLVM_SPELLING_ARCH} --verbose --prefix ${DESTDIR}/usr/local

.include <bsd.port.mk>
