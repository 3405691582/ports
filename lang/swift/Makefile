COMMENT-main =		swift programming language
COMMENT-stdlib =	swift standard libraries
COMMENT-libdispatch =	swift dispatch library
COMMENT-foundation =	swift foundation library
COMMENT-swiftpm =	swift package manager
COMMENT-xctest =	swift xctest library
COMMENT-testing =	swift testing library
COMMENT-format =	swift formatting library
COMMENT-lsp =		swift language server
COMMENT-docc =		swift documentation compiler
V =			6.3
PKGNAME-main = 		swift-${V}
PKGNAME-stdlib = 	swift-stdlib-${V}
PKGNAME-libdispatch = 	swift-libdispatch-${V}
PKGNAME-foundation = 	swift-foundation-${V}
PKGNAME-swiftpm = 	swift-swiftpm-${V}
PKGNAME-xctest = 	swift-xctest-${V}
PKGNAME-testing = 	swift-testing-${V}
PKGNAME-format = 	swift-format-${V}
PKGNAME-lsp = 		swift-sourcekit-lsp-${V}
PKGNAME-docc = 		swift-docc-${V}
CATEGORIES =		lang
HOMEPAGE =		https://swift.org

PERMIT_PACKAGE =	Yes

MULTI_PACKAGES =	-main -stdlib -libdispatch -foundation -swiftpm \
			-xctest -testing -format -lsp -docc

DIST_SUBDIR =		swift

SEPARATE_BUILD =	Yes
ONLY_FOR_ARCHS = 	amd64 aarch64

FLAVOR ?=
PSEUDO_FLAVORS =	native_bootstrap

.if ${FLAVOR} == native_bootstrap
BUILD_DEPENDS +=	lang/swift
.endif

#BUILD_DEPENDS +=	devel/cmake
#BUILD_DEPENDS +=	lang/python/3
BUILD_DEPENDS +=	shells/bash
BUILD_DEPENDS +=	devel/ninja
BUILD_DEPENDS +=	sysutils/e2fsprogs
BUILD_DEPENDS +=	textproc/libxml
BUILD_DEPENDS +=	net/curl

RUN_DEPENDS-main += \
	lang/swift,-stdlib \
	lang/swift,-libdispatch \
	lang/swift,-foundation \
	archivers/zstd \
	databases/sqlite3 \
	sysutils/e2fsprogs

LIB_DEPENDS-stdlib += \
	archivers/zstd \
	sysutils/e2fsprogs

LIB_DEPENDS-dispatch +=	\
	lang/swift,-stdlib

LIB_DEPENDS-foundation += \
	lang/swift,-stdlib \
	lang/swift,-libdispatch \
	net/curl \
	textproc/libxml

LIB_DEPENDS-xctest += \
	lang/swift,-stdlib \
	lang/swift,-libdispatch \
	lang/swift,-foundation \
	archivers/zstd

LIB_DEPENDS-testing += \
	lang/swift,-libdispatch \
	lang/swift,-foundation \
	lang/swift,-stdlib

RUN_DEPENDS-swiftpm += \
	lang/swift,-main \
	lang/swift,-stdlib \
	lang/swift,-libdispatch \
	lang/swift,-foundation \
	lang/swift,-xctest \
	databases/sqlite3 \
	textproc/libxml

WRKDIST = 		${WRKDIR}/dist
PORTHOME = 		${WRKDIR}
DPB_PROPERTIES =        parallel

LLVM_SPELLING_ARCH =	${MACHINE_ARCH}
.if "${MACHINE_ARCH}" == "amd64"
LLVM_SPELLING_ARCH =	x86_64
.endif
SWIFT_TRIPLE =		${LLVM_SPELLING_ARCH}-unknown-openbsd${OSREV}
SUBST_VARS +=		LLVM_SPELLING_ARCH SWIFT_TRIPLE

