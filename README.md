# Noah Parsons

**Independent researcher in computational physics, systems software and scientific-software verification · Newcastle, Wyoming**

[ORCID 0009-0000-7224-6040](https://orcid.org/0009-0000-7224-6040) · [parsons.m.noah@gmail.com](mailto:parsons.m.noah@gmail.com)

I build software for physics and systems, and I test whether scientific software gives correct answers. Most of my work starts from the same question: when a program reports success, how do we know the result is right? That question has led to a compiler for classical mechanics, an operating system written from scratch, a study of three dynamics engines against independent references, fixes in Project Chrono, SciPy and CFAST, and an open journal for this kind of work.

---

## Recent

- **October 2026.** A regression I reported in SciPy's stiff ODE solver ([#26384](https://github.com/scipy/scipy/issues/26384)) was traced to an indexing error in the Fortran-to-C translation of `vode` and fixed in [#26387](https://github.com/scipy/scipy/pull/26387).
- **October 2026.** Founded [Examen Silentii](https://examen-silentii.github.io), an open journal of independent examinations of scientific software and research data.
- **October 2026.** Faults I reported in Project Chrono's assembly analysis were fixed upstream ([#846](https://github.com/projectchrono/chrono/issues/846), [#847](https://github.com/projectchrono/chrono/issues/847), [#851](https://github.com/projectchrono/chrono/issues/851)).
- **October 2026.** A documentation discrepancy found during my pyOpenSci review of PyCFAST was reported upstream to NIST's CFAST ([firemodels/cfast#2553](https://github.com/firemodels/cfast/issues/2553)).

---

## Research

### Verification of rigid-body dynamics engines
A differential study of MechanicsDSL, `sympy.physics.mechanics` and Drake, adjudicated against closed-form references written in NumPy alone, sharing no library with any engine under test. The frozen suite of 55 cases covers six axes, three mechanism families (pendulum chains, slider-crank, cart-pole), regular and chaotic regimes, and constrained and unconstrained pathways.

The engines agree to machine precision on every adjudicated case. An apparent difference in reach turned out to measure how each engine was driven, not the engine itself. Every engine, and the independent reference, reports success at an unstable equilibrium while producing motion the exact solution does not have: a shared failure of floating-point arithmetic that differential testing cannot detect.

- Manuscript: *Limits of Differential Testing: Three Rigid-Body Dynamics Engines Under Library-Independent Adjudication* (in submission)
- Artefacts: [doi:10.5281/zenodo.22315172](https://doi.org/10.5281/zenodo.22315172)
- Companion study: *A shared blind spot in numerical quadrature*, [doi:10.5281/zenodo.22557771](https://doi.org/10.5281/zenodo.22557771)
- Technical reports TR-2026-01 *Reference Oracle*, TR-2026-02 *Sympy Adapter*, TR-2026-03 *Drake Adapter*, TR-2026-04 *Week One Findings*, TR-2026-05 *Three Families*, TR-2026-06 *Driving the Engines*
- Public conformance page: each new engine release is run automatically against the reference cases

### Benchmark problem for the IFToMM multibody library
*Cart-pole with a light cart*: a problem in which the mass matrix nearly loses rank twice per swing, with reference solution and convergence record. Submitted to the IFToMM benchmark library, October 2026. [light-cartpole-benchmark](https://github.com/Noah-Parsons/light-cartpole-benchmark)

### Coverage of withdrawal dates in the Western Interconnection queue
Tests whether the records behind Berkeley Lab's published median time-to-withdrawal for the non-ISO West represent the region. Only 636 of 5,277 western withdrawals (12.1%) carry a usable date, from six of 31 transmission providers. The reporting subset is unrepresentative, but reweighting moves the median only from 1.83 to 1.77 years: the binding limitation is coverage, not composition. [doi:10.5281/zenodo.22547678](https://doi.org/10.5281/zenodo.22547678) · [western-queue-reporting](https://github.com/Noah-Parsons/western-queue-reporting)

### Galactic algorithms, measured
An empirical study of the fusion tree against practical search structures: 10 structures, n from 2^8 to 2^25, 48,600 timings, two compilers, with zero failures across 20 million correctness checks. The fusion tree never beats a well-built B-tree, though it does beat binary search at large n. Extended into new structures, ClusterJump and SplineIndex, under pre-registered plans. [doi:10.5281/zenodo.22718523](https://doi.org/10.5281/zenodo.22718523) [fusion-tree-benchmark](https://github.com/Noah-Parsons/fusion-tree-benchmark)

---

## Software

### MechanicsDSL
A domain-specific language and compiler for physical systems. You write a Lagrangian or Hamiltonian in LaTeX-inspired notation; the symbolic engine, built on SymPy, derives the equations of motion, and the compiler generates code in any of twelve target languages, including dependency-free C for Cortex-M microcontrollers, plus a JAX runtime backend. MIT licensed. [doi:10.5281/zenodo.17771040](https://doi.org/10.5281/zenodo.17771040)

| Package | Purpose |
|---|---|
| [mechanicsdsl](https://github.com/MechanicsDSL/mechanicsdsl) | Core compiler, published on PyPI as `mechanicsdsl-core` |
| [mechanicsdsl-embedded](https://github.com/MechanicsDSL/mechanicsdsl-embedded) | Deployment to Arduino, Raspberry Pi and ARM devices; C++ and `no_std` Rust for real-time control. Published on PyPI as `mechanicsdsl-embedded` |
| [mechanicsdsl-ros2](https://github.com/MechanicsDSL/mechanicsdsl-ros2) | Compilation of physical systems to ROS 2 packages. Published on PyPI as `mechanicsdsl-ros2` |
| [mechanicsdsl-unity](https://github.com/MechanicsDSL/mechanicsdsl-unity) | Simulation components for Unity and Unreal Engine. Published on PyPI as `mechanicsdsl-unity` |
| [mechanicsdsl-datasets](https://github.com/MechanicsDSL/mechanicsdsl-datasets) | Reference datasets for parameter estimation and inverse-problem benchmarks. Published on PyPI as `mechanicsdsl-datasets` |
| [mechanicsdsl-notebooks](https://github.com/MechanicsDSL/mechanicsdsl-notebooks) | Jupyter notebooks across the supported physics domains. Published on PyPI as `mechanicsdsl-notebooks` |

Release 2.1.3 was a correctness release: the project's own adversarial suite found and fixed faults in which the compiler produced wrong results while reporting success.

### NexusOS
An x86-64 operating system written from scratch: custom bootloader, long-mode kernel, preemptive scheduler with mutex, semaphore and condition-variable primitives, four-level paging, a FAT12 filesystem and a compositing window manager. No GRUB, no Limine, no tutorial framework. It boots on real hardware by legacy BIOS and by UEFI, and ran a five-hour soak test of about three million context switches with its synchronisation invariants intact. [NexusOS](https://github.com/Noah-Parsons/NexusOS) · Book: [*Build Your Own OS*](https://leanpub.com/build-your-own-os)

### Legacy software recovery
Recovered a 1980s DIBOL/DBL accounting system: archived its source, rebuilt it from that source, traced its history from RT-11 through Unix to DOS, and compiled 742 of its 775 files unmodified under Synergy/DE v12. (Private repository, with the owner's permission.)

---

## Contributions to other projects

| Project | Contribution | Status |
|---|---|---|
| [Project Chrono](https://github.com/projectchrono/chrono) | Reported faults in assembly-level accelerations, the Python bindings and `DoFrameKinematics` ([#846](https://github.com/projectchrono/chrono/issues/846), [#847](https://github.com/projectchrono/chrono/issues/847), [#851](https://github.com/projectchrono/chrono/issues/851)) | Fixed |
| Project Chrono | Regression test of `DoAssembly` on coupled mechanisms across three solvers ([#856](https://github.com/projectchrono/chrono/pull/856)) | In review |
| [SciPy](https://github.com/scipy/scipy) | Reported a stiff-solver regression in `integrate.ode` (vode) since 1.17.0 ([#26384](https://github.com/scipy/scipy/issues/26384)) | Fixed in [#26387](https://github.com/scipy/scipy/pull/26387) |
| [CFAST](https://github.com/firemodels/cfast) (NIST) | Input-guide limits that disagree with the source, found in review ([#2553](https://github.com/firemodels/cfast/issues/2553)) | Accepted |
| [PyCFAST](https://github.com/bewygs/pycfast) | Issues found in review ([#231](https://github.com/bewygs/pycfast/issues/231), [#232](https://github.com/bewygs/pycfast/issues/232)) | Fixed in [#236](https://github.com/bewygs/pycfast/pull/236), [#237](https://github.com/bewygs/pycfast/pull/237) |
| [Picht](https://github.com/rolypolytoy/picht) | Six issues found in review: Windows installation conflict ([#7](https://github.com/rolypolytoy/picht/issues/7)), Getting Started example that does not run on 2.2.0 ([#8](https://github.com/rolypolytoy/picht/issues/8)), a test suite that checks structure but not physical correctness ([#9](https://github.com/rolypolytoy/picht/issues/9)), a demo script shipped inside the package ([#10](https://github.com/rolypolytoy/picht/issues/10)), inconsistent packaging metadata ([#11](https://github.com/rolypolytoy/picht/issues/11)) and untagged releases ([#12](https://github.com/rolypolytoy/picht/issues/12)) | Reported |
| [PUDL archiver](https://github.com/catalyst-cooperative/pudl-archiver) (Catalyst Cooperative) | Archiver for PacifiCorp's interconnection queue ([#1409](https://github.com/catalyst-cooperative/pudl-archiver/pull/1409)) | In review |

---

## Peer review and service

- **Founding editor**, [Examen Silentii](https://examen-silentii.github.io), journal of software and data verification
- **Reviewer**, pyOpenSci: Picht ([#242](https://github.com/pyOpenSci/software-submission/issues/242)) and PyCFAST ([#318](https://github.com/pyOpenSci/software-submission/issues/318))
- **Reviewer**, Journal of Open Source Software
- **Member**, US Research Software Engineer Association
- **Stakeholder**, Wyoming Energy Authority transmission study (SF0102)

---

## Publications

**Peer-reviewed**
- Parsons, N. (2025). Strategic grid modernization for enhanced energy security and industrial competitiveness: A multi-pillar framework for the United States. *Applied Journal of Economics, Law and Governance*, 1(2), 149–172. [doi:10.57017/ajelg.v1.i2(2).03](https://doi.org/10.57017/ajelg.v1.i2(2).03)

**Editorial**
- Parsons, N. (2026). Silent failures in scientific software: On the founding of Examen Silentii. *Examen Silentii*, 1. [doi:10.5281/zenodo.23290573](https://doi.org/10.5281/zenodo.23290573)

**Book**
- Parsons, N. *Build Your Own OS*. Leanpub. [leanpub.com/build-your-own-os](https://leanpub.com/build-your-own-os)

**Preprints and archived studies**
- Parsons, N. (2026). Who reports withdrawal dates in the Western Interconnection queue, and does it matter? [doi:10.5281/zenodo.22547678](https://doi.org/10.5281/zenodo.22547678)
- Parsons, N. (2026). A shared blind spot in numerical quadrature. [doi:10.5281/zenodo.22557771](https://doi.org/10.5281/zenodo.22557771)
- Parsons, N. (2026). Artefacts for *Limits of Differential Testing*. [doi:10.5281/zenodo.22315172](https://doi.org/10.5281/zenodo.22315172)
