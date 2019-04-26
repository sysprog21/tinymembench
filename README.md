# tinymembench

This is a simple memory benchmark program, which tries to measure the peak
bandwidth of sequential memory accesses and the latency of random memory
accesses. Bandwidth is measured by running different assembly code for
the aligned memory blocks and attempting different prefetch strategies.

## Benchmark

The benchmark results for some hardware can be found in the wiki page:
    https://github.com/ssvb/tinymembench/wiki

## Build from source

This program can be compiled in either linux or windows (via mingw32 and msys)
by simply running make:
```shell
$ make
```

Adding extra optimization options is possible:
```shell
$ CFLAGS="-O2 -march=atom -mtune=atom" make
```

Example of crosscompiling for Arm:
```shell
$ CC=arm-linux-gnueabihf-gcc CFLAGS="-O2 -mcpu=cortex-a9" make
```

Example of crosscompiling and running the benchmark on Android device:
```shell
$ CC=arm-linux-gnueabihf-gcc CFLAGS="-O2 -mcpu=cortex-a8 -static" make
$ adb push tinymembench /data/local/tmp/tinymembench
$ adb shell /data/local/tmp/tinymembench
```