DISTNAME =		swift-${V}
TAGNAME = 		swift-6.3-DEVELOPMENT-SNAPSHOT-2026-01-29a
DISPATCH_TAGNAME = 	swift-DEVELOPMENT-SNAPSHOT-2025-10-02-a
ARGPARSER_TAGNAME = 	1.5.1
COLLECTIONS_TAGNAME = 	1.3.0
CRYPTO_TAGNAME = 	3.15.1
CERTIFICATES_TAGNAME = 	1.10.1
ASN1_TAGNAME = 		1.3.2
SYSTEM_TAGNAME = 	1.5.0
SQLITE_TAGNAME = 	1.0.7
CMAKE_TAGNAME = 	3.30.2
NIO_TAGNAME =		2.91.0
ATOMICS_TAGNAME = 	1.2.0
TOOLS_TAGNAME =		0.0.9
DIST_TUPLE += \
	github swiftlang swift ${TAGNAME} swift \
	github swiftlang swift-cmark ${TAGNAME} cmark \
	github swiftlang swift-llbuild ${TAGNAME} llbuild \
	github swiftlang swift-package-manager ${TAGNAME} swiftpm \
	github swiftlang llvm-project ${TAGNAME} llvm-project \
	github swiftlang swift-build ${TAGNAME} swift-build \
	github swiftlang swift-driver ${TAGNAME} swift-driver \
	github swiftlang swift-syntax ${TAGNAME} swift-syntax \
	github swiftlang swift-corelibs-xctest ${TAGNAME} swift-corelibs-xctest \
	github swiftlang swift-foundation-icu ${TAGNAME} swift-foundation-icu \
	github swiftlang swift-foundation ${TAGNAME} swift-foundation \
	github swiftlang swift-testing ${TAGNAME} swift-testing \
	github swiftlang swift-corelibs-foundation ${TAGNAME} \
		swift-corelibs-foundation \
	github swiftlang swift-tools-support-core ${TAGNAME} \
		swift-tools-support-core \
	github swiftlang swift-experimental-string-processing ${TAGNAME} \
		swift-experimental-string-processing \
	github swiftlang swift-corelibs-libdispatch ${DISPATCH_TAGNAME} \
		swift-corelibs-libdispatch \
	github swiftlang swift-toolchain-sqlite ${SQLITE_TAGNAME} \
		swift-toolchain-sqlite \
	github apple swift-asn1 ${ASN1_TAGNAME} swift-asn1 \
	github apple swift-crypto ${CRYPTO_TAGNAME} swift-crypto \
	github apple swift-system ${SYSTEM_TAGNAME} swift-system \
	github apple swift-certificates ${CERTIFICATES_TAGNAME} \
		swift-certificates \
	github apple swift-argument-parser ${ARGPARSER_TAGNAME} \
		swift-argument-parser \
	github apple swift-collections ${COLLECTIONS_TAGNAME} \
		swift-collections \
	github swiftlang swift-docc-render-artifact ${TAGNAME} swift-docc-render-artifact \
	github swiftlang swift-docc ${TAGNAME} swift-docc \
	github swiftlang swift-tools-protocols ${TOOLS_TAGNAME} swift-tools-protocols \
	github swiftlang sourcekit-lsp ${TAGNAME} sourcekit-lsp  \
	github swiftlang indexstore-db ${TAGNAME} indexstore-db \
	github apple swift-nio ${NIO_TAGNAME} swift-nio \
	github apple swift-markdown ${TAGNAME} swift-markdown \
	github apple swift-lmdb ${TAGNAME} swift-lmdb \
	github apple swift-docc-symbolkit ${TAGNAME} swift-docc-symbolkit \
	github apple swift-atomics ${ATOMICS_TAGNAME} swift-atomics

BOOTSTRAP_V =	 ${V}
SITES.bootstrap = \
	https://github.com/3405691582/swift-bootstrap/releases/download/
.for arch in ${ONLY_FOR_ARCHS}
SUPDISTFILES.bootstrap += \
	7.8/swift-bootstrap-${BOOTSTRAP_V}-${arch}.tar.gz
.endfor
.if ${FLAVOR} != native_bootstrap
DISTFILES.bootstrap = \
	7.8/swift-bootstrap-${BOOTSTRAP_V}-${MACHINE_ARCH}.tar.gz
.endif

CMAKE_BIN = 		${WRKDIR}/bin/cmake
NINJA_BIN = 		${WRKDIR}/bin/ninja
BOOTSTRAP_BASE =	${WRKDIR}/bootstrap
BOOTSTRAP_DIR =		${BOOTSTRAP_BASE}/${TRUEPREFIX}
SWIFT_SUFFIX =		openbsd-${LLVM_SPELLING_ARCH}
COMPONENTS = \
	autolink-driver;compiler;stdlib;sdk-overlay;toolchain-tools;license
