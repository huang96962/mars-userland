#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2011, 2013, Oracle and/or its affiliates. All rights reserved.
#

include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		g11n
COMPONENT_VERSION=	1.00
COMPONENT_REVISION=	0
COMPONENT_PROJECT_URL=	https://github.com/huang96962/g11n
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/archive/v$(COMPONENT_VERSION).tar.gz
COMPONENT_SUMMARY_UTF8=	Iconv modules for UTF-8 Locale
COMPONENT_SUMMARY_EXTRA= Iconv modules extra files
COMPONENT_SUMMARY_UNICODE= iconv modules for Unicode
COMPONENT_SUMMARY_MAN= 	Iconv Man Pages for UTF-8 Locale
COMPONENT_SUMMARY_XSH=	XSH4 conversion for ISO Latin character sets

include ../../make-rules/prep.mk
include ../../make-rules/justmake.mk
include ../../make-rules/ips.mk

# idn include files
COMPONENT_PRE_BUILD_ACTION = (cd $(PWD)/$(COMPONENT_SRC) ; \
	ln -s $(PWD)/idn src/lib/iconv/utf-8/idn \
	)

COMPONENT_COPY_ACTION = 

# build and install
COMPONENT_BUILD_ACTION = (cd $(PWD)/$(COMPONENT_SRC) ; export PATH+=:/opt/sunstudio12.1/bin ; \
        export SRC=$(PWD)/$(COMPONENT_SRC) ; \
        export CLOSED_BUILD=\# ; \
        export PKGARCHIVE=$(PWD)/$(COMPONENT_SRC) ; \
	make all 2>&1 | tee make.log ; \
       	make install 2>&1 | tee install.log \
	) 

# link to proto dir
COMPONENT_POST_BUILD_ACTION = ( \
	rm -rf $(BUILD_DIR)/prototype ; \
	mkdir -p $(BUILD_DIR)/prototype ; \
	ln -s $(PWD)/$(COMPONENT_SRC)/proto/i386/fileroot/ $(BUILD_DIR)/prototype/i386 \
	)

build:  $(BUILD_32)

#REQUIRED_PACKAGES += consolidation/l10n/l10n-incorporation 
REQUIRED_PACKAGES += system/library
