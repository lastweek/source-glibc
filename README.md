# GLIBC Source Code (v2.30)

For fun.

- Heads up: THe coding style is old-fashioned and alien-like.
- Dynamic linker: `elf/rtld.c`.
    - ELF's `.interp` section points to the dynamic linker, and here it is.
    - `dl_main()`: I guess this function is the entry point of the dynamic linker.
       Or maybe `dl_start()`. I don't know.
       Anyhow, the runtime virtual address of the dynamic linker is written into the `GOT[2]` slot,
       which is reserved for the dynamic linker.
    - Inside `dl_main()`, you can see how `LD_PRELOAD` is handled before the normal library scan.
- Start function name: `__libc_start_main`.
    - One thing I came across while building the ELF loader is the AUX array.
      It's an array setup by the kernel loader to pass some general information
      to the dynamic linker. It's implicitly setup in the original stack.

## Fun Read

- [System V Application Binary Interface](https://uclibc.org/docs/psABI-x86_64.pdf)
- [How the ELF Ruined Christmas](https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-di-frederico.pdf)

