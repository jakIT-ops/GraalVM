# difference between the CE and EE versions of GraalVM


On the performance front, the enterprise edition (EE) adds vectorization, a state-of-the-art inliner, compressed oops, profile guided optimizations... also the ability to emit debug symbols. You can build faster native images, that consume less memory, that can be specifically tuned for your workload, and all that can be consumed by the native tooling (gdb).

On the security front, there are optional Spectre mitigations, at the expense of some performance. There's also Sulong managed, which allows to run native code (compiled to LLVM bitcode) in a safe way, think ArrayIndexOutOfBoundsException instead of segfaults.

This answer is definitely not comprehensive and may be outdated as soon as some features are open-sourced to the community edition and/or the GraalVM team adds even more advanced features to the enterprise edition.
