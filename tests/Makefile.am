# SPDX-License-Identifier: GPL-2.0+
# Makefile.am

AUTOMAKE_OPTIONS = serial-tests
SUBDIRS = src

TESTS =

TESTS_ENVIRONMENT = \
	if [ -z $$SCRATCH_MNT ]; then \
		export SCRATCH_MNT=/tmp/erofstest/scratch;	\
		mkdir -p $$SCRATCH_MNT 2>/dev/null; \
	fi; \
	if [ -z $$TEST_MNT ]; then \
		export TEST_MNT=/tmp/erofstest/test;	\
		mkdir -p $$TEST_MNT 2>/dev/null; \
	fi; \
	if [ -z $$RESULT_DIR ]; then \
		export RESULT_DIR=`pwd`/results;	\
		mkdir -p $$RESULT_DIR/erofs 2>/dev/null; \
		mkdir -p $$RESULT_DIR/fscache 2>/dev/null; \
	fi; \
	[ -z $$MKFS_EROFS_PROG ] && export MKFS_EROFS_PROG=../mkfs/mkfs.erofs; \
	[ -z $$FSCK_EROFS_PROG ] && export FSCK_EROFS_PROG=../fsck/fsck.erofs; \
	[ -z $$EROFSFUSE_PROG ] && export EROFSFUSE_PROG=../fuse/erofsfuse;

if ENABLE_LZ4
TESTS_ENVIRONMENT += export lz4_on=1;
endif
if ENABLE_LZ4HC
TESTS_ENVIRONMENT += export lz4hc_on=1;
endif
if ENABLE_LIBLZMA
TESTS_ENVIRONMENT += export lzma_on=1;
endif

# 001 - test if unknown algorithm is specificed
TESTS += erofs/001

# 002 - mkfs & test short symlink (fast symlink)
TESTS += erofs/002

# 003 - mkfs & test long symlink (non-fast symlink)
TESTS += erofs/003

# 004 - mkfs & test character/block device
TESTS += erofs/004

# 005 - mkfs & test pipe
TESTS += erofs/005

# 006 - verify the uncompressed image
TESTS += erofs/006

# 007 - check for bad lz4 versions
TESTS += erofs/007

# 008 - verify lz4 compressed image
TESTS += erofs/008

# 009 - verify lz4hc compressed image
TESTS += erofs/009

# 010 - (legacy image) verify lz4 compressed image
TESTS += erofs/010

# 011 - (legacy image) verify lz4hc compressed image
TESTS += erofs/011

# 012 - check the hard-link functionality
TESTS += erofs/012

# 013 - check if hardlinked directories are allowed
TESTS += erofs/013

# 014 - check if cross-device submounts are handled properly
TESTS += erofs/014

# 015 - regression test for battach on full buffer block
TESTS += erofs/015

# 016 - verify the uncompressed image with 2-level random files
TESTS += erofs/016

# 017 - check the compress-hints functionality
TESTS += erofs/017

# 018 - verify lzma compressed image
TESTS += erofs/018

# 019 - check extended attribute functionality
TESTS += erofs/019

# 001 - check inline/non-inline/multidev layout in fscache mode
TESTS += fscache/001

# 002 - test error path handling when OPEN request fails
TESTS += fscache/002

# 003 - test remounting erofs when user daemon has changed with different tag
TESTS += fscache/003

# 004 - test writing to premature anon_fd.
TESTS += fscache/004

# 005 - test if system could recover from previous wrong behaved user daemon
TESTS += fscache/005

# 006 - test user daemon closing anon_fd prematurely
TESTS += fscache/006

# 007 - test the behavior when user daemon fails to handle READ request
TESTS += fscache/007

# 008 - erofs-utils compiling test
TESTS += fscache/008

# 009 - erofs-utils compiling test (readahead)
TESTS += fscache/009

# 010 - lseek test
TESTS += fscache/010

# 011 - test the time sequence of closing device fd before closing anonymous fds
TESTS += fscache/011

# 012 - test if the pending requests could be completed when daemon gets killed
TESTS += fscache/012

# 013 - test if 'inuse' and 'cull' cmds work as expected
TESTS += fscache/013

# 014 - test if multiple erofs filesystem instances can be mounted at the same time
TESTS += fscache/014

# 015 - test shared domain
TESTS += fscache/015

EXTRA_DIST = common/rc erofs fscache

clean-local: clean-local-check
.PHONY: clean-local-check
clean-local-check:
	-rm -rf results
