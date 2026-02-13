# GPU-Accelerated Inclusive Scan in Julia

This repository showcases a high-performance implementation of the **Inclusive Scan** algorithm (Blelloch Scan) developed for the **QEDjl-project** ecosystem. The project was completed as part of a Master's level curriculum.

## Technical Contribution

This implementation focuses on leveraging **CUDA.jl** for efficient parallel prefix sum operations on NVIDIA GPUs.

### Core Features
* [cite_start]**Blelloch Scan Pattern:** Efficient two-phase (Up-sweep and Down-sweep) implementation in CUDA kernels[cite: 11, 13, 14].
* [cite_start]**Dynamic Shared Memory:** Optimized data movement using `CuDynamicSharedArray` to maximize throughput[cite: 9, 17].
* [cite_start]**Scalability:** Support for large arrays through block-based scanning and increment addition[cite: 16, 18, 19].

### Authors & Roles
While I am the primary maintainer of this repository, the project was a collaborative effort with **Bulat Fakhrutdinov**:

* [cite_start]**Timur Gildeev (@gtimuri):** Developed the core CUDA kernels (`_scanBlockKernel!`, `_addIncrementsKernel!`) and the high-level `largeArrayScanInclusive!` interface[cite: 9, 16, 17].
* [cite_start]**Bulat Fakhrutdinov (@Korjick):** Engineered the testing suite and validation logic to ensure numerical stability and performance[cite: 6, 7, 8].

## Project Structure
* [cite_start]`src/InclusiveScans.jl`: Core algorithm and GPU kernels[cite: 9].
* [cite_start]`test/test-basic-test.jl`: Validation suite comparing GPU results with CPU references[cite: 6].
* `Project.toml`: Project dependencies (CUDA, Random) and compatibility.

## Verification
To run the tests and verify the implementation:
```julia-repl
julia --project=@.
pkg> activate .
pkg> test