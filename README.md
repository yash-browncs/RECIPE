RECIPE modified to cross-compile for gem5 based on ARM. Almost works (only needs ARM libtbb)

Use commands prefixed with `aarch64-linux-gnu-g++` in `build/makelog.txt` to build object files.
Be sure to replace absolute directory paths.
During linking be sure to use -static flag. It should show the following output:

Currently only uses P-BwTree, since other data structures have several other dependencies and/or
x86 only assembly instructions in source.

On installing ARM libtbb locally, just use -L/path/to/ARM/libtbb and -ltbb in the linker command. Copy 
the resulting binary to gem5 mount directory and run `./ycsb`. Use `libIndexes.a` and `yc.o` as precompiled 
object files for current source.

```
/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/bin/ld: cannot find -lboost_system
/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/bin/ld: cannot find -lboost_thread
/usr/lib/gcc-cross/aarch64-linux-gnu/9/../../../../aarch64-linux-gnu/bin/ld: cannot find -ltbb
```

TODO

Update README with exact commands
Rewrite Makefile in build/ with relative paths
Clean up unnecessary/unused folders (data structures except BwTree)