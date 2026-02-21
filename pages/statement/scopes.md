# Solution Scopes

We are only looking to solve a subset of the VM use cases. Even though, the architecture solves all the problems. It makes the VM ideal for only the following use cases:

- High Performance Computing
- Statically Compiled Codebases/Scripts
- Scripts that don't depend on `eval()`-ing untrusted codebases
- Codebases where FFI is an important abstraction
- Server Applications

## What is NOT in our scope

Please note that the following is not even remotely in our scope :

- Isolation of the codebase from the hardware
- Running untrusted codebases
- Garbage Collection
- Automatic Memory Management[\*](#1-automatic-memory-management)

## Our Solution Scopes

As important as it is to understand the issue, it is equally important to narrow down our scope to not drift from our trajectory.

Our scope is contained to :

- Deterministic Execution
- Absense of Garbage Collection
- Just-in-Time Compilation
- Cached Just-in-Time Compilation
- Cached Interpreter Bytecode for hot startups
- Profile-Guided Metadata (AOT-Guided JIT)
- Minimal Cost FFI (Foreign Function Interface)
- Async-Capable FFI (FFI with State Machine Implementations that works)
- SIMD-first Vectored ISA
- Async-Aware VM, JIT Executor
- Separation between Async (Green) and System (OS) Threads
<!-- TODO: Add more -->

#### Notes

##### 1. Automatic Memory Management

It is important to distinguish "Automatic Memory Management" from garbage collection since languages like Rust, Swift have proved it is possible without Garbage Collection architecture.
