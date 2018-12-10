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
# Copyright (c) 2014, 2018, Oracle and/or its affiliates. All rights reserved.
#

include ../../../make-rules/shared-macros.mk

#export PROTO_DIR=	$(BUILD_DIR)/i86

COMPONENT_NAME=		db-derby
COMPONENT_VERSION=      10.14.2.0
#10.6.2.1
COMPONENT_REVISION=     0
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)-src
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=  http://mirrors.hust.edu.cn/apache/db/derby/$(COMPONENT_NAME)-$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)

ORIGIN_PATH=		javadb-package-files

include $(WS_MAKE_RULES)/prep.mk
include $(WS_MAKE_RULES)/justmake.mk
include $(WS_MAKE_RULES)/ips.mk

# only the source files built successfully,
# so copy the document files from original package.
# view build.xml for build command, default is "ant all".
# must move all files to prototype/i386

COMPONENT_PRE_BUILD_ACTION = (cp -rf $(PWD)/$(ORIGIN_PATH)/* $(@D)/)

COMPONENT_BUILD_ACTION = cd $(@D) ; ant all

COMPONENT_POST_BUILD_ACTION = (cd $(PWD); mkdir -p $(PWD)/build/prototype/i386; \
			    mv $(@D)/* $(PWD)/build/prototype/i386 )

build: $(BUILD_32)

clean::
	$(RM) -r $(PWD)/build
	$(RM) -r $(PWD)/$(COMPONENT_NAME)-$(COMPONENT_VERSION)-doc-src


