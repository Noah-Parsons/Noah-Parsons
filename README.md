## About

I am Noah Parsons, an independent researcher in Newcastle, Wyoming, working
across computational physics, systems software, and applied policy research.

## Active projects

### MechanicsDSL

A domain-specific language and compiler for physical systems. You write a
Lagrangian or Hamiltonian in LaTeX-inspired syntax; the symbolic engine (built
on SymPy) derives the equations of motion automatically, and the compiler
generates simulation code in your choice of twelve target languages. MIT
licensed, on PyPI as `mechanicsdsl-core`.

- [mechanicsdsl](https://github.com/MechanicsDSL/mechanicsdsl) — Core compiler.
  Write a Lagrangian, get a simulation. Twelve code generation backends,
  built on SymPy.
- [mechanicsdsl-datasets](https://github.com/MechanicsDSL/mechanicsdsl-datasets) —
  Reference datasets for physics parameter estimation and inverse problem
  benchmarking.
- [mechanicsdsl-embedded](https://github.com/MechanicsDSL/mechanicsdsl-embedded) —
  Deploy MechanicsDSL simulations to Arduino, Raspberry Pi, and ARM edge
  devices. Optimized C++ and no_std Rust for real-time closed-loop control.
- [mechanicsdsl-ros2](https://github.com/MechanicsDSL/mechanicsdsl-ros2) —
  Compile MechanicsDSL physical systems to ROS2 packages.
- [mechanicsdsl-unity](https://github.com/MechanicsDSL/mechanicsdsl-unity) —
  Simulation components for Unity and Unreal Engine, compiled from
  MechanicsDSL notation.
- [mechanicsdsl-notebooks](https://github.com/MechanicsDSL/mechanicsdsl-notebooks) —
  Jupyter notebooks demonstrating MechanicsDSL across the supported physics
  domains.

### NexusOS

[A small x86-64 operating system written from scratch.](https://github.com/GuiloScion/NexusOS)
Custom bootloader, long-mode kernel, preemptive scheduler with mutex,
semaphore, and condvar primitives, 4-level paging, FAT12 filesystem, and a
compositing window manager. No GRUB, no Limine, no tutorial framework, every
line original.

### Verification of Scientific Software

A differential study of three rigid-body dynamics engines, MechanicsDSL, sympy.physics.mechanics, and Drake, adjudicated against a closed-form reference implemented in NumPy alone, sharing no library with any engine under test. A 55-case adversarial suite across six axes, frozen before measurement, covering three mechanism families, regular and chaotic regimes, and constrained and unconstrained pathways. An earlier phase found three silent failures in MechanicsDSL itself — lost parenthesisation in inlined denominators, a constrained-Lagrangian freeze, and an ARM backend emitting hardcoded dynamics regardless of input.

### Spin chain dynamics

Analytical modeling of energy transfer and information flow in a
boundary-driven nonequilibrium quantum spin chain.

## Publications

Parsons, N. (2025). *Strategic Grid Modernization for Enhanced Energy Security
and Industrial Competitiveness: A Multi-Pillar Framework for the United States.*
Applied Journal of Economics, Law and Governance, 1(2), 149–172.
[doi:10.57017/ajelg.v1.i2(2).03](https://doi.org/10.57017/ajelg.v1.i2(2).03)

## Contact

[ORCID](https://orcid.org/0009-0000-7224-6040) · parsons.m.noah@gmail.com