SWIFT_COMPONENTS = \
	${COMPONENTS};libexec;swift-remote-mirror;static-mirror-lib
BOOTSTRAP_COMPONENTS = \
	autolink-driver;compiler;stdlib;sdk-overlay;toolchain-tools;license

post-extract:
	ln -fs `which cmake` ${CMAKE_BIN}
	ln -fs `which ninja` ${NINJA_BIN}
.if ${FLAVOR} != native_bootstrap
	mkdir -p ${BOOTSTRAP_BASE}
	mv -f ${WRKDIR}/usr ${BOOTSTRAP_BASE}
.endif

do-build:
	${SETENV} ${MAKE_ENV} \
	    PATH=${BOOTSTRAP_DIR}/bin:${PORTPATH} \
	    SWIFT_BUILD_ROOT=${WRKBUILD} \
	    ${WRKSRC}/swift/utils/build-script \
	      -j${MAKE_JOBS} \
	      --native-clang-tools-path=${WRKDIR}/bin \
	      --build-subdir=toolchain \
	      --extra-cmake-options=-DBRIDGING_MODE=PURE \
	      --install-prefix=${TRUEPREFIX} \
	      --llvm-install-components=IndexStore \
	      --llvm-targets-to-build=host \
<<<<<<< HEAD
	      --release -A \
	      --install-swift \
	      --swift-install-components="${SWIFT_COMPONENTS}" \
	      --install-libdispatch \
=======
	      --swift-install-components=${SWIFT_COMPONENTS} \
	      --release -A --install-swift \
	      --libdispatch --install-libdispatch \
>>>>>>> 3ca6670bac8 (wip docc, sourcekit-lsp)
	      --foundation --install-foundation \
	      --xctest --install-xctest \
	      --swift-testing --install-swift-testing \
	      --swift-testing-macros --install-swift-testing-macros \
	      --llbuild \
	      --swiftpm --install-swiftpm \
	      --swift-driver --install-swift-driver \
	      --swiftformat --install-swiftformat \
	      --sourcekit-lsp --install-sourcekit-lsp \
	      --swiftdocc --install-swiftdocc

