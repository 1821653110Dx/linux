# var
```make
OBJS = kang.o yul.o	# save ['kang.o', 'yul.o'] to OBJS  # OBJS is the predefined var, whose meaning is objects to be compiled
CC = gcc	# save 'gcc' to CC ; CC refers to compiler
CFLAGS = -Wall -O -g	# save '-Wall -O -g' to CFLAGS # CFLAGS refers to compilation options

sunq : $(OBJS)	# dependency of sunq = { OBJS }. if sunq not exsist or any dependency has been updated
	$(CC) $(OBJS) -o sunq	# link { OBJS } into executable sunq by { CC }
kang.o : kang.c kang.h	# dependency of kang.o = kang.c, kang.h. if kang.o not exsist or any dependency has been updated
	$(CC) $(CFLAGS) -c kang.c -o kang.o	# compile kang.c into executable kang.o with { CC }, extra opt = { CFLAGS }
yul.o : yul.c yul.h	# dependency of yul.o = yul.c, yul.h. if yul.o not exsist or any dependency has been updated
	$(CC) $(CFLAGS) -c yul.c -o yul.o	# compile yil.c into executable yul.o with { CC }, extra opt = { CFLAGS }
```
```make
FOO ?= bar	# save bar to FOO if empty, oherwise remains
```
```make
Main = hello.o hello-1.o	# def list Main = [hello.o, hello-1.o]
Main += hello-2.o	# append hello-2.o to Main
```
```make
OBJS = kang.0 yul.0	# set OBJS = ['kang.o','yul.o']
CC = gcc	# set CC = 'gcc'
CFLAGS = -Wall -O -g	# set CFLAGS = '-Wall -O -g'

sunq : $(OBJS)	# dependency of sunq = { OBJS }. if sunq not exist or any dependency update
	$(CC) $^ -o $@	# $^ : all needed denpendencies ; $@ : default output file
kang.o : kang.c kang.h	# dependency of kang.o = ['kang.c', 'kang.h']. if kang.o not exist or any dependen cy update
	$(CC) $(CFLAGS) -c $< -o $@	# $< = first denpendency
yul.o : yul.c yul.h	# denpendency of yul.o = ['yul.c', 'yul.h']. if yul.o not exist or any denpendency update
	$(CC) $(CFLAGS) -c $< -o $@
```
# const
```make
dir := /foo/bar	# def const dir = /foo/bar
```
