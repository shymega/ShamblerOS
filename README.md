# shyOS

shyOS is my ([@shymega][shymega]) personal attempt at creating a hobby
operating system with my own take on how an OS should be like.

shyOS is _not_ like Linux, which is a monolithic kernel with
dynamically-loadable modules. It bears a closer resemblance to MINIX,
Plan 9 and Inferno, but written in [Rust][rust], a thread-safe systems
programming language, with *some* exceptions for low-level components.

## Feature outline:

Worth noting: shyOS is **NOT** designed to be a Unix-like/POSIX
operating system.

### Core system.

- Microkernel
  - Minimalist microkernel.
    - Perform an minimal amount of functions in kernel-space as possible.

    - Perform nearly all functions in user-space.

   - Aim for nearly all of the kernel to be written in [Rust][rust].
      - With exceptions for low-level components, which cannot be
        written in Rust.
      - Non-Rust components **must** be thread-safe *and* thoroughly
        tested continously.

- POSIX emulation layer

  This is to provide compatibility to other OSes, which may not
  necessarily conform to shyOS's conventions.

  * Sublayers - these provide extensions to the 'root' POSIX
    emulation layer.
    * Linux kernel emulation sublayer.
    * FreeBSD emulation sublayer.
  * Translate 'foreign' syscalls to native syscalls for shyOS.

  Worth noting: this will (probably) cause a noticeable slow down.

- Filesystem:
  * Filesystem similar to ZFS/BTRFS.

- License:
  Haven't decided yet. I'd like to use GPLv3, but I'm worried that it'll make things difficult further down the line.
  If I had to use a permissive license, I'd go with Apache License 2.0.

[shymega]: https://github.com/shymega
[rust]: https://www.rust-lang.org
