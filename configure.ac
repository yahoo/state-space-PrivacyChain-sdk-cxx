dnl This is a GNU -*- autoconf -*- specification that is processed by Autoconf.
dnl Copyright Yahoo Inc. 2021.
dnl Licensed under the terms of the Apache-2.0 license.
dnl See the LICENSE file in https://github.com/yahoo/PrivacyChain-sdk-c++/blob/master/LICENSE for terms.
dnl
dnl ./buildconf &&
dnl ./configure --prefix=/opt/iab/privacychain --with-std-tunitas=/opt/tunitas --with-std-scold=/opt/std/scold &&
dnl make &&
dnl make check &&
dnl make install &&
dnl echo OK DONE
dnl
AC_INIT([privacychain-sdk-c++], [0.2.0], [state-space@yahooinc.com])
TF_INIT(AC_PACKAGE_NAME, AC_PACKAGE_VERSION, AC_PACKAGE_BUGREPORT)

dnl These options are also in the Makefile.am in AUTOMAKE_OPTIONS
dnl AM_INIT_AUTOMAKE([no-define subdir-objects foreign])
AM_SILENT_RULES([yes])

AC_CONFIG_SRCDIR([src/iab/privacychain/namespace.xcpp])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile])

#
# To have submodules
#   configure.ac: TF_CONFIG_SUBMODULES([submodules], [...list...])
#   Makefile.am:  SUBDIRS = @subdirs@
# to have no submodules
#   comment these schemes out in both places
#

TF_COMPONENT_METADIRECTORY_TIERS
TF_WITH_USR_LOCAL
TF_ENABLE_GNU
TF_ENABLE_GDB
TF_ENABLE_GCC
TF_ENABLE_MOCK_BUILD
TF_ENABLE_LIBTOOL_NO_INSTALL

#
# To perform production builds, only the WITH_STD mentions must be replicated in
#   Makefile.am: INSTALLATION_AREAS
#
# To perform development builds, the mentions herein must be replicated faithfully
#   Makefile.am: DEVLOPMENT_AREAS, TESTING_AREAS
#   Makefile.am: INSTALLATION_AREAS (same as before)
#

dnl ---> Some day when State Space Solutoins is more mature
dnl --->      and when IAB PrivacyChain is "standardized"
dnl --->      and when Hyperledger Fabric 1.4 (until 2020), 2.0 (since 2020), 3.0 (sic)
dnl ---> TF_WITH_STD([iab-privacychain])
dnl ---> TF_WITH_SUBSYSTEM([iab-privacychain-sdk], [], [The IAB PrivacyChain C++ Client-side SDK])

TF_WITH_STD([state-space])
# WATCHOUT - this simplistic interface will be subsumed when Hyperledger Fabric C++ (below) is ready
TF_WITH_SUBSYSTEM([state-space-fabric-sdk], [], [The State Space ersatz Hyperledger Fabric C++ Client-side SDK])
dnl Release 01 (Maximum Hammer) DOES NOT use this
dnl Release 02 (Intensive Toothbrush) MIGHT NOT use this
TF_WITH_STD([hyperledger-fabric])
TF_WITH_SUBSYSTEM([hyperledger-fabric-sdk], [], [The Hyperledger Fabric C++ Client-side SDK])
dnl not yet ---> TF_WITH_SUBSYSTEM([hyperledger-fabric-db], [], [The Hyperledger Fabric Data Base C++ Client-side SDK])
dnl not yet ---> TF_WITH_SUBSYSTEM([hyperledger-fabric-ca], [], [The Hyperledger Fabric Certificate Authority C++ Client-side SDK])
dnl not yet ---> TF_WITH_SUBSYSTEM([hyperledger-fabric], [], [The Hyperledger Fabric C++ Client-side SDK])
dnl not yet ---> TF_WITH_SUBSYSTEM([hyperledger], [], [The Hyperledger C++ Client-side SDK])

TF_WITH_STD([tunitas]) dnl application data types
TF_WITH_SUBSYSTEM([temerarious-flagship], [], [The Tunitas Build System])
TF_WITH_SUBSYSTEM([tunitas-basics], [], [The Tunitas Basics Components])
TF_WITH_SUBSYSTEM([tunitas-butano], [], [The Tunitas Butano TCF v1.1])

TF_WITH_STD([scold]) dnl the core modules system
# And mention these in $(DEVELOPMENT_AREAS) in Makefile.am
TF_WITH_MODULE([json])
TF_WITH_MODULE([langu]) dnl else module-shell
TF_WITH_MODULE([nonstd])
TF_WITH_MODULE([rabinpoly])
TF_WITH_MODULE([sys])
TF_WITH_MODULE([rigging]) dnl a.k.a. unit-rigging -> rigging-unit -> rigging (only); mention in Makefile.am TESTING_AREAS

dnl [[deprecating]] these are being subsumed into the v2.0-series work of one or more of langu, nonstd, options, sys
TF_WITH_MODULE([cppunit]) dnl And mention in $(TESTING_AREAS) in Makefile.am
TF_WITH_MODULE([posix])
TF_WITH_MODULE([shell]) dnl but prefer module-langu for langu::ish::shell
TF_WITH_MODULE([std])
TF_WITH_MODULE([string]) dnl a.k.a. c-string

TF_MSG_VERBOSE([compiler-specific (alphabetical)])
TF_WITH_NONSTD([cppunit]) dnl ... circa cppunit-1.14 or 1.16 is good
TF_WITH_NONSTD([gcc]) dnl ....... but modern gcc-11.2 & beyond is fine
TF_WITH_NONSTD([jsoncpp]) dnl ... but modern jsoncpp-1.8.4 is fine

AM_PROG_AR
LT_PREREQ([2.4.2])
LT_INIT
AC_PROG_CC
AC_PROG_CXX
AM_PROG_CC_C_O
TF_PROG_DC

TF_CHECK_CPPUNIT
TF_CHECK_JSONCPP
TF_CHECK_STD_FILESYSTEM dnl get @libstd_filesystem@ for Makefile.am

TF_FINALIZE
