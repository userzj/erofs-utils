# SPDX-License-Identifier: GPL-2.0+

ACLOCAL_AMFLAGS = -I m4

SUBDIRS = man lib mkfs dump fsck
if ENABLE_FUSE
SUBDIRS += fuse
endif

# testcases are handled in the end
SUBDIRS += tests