do-install:
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/swift-${SWIFT_SUFFIX} -- \
	    install-swift-components
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/libdispatch-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/libdispatch_static-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/foundation_macros-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/foundation-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/foundation_static-${SWIFT_SUFFIX} -- \
	    install
	cp ${WRKBUILD}/toolchain/llvm-${SWIFT_SUFFIX}/lib/libIndexStore.so \
	    ${DESTDIR}/${TRUEPREFIX}/lib
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/xctest-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/llbuild-${SWIFT_SUFFIX} -- \
	    install-swift-build-tool
	${SETENV} DESTDIR=${DESTDIR}/${TRUEPREFIX} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/swifttestingmacros-${SWIFT_SUFFIX} -- \
	    install
	${SETENV} DESTDIR=${DESTDIR}/${TRUEPREFIX} ${CMAKE_BIN} --build \
	    ${WRKBUILD}/toolchain/swifttesting-${SWIFT_SUFFIX} -- \
	    install
	${WRKDIST}/swiftpm/Utilities/bootstrap install \
	    --install-only --release \
	    --swiftc-path ${DESTDIR}/${TRUEPREFIX}/bin/swiftc \
	    --clang-path ${WRKDIR}/bin/clang \
	    --cmake-path ${CMAKE_BIN} \
	    --ninja-path ${NINJA_BIN} \
	    --build-dir \
		${WRKBUILD}/toolchain/swiftpm-${SWIFT_SUFFIX} \
	    --llbuild-build-dir \
		${WRKBUILD}/toolchain/llbuild-${SWIFT_SUFFIX} \
	    --dispatch-build-dir \
		${WRKBUILD}/toolchain/libdispatch-${SWIFT_SUFFIX} \
	    --prefix ${DESTDIR}/${TRUEPREFIX} \
	    --verbose
	${WRKSRC}/swift-driver/Utilities/build-script-helper.py install \
	    --package-path ${WRKSRC}/swift-driver \
	    --build-path \
		${WRKBUILD}/toolchain/swiftdriver-${SWIFT_SUFFIX} \
	    --configuration release \
	    --toolchain ${DESTDIR}/${TRUEPREFIX} \
	    --ninja-bin ${NINJA_BIN} \
	    --cmake-bin ${CMAKE_BIN} \
	    --dispatch-build-dir \
		${WRKBUILD}/toolchain/libdispatch-${SWIFT_SUFFIX}
	${WRKSRC}/sourcekit-lsp/Utilities/build-script-helper.py install \
	    --package-path ${WRKSRC}/sourcekit-lsp \
	    --build-path ${WRKBUILD}/toolchain/unified-swiftpm-build-openbsd-${LLVM_SPELLING_ARCH} \
	    --configuration release \
	    --toolchain ${DESTDIR}/${TRUEPREFIX} \
	    --ninja-bin ${NINJA_BIN} \
	    --multiroot-data-file ${WRKSRC}/swift/utils/build_swift/resources/SwiftPM-Unified-Build.xcworkspace \
	    --prefix ${DESTDIR}/${TRUEPREFIX}
	${WRKSRC}/swift-format/build-script-helper.py install \
	    --toolchain ${DESTDIR}/${TRUEPREFIX} \
	    --configuration release \
	    --build-path ${WRKBUILD}/toolchain/unified-swiftpm-build-openbsd-${LLVM_SPELLING_ARCH} \
	    --multiroot-data-file ${WRKSRC}/swift/utils/build_swift/resources/SwiftPM-Unified-Build.xcworkspace \
	    --prefix ${DESTDIR}/${TRUEPREFIX}
	${WRKSRC}/swift-docc/build-script-helper.py install \
	    --toolchain ${DESTDIR}/${TRUEPREFIX} \
	    --configuration release \
	    --build-dir ${WRKBUILD}/toolchain/unified-swiftpm-build-openbsd-${LLVM_SPELLING_ARCH} \
	    --multiroot-data-file ${WRKSRC}/swift/utils/build_swift/resources/SwiftPM-Unified-Build.xcworkspace \
	    --install-dir ${DESTDIR}/${TRUEPREFIX}/bin
	mkdir -p ${DESTDIR}/${TRUEPREFIX}/share/docc/render
	rsync -a ${WRKSRC}/swift-docc-render-artifact/dist/ ${DESTDIR}/${TRUEPREFIX}/share/docc/render

.PHONY: bootstrap
bootstrap: patch
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	  ${WRKSRC}/swift/utils/build-script \
	    -j${MAKE_JOBS} \
	    --preset=bootstrap_stage0_openbsd \
	    build_subdir=stage0 install_destdir=${WRKBUILD}/install0
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install0/${TRUEPREFIX}/bin/:${PATH} \
	  ${WRKSRC}/swift/utils/build-script \
	    -j${MAKE_JOBS} \
	    --preset=bootstrap_stage1_openbsd \
	    build_subdir=stage1 install_destdir=${WRKBUILD}/install1
	env SWIFT_BUILD_ROOT=${WRKBUILD} \
	    PATH=${WRKBUILD}/install1/${TRUEPREFIX}/bin/:${PATH} \
	  ${WRKSRC}/swift/utils/build-script \
	    -j${MAKE_JOBS} \
	    --preset=bootstrap_stage2_openbsd \
	    build_subdir=stage2 install_destdir=${BOOTSTRAP_DIR}

.PHONY: bootstrap-package
bootstrap-package: patch
	${SETENV} ${MAKE_ENV} \
	    PATH=${BOOTSTRAP_DIR}/bin:${PORTPATH} \
	    SWIFT_BUILD_ROOT=${WRKBUILD} \
	  ${WRKSRC}/swift/utils/build-script \
	    -j${MAKE_JOBS} \
	    --native-clang-tools-path=/usr/bin \
	    --build-subdir=${WRKBUILD}/bootstrap \
	    --extra-cmake-options=-DBRIDGING_MODE=PURE \
	    --install-prefix=${TRUEPREFIX} \
	    --llvm-targets-to-build=host \
	    --swift-install-components="${BOOTSTRAP_COMPONENTS}" \
	    --release -A \
	    --foundation \
	    --install-swift \
	    --install-foundation \
	    --install-libdispatch \
	    --skip-early-swift-driver \
	    --installable-package=${WRKDIR}/swift-bootstrap-${V}-${MACHINE_ARCH}.tar.gz

.include <bsd.port.mk>
