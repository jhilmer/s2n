#
# Copyright 2014 Amazon.com, Inc. or its affiliates. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License").
# You may not use this file except in compliance with the License.
# A copy of the License is located at
#
#  http://aws.amazon.com/apache2.0
#
# or in the "license" file accompanying this file. This file is distributed
# on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either
# express or implied. See the License for the specific language governing
# permissions and limitations under the License.
#

OBJS = $(wildcard ../utils/*.o ../stuffer/*.o ../tls/*.o ../iana/*.o ../crypto/*.o ../error/*.o ../libcrypto-root/lib/libcrypto.a)

.PHONY : all
all: libs2n.a libs2n.so libs2n.dylib

include ../s2n.mk

libs2n.a: ${OBJS}
	ar cru libs2n.a ${OBJS}
	ranlib libs2n.a

libs2n.so: ${OBJS}
	${CC} -shared ${LIBS} -o libs2n.so ${OBJS}

libs2n.dylib: ${OBJS}
	test ! -f /usr/lib/libSystem.dylib || libtool -dynamic ${LIBS} -o libs2n.dylib ${OBJS}
