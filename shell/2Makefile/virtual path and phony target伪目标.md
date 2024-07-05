# Virtual path
```make
VPATH = src:../headers # search src and ../headers if current dir don't have dependency and target
# if not set VPATH, make will find dependency and target at current dir only
```
# phony target
```make
.PHONY : clean  # specify usable files with the same name as cmd : clean
```
