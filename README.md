# shyOS

shyOS is my (@shymega) personal attempt at creating a hobby operating
system with my own take on how an OS should be like.

shyOS takes from decades of computer science research, learns from the
best, and crafts it into the operating system that might, or might not
take off.

shyOS is _not_ like Linux, which is a monolithic kernel with
dynamically-loadable modules. It bears a closer resemblance to MINIX,
Plan 9 and Inferno, but written in [Rust][rust], a thread-safe systems
programming language, with *some* exceptions for low-level
components..

## Feature outline:

Worth noting: shyOS is **NOT** designed to be a `Unix-like`/POSIX
operating system. I (@shymega) am not intending to advertise shyOS as
such. Consider shyOS to be a progressive experiment.

### Core system.

- Microkernel (w/ potential VM, like Inferno)
  - Minimalist microkernel.
    - Perform an minimal amount of functions in kernel-space as possible.
      - Ideally 1% of functions in kernel-space.

    - Perform nearly all functions in user-space.
      - Ideally 99% of functions in user-space.

   - Aim for nearly all of the kernel to be written in [Rust][rust].
      - With exceptions for low-level components, which cannot be
        written in Rust (yet... the time is coming; brace yourselves!).
      - Non-Rust components **must** be thread-safe *and* thoroughly
        tested.

- POSIX emulation layer

  This is to provide compatibility to other OSes, which may not
  necessarily conform to shyOS's conventions.

  * Sublayers - these provide extensions to the 'root' POSIX
    emulation layer.
    * Linux kernel emulation sublayer.
    * FreeBSD emulation sublayer.
  * Translate 'foreign' syscalls to native syscalls for shyOS.

- Filesystem:
  * Distributed <-- like Plan 9..?
  * Choice of *type* of filesystem.
    The kernel will **not** care what type of filesystem (hierarchical
    vs. non-hierarchical design), as long as it can operate within the
    realms of the selected filesystem.

[rust]: https://www.rust-lang.org
