# The Problem

Virtual Machines are laggy, more or less of the time.

In fact, even production virtual machines are fundamentally built on the model of usage of
acoustic speculation with compilation and decompilation ecosystem as prevalent even in statically
typed programming languages.

## Impact

Such an outlook towards virtual machine systems would ultimately lead to reduced efficiency, JIT tax,
speculation tax, runtime tax, FFI overhead which results in a vendor lock in for the subsystems
and frameworks.

The solution to this problem, as has been devised, are as follows:

- **Intensive Speculation, Aggressive Optimization:** This is a paradigm that works, until it does not or until it overpays for the performance benefit. This is infinitely worse than compiling the code as a whole with programming tools like LLVM that already optimizes for the same task.
- **AOT:** Ahead of Time Compilation is a newer, emerging, solution to this issue that does address the core requirement, but it introduces some noteworthy, and sometimes dealbreaking considerations:
  1. **Baseline CPU instruction usage:** Let us say `binaryA` was targeted for 64-bit CPUs. That means it targets x86-64-v1 (baseline). That effectively means that the computation happens using instructions from older 128-bit instructions instead of modern 512-bit AVX512 instructions, which can process 512 bits in a single operation.
  2. **Platform based separate binary:** This is mostly an inconvenience, but a noteworthy one. This inconvenience turns into a burden as soon as we incorporate cpufeatures with binary.
  3. **A different league:** AOT is a fundamentally different league that also makes it incompatible with many existing products, like distributed servers on heteroarchitectures and heteroplatforms require recompilation on each node.

## Are VMs obsolete?

Ironically, even given the "solutions", VMs are far from being obsolete. They are thriving - even if inefficient. Noteworthy examples include :

- **JVM:** Used on billions of servers, including Code Editors like from the JetBrains fleet of code editors.
- **ART (and, formerly Dalvik):** Used in Android Mobiles.
- **Lua, JS, Python:** Well known scripting languages.

Yet, one form of VM is still missing - A VM with :

- Minimal overhead
- Efficient caching JIT
- Fast and efficient JIT compilation
- Async-friendly / cooperative
- Near machine-code ISA
- Fast warm-up

That is what the Sa VM Philosophically would want to target!

<!-- TODO: Add Real Life examples -->
