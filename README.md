# GPU-Accelerated Inclusive Scan in Julia

This repository showcases a high-performance implementation of the **Inclusive Scan** algorithm (Blelloch Scan) developed for the **QEDjl-project** ecosystem. The project was completed as part of a Master's level curriculum.

## Technical Contribution

This implementation focuses on leveraging **CUDA.jl** for efficient parallel prefix sum operations on NVIDIA GPUs.

### Core Features
* **Blelloch Scan Pattern:** Efficient two-phase (Up-sweep and Down-sweep) implementation in CUDA kernels.
* **Dynamic Shared Memory:** Optimized data movement using `CuDynamicSharedArray` to maximize throughput.
* **Scalability:** Support for large arrays through block-based scanning and increment addition.

### Authors & Roles
While I am the primary maintainer of this repository, the project was a collaborative effort with **Bulat Fakhrutdinov**:

* **Timur Gildeev (@gtimuri):** Developed the core CUDA kernels (`_scanBlockKernel!`, `_addIncrementsKernel!`) and the high-level `largeArrayScanInclusive!` interface.
* **Bulat Fakhrutdinov (@Korjick):** Engineered the testing suite and validation logic to ensure numerical stability and performance.

## Project Structure
* `src/InclusiveScans.jl`: Core algorithm and GPU kernels.
* `test/test-basic-test.jl`: Validation suite comparing GPU results with CPU references.
* `Project.toml`: Project dependencies (CUDA, Random) and compatibility.

## Verification
To run the tests and verify the implementation:
```julia-repl
julia --project=@.
pkg> activate .
pkg> test
