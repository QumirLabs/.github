# QumirLabs

We build open-source compilers and analytical systems that run
natively and in the browser.

Our projects share a compiler foundation built on LLVM, with a focus
on clear architecture, efficient execution, and reusable components.

### Qumir — the oz-lang compiler and runtime

Qumir implements the compiler and runtime for **oz-lang**, an embeddable
typed language. **Kumir**, the educational language with Russian keywords,
is implemented as a higher-level frontend on top of this foundation.

Use oz-lang to:

- Embed typed computations and user-defined functions in C++ applications.
- Generate numerical and data-processing kernels, including SQL query
  kernels in QumirDB.
- Build domain-specific languages and experiment with compiler transformations.

Qumir supports interpretation, native JIT and ahead-of-time compilation,
and WebAssembly through a shared compiler pipeline.

For example, keep the positive elements of a SIMD vector:

```core
(block
  (use Vector)
  (fun <main> ()
    (block
      (var values = (vec -3 4 -1 8))
      (var positive = (> values 0))
      (output
        (call builtin::select positive values (vec 0 0 0 0))
        "\n"))))
```

Prints `{0, 4, 0, 8}`.

[Source](https://github.com/QumirLabs/qumir) ·
[oz-lang tutorial](https://github.com/QumirLabs/qumir/blob/master/docs/arch/core-lang.md) ·
[Try online](https://qumir.dev)

### QumirDB — compiled SQL analytics

An analytical SQL engine for Parquet, built on Qumir.

Queries compile to native code or WebAssembly. Custom functions written
in Rust can be optimized together with the query, bringing domain-specific
computation into the same compiled pipeline.

[Source](https://github.com/QumirLabs/qumirdb) ·
[Try online](https://db.qumir.dev)

---

We care about understandable systems, coherent design, and performance
backed by measurements.

Explore the code, try the playgrounds, or bring a question, bug report,
or idea to either repository.
