# Noah Parsons

**Independent researcher in computational physics, systems software, scientific-software verification and open energy data · Newcastle, Wyoming**

[ORCID 0009-0000-7224-6040](https://orcid.org/0009-0000-7224-6040) · [parsons.m.noah@gmail.com](mailto:parsons.m.noah@gmail.com) · [noah-parsons.github.io](https://noah-parsons.github.io) · [Dynamics conformance results](https://noah-parsons.github.io/dynamics-conformance/) · [High Plains Open Energy Data](https://high-plains-open-energy-data.github.io) · [Examen Silentii](https://examen-silentii.github.io)

I build software for physics and systems, and I test whether scientific software and public data give correct answers. Most of my work starts from one question: when a program reports success, how do we know the result is right?

That question has led to:
- a compiler for classical mechanics (MechanicsDSL) and a desktop worksheet built on it;
- an x86-64 operating system written from scratch (NexusOS) and a book on how to build one;
- a study of four rigid-body dynamics engines against references that share no code with any of them, and a page that re-runs those checks on every new engine release;
- conformance checks of orbit propagators, numerical quadrature and Lambert solvers;
- audits of public energy data: the Western Interconnection queue, EIA-860, and the US wind and solar databases;
- computer proofs of new lower bounds in the covering-code tables;
- the restoration of a DBL accounting system in production since 1980;
- fixes and reports in Project Chrono, SciPy, Basilisk, FilterPy, hapsira, CFAST and Catalyst Cooperative's PUDL;
- an open journal for this kind of work; and
- an open-data project on Wyoming's energy system.

Everything below is stated as of 14 November 2026.

---

## Contents

- [Recent](#recent)
- [Research](#research)
- [Software](#software)
- [Contributions to other projects](#contributions-to-other-projects)
- [Peer review and editorial work](#peer-review-and-editorial-work)
- [Energy policy and public engagement](#energy-policy-and-public-engagement)
- [Publications](#publications)
- [Experience and recognition](#experience-and-recognition)

---

## Recent

**November 2026**
- Founded [High Plains Open Energy Data](https://high-plains-open-energy-data.github.io), with four checked outputs so far:
  - a Wyoming generator dataset that matches EIA-860 exactly;
  - a tracker of proposed and retiring generators;
  - a 25-year comparison of Wyoming's generation with its in-state retail sales;
  - an undergraduate lesson built on [PUDL](https://catalyst.coop/pudl/).
- Reported to Catalyst Cooperative that PUDL's `operational_status` labels cancelled (`CN`) and indefinitely postponed (`IP`) generators as "proposed". That is 1,018 generators and 123,106 MW for 2025, about 27% of everything PUDL calls proposed.
- Became an editor at pyOpenSci. My first submission as editor is [xarray-binfile](https://github.com/pyOpenSci/software-submission/issues/373).
- Opened Basilisk [#1678](https://github.com/AVSLab/basilisk/issues/1678) and [#1679](https://github.com/AVSLab/basilisk/pull/1679), documenting that the task rate is the largest step the adaptive RKF45 and RKF78 integrators can take. I revised #1679 at the lead maintainer's request. He has asked for a follow-up adding an accuracy comparison to the `scenarioVariableTimeStepIntegrators.py` example.
- Opened a BLS Consumer Price Index archiver for Catalyst Cooperative's PUDL archiver ([#1469](https://github.com/catalyst-cooperative/pudl-archiver/pull/1469)), plus three further pull requests ([#1470](https://github.com/catalyst-cooperative/pudl-archiver/pull/1470)–[#1472](https://github.com/catalyst-cooperative/pudl-archiver/pull/1472)).
- PacifiCorp's other interconnection queues ([#1443](https://github.com/catalyst-cooperative/pudl-archiver/pull/1443)) were approved after a sandbox archive run and moved by Catalyst to [#1466](https://github.com/catalyst-cooperative/pudl-archiver/pull/1466) for merging.
- Fixed per-vertex UV export in Project Chrono's Blender exporter ([#867](https://github.com/projectchrono/chrono/pull/867), for issue #865).
- Submitted the Western Interconnection withdrawal-date study to *The Electricity Journal*.
- Wrote to FERC's Office of Public Participation about how withdrawal dates are reported.
- Deposited two companion notes on covering codes on Zenodo.
- Published my first two open preprint reviews on PREreview.
- Posted my first review for the Journal of Open Source Software (pyvisco).
- Completed my pyOpenSci review of PyCFAST.
- Released MechanicsDSL 2.1.4, a code-generator correctness release, and MechanicsDSL Studio 1.1.0 to 1.2.0. Studio 1.2.0 adds symplectic integration for conservative systems.
- Wrote a guest article for Synergex, at their invitation, on restoring and migrating a legacy DBL accounting system to Synergy/DE v12.

**October 2026**
- My archiver for PacifiCorp's interconnection queue was merged into Catalyst Cooperative's PUDL archiver ([#1409](https://github.com/catalyst-cooperative/pudl-archiver/pull/1409), merged as [#1435](https://github.com/catalyst-cooperative/pudl-archiver/pull/1435)).
- FilterPy 2.0.0 was released with three of my fixes: NumPy 2 compatibility, building from source with current pip, and batch filtering with missing measurements.
- I reported a regression in SciPy's stiff ODE solver ([#26384](https://github.com/scipy/scipy/issues/26384)). It was traced to an indexing error in the Fortran-to-C translation of `vode` and fixed in [#26387](https://github.com/scipy/scipy/pull/26387).
- Project Chrono fixed three faults I reported ([#846](https://github.com/projectchrono/chrono/issues/846), [#847](https://github.com/projectchrono/chrono/issues/847), [#851](https://github.com/projectchrono/chrono/issues/851)) and merged my regression test for `DoAssembly` on coupled mechanisms ([#856](https://github.com/projectchrono/chrono/pull/856)) and its follow-up ([#863](https://github.com/projectchrono/chrono/pull/863)).
- Found silent failures in four of hapsira's Kepler solvers ([#24](https://github.com/pleiszenburg/hapsira/pull/24), [#25](https://github.com/pleiszenburg/hapsira/pull/25)) and in its Vallado Lambert solver ([#26](https://github.com/pleiszenburg/hapsira/issues/26)), and two in Basilisk's Lambert solver ([#1651](https://github.com/AVSLab/basilisk/issues/1651), [#1652](https://github.com/AVSLab/basilisk/issues/1652)). Basilisk fixed both in [#1653](https://github.com/AVSLab/basilisk/pull/1653) the next day.
- Checked EIA-860 plant by plant against the US Wind Turbine Database and the US Large-Scale Solar Photovoltaic Database. I reported the confirmed discrepancies to EIA and to the database team at Lawrence Berkeley National Laboratory.
- Proved three new lower bounds for mixed binary/ternary covering codes: K(2,5,1) ≥ 34, K(1,7,1) ≥ 45 and K(2,6,1) ≥ 59.
- Submitted *Cart-pole with a light cart* to the IFToMM multibody benchmark library.
- Founded [Examen Silentii](https://examen-silentii.github.io), a journal of software and data verification, and published its inaugural editorial.
- Posted my pyOpenSci review of Picht. Issues from my PyCFAST review were fixed upstream and led to a NIST CFAST issue ([#2553](https://github.com/firemodels/cfast/issues/2553)).
- Submitted a formal stakeholder comment letter on the Wyoming Electricity Transmission Study's draft grid inventory.
- Built an independent map of Wyoming's transmission network and sent it to the study's contractor.
- Released MechanicsDSL Studio 1.0.0, a desktop worksheet for Windows.
- Finished the migration of the DBL accounting system to Synergy/DE v12: it runs end to end on 64-bit Windows.
- Released DBL Data Converter 1.0.0.
- Raced ClusterJump against eight rival indexes on the four SOSD datasets.

**September 2026**
- Completed the dynamics-engine study, published its artefacts on Zenodo, and released the quadrature companion study.
- Published *Who Reports Withdrawal Dates in the Western Interconnection Queue, and Does It Matter?*.
- Began porting the DBL accounting system to Synergy/DE v12: 742 of its 775 source files compiled unmodified.
- Published the fusion-tree benchmark.

---

## Research

### 1. Verification of rigid-body dynamics engines

*Limits of Differential Testing: Three Rigid-Body Dynamics Engines Under Library-Independent Adjudication.* The manuscript is public on Zenodo; its journal venue is to be decided. Artefacts: [doi:10.5281/zenodo.22315172](https://doi.org/10.5281/zenodo.22315172) (about 130 files). Study code: [`stress_suite/`](https://github.com/MechanicsDSL/mechanicsdsl/tree/main/stress_suite).

**Question.** When a dynamics engine returns the wrong equations or the wrong motion, does it say so? And can differential testing, comparing engines with one another, catch the cases where it does not?

**Engines.**

| Engine | Version |
|---|---|
| MechanicsDSL | 2.1.3 (commit `a8dc2b2`) |
| `sympy.physics.mechanics` | 1.14.0 |
| Drake | 1.56.0 |
| Project Chrono (fourth engine, added later) | PyChrono 10.0.0 |

**Design.**
- **Frozen case matrix.** 55 cases across six stress axes, fixed before measurement:
  - degrees of freedom;
  - closed kinematic loops;
  - redundant constraints;
  - near-singular mass matrices;
  - mass ratios to about 10¹⁵;
  - symbolic nesting depth.

  Prospective extension is allowed. Dropping a case after seeing its result is not.
- **Library-independent referee.** The references are closed forms written in NumPy alone, sharing no library with any engine under test. The referee was corroborated against a classical result it was never fitted to: the small-oscillation frequencies of a hanging chain, from the zeros of J₀. Its relative error on the first three modes falls from 5.5%, 4.3% and 1.6% at N = 4 to 0.19% at N = 128, halving as N doubles.
- **Pinned integrator.** Every engine supplies only its right-hand side, and all are integrated by one SciPy DOP853 call (rtol 10⁻¹⁰, atol 10⁻¹²). The measurement therefore cannot rank engines by integration, by design.
- **Three mechanism families:**
  - pendulum chains;
  - a slider-crank, a closed loop whose effective inertia varies 10⁴ times over a revolution and nearly loses its mass matrix at both dead centres;
  - a cart-pole whose mass-matrix determinant collapses 10⁶ times twice per swing with a light cart.
- **Disclosure.** I maintain one of the engines measured. That is stated throughout, and fixes made to my own engine after the freeze are held out of the results.

**Results.**
- **Frozen baseline.** At v2.1.3: 44 pass, 0 silent, 1 error and 10 timeouts.
  - The error is an exactly singular mass matrix, correctly refused at compile time.
  - A re-run was bit-identical to the first.
  - Oracle coverage is reported by pathway, not pooled.
  - Two referees cover 40 of the 45 adjudicated cases between them.
- **Agreement.** Across 72 engine–case pairs in the slider-crank and cart-pole families there were no disagreements and no refusals. Worst residuals:
  - cart-pole at M/m = 10⁻⁶: MechanicsDSL 1.25 × 10⁻¹⁴, SymPy 0, Drake 1.96 × 10⁻¹⁶;
  - slider-crank: MechanicsDSL 6.9 × 10⁻¹⁵, SymPy 5.7 × 10⁻¹⁵.

  Probe-sampling robustness used 19,200 comparisons (5 seeds × 4 regimes × 64 states); the worst was 6.5 × 10⁻¹².
- **Reach measured the driving, not the engine.** An apparent difference in reach (5, 12 and 30 coordinates) disappeared on an equal compute budget: all three engines answer 80 coordinates. At 80 coordinates, Drake is about 3,600 times faster than SymPy and 5,750 times faster than MechanicsDSL. Driven well, SymPy is 1.6 to 2.0 times faster than MechanicsDSL.
- **A shared failure differential testing cannot see.** At the inverted equilibrium of a pendulum chain, every engine, and the independent reference, reports success while producing about 20 rad of motion that the exact solution does not have.
  - The cause is arithmetic, not a defect: sin π evaluates to 1.2 × 10⁻¹⁶ in binary64, and the unstable equilibrium amplifies it exponentially.
  - An arbitrary-precision sweep from 16 to 150 digits gives a measured slope of 0.735 s of delay per digit against a predicted 0.735. Precision buys delay, never immunity.
  - The failure replicates on the cart-pole.
- **The convention-mismatch diagnostic.** In a cross-engine comparison, an error of exactly 1.00 or exactly 2.00 on every case is a convention mismatch in the comparison, not a defect in an engine. Three instances were caught this way: the canonical (q, p) state ordering, Drake's relative joint angles, and a mirrored cart-pole offset. Validated against injected faults, the rule is sufficient but not necessary.
- **Upstream findings.**
  - Drake's constrained continuous-time path requires its own integrator (CENIC), which the maintainers confirmed on Drake's GitHub Discussions.
  - Pinocchio's maintainers explained, in their Discussions, how Baumgarte stabilisation enters LCABA's accelerations.
  - Chrono's acceleration-level `DoAssembly` omitted the quadratic-velocity term, giving an error of exactly ω²L. That led to fixes on Chrono's main branch (see [Contributions](#contributions-to-other-projects)).

**Technical reports.**
- TR-2026-01 *Reference Oracle*
- TR-2026-02 *Sympy Adapter*
- TR-2026-03 *Drake Adapter*
- TR-2026-04 *Week One Findings*
- TR-2026-05 *Three Families*
- TR-2026-06 *Driving the Engines*, which records the reach confound dissolving and three defects found in my own engine:
  - 97% of compile time went into one cosmetic `sympy.simplify` call;
  - a simplification timeout was inert on Windows;
  - CPython's recursion limit presented as a derivation failure. With it raised, the engine derives a 100-coordinate system at 1.3 × 10⁻¹² relative error.

**Chrono as a fourth engine.** [chrono-matrix-adjudication](https://github.com/Noah-Parsons/chrono-matrix-adjudication) adjudicates Chrono through its own system matrices: the mass matrix and constraint Jacobian from `WriteSystemMatrices`, with the saddle-point system solved in NumPy. The state is applied with `Setup()` and `Update()`, so Chrono does not move it. Sixteen probe states per case, at a relative tolerance of 10⁻⁸:

| Family | Cases | Worst acceleration error | Worst constraint-force error |
|---|---|---|---|
| Pendulum chain, N = 1–5 | 5 | 4.0 × 10⁻¹² | 1.3 × 10⁻¹² |
| Slider-crank, both dead centres, mass ratio to 10⁶ | 10 | 1.4 × 10⁻¹¹ (8.2 × 10⁻¹¹ at dead centre) | 4.7 × 10⁻⁹ |
| Cart-pole, mass ratio 10 to 10⁻⁶ | 5 | 3.2 × 10⁻¹³ | 4.3 × 10⁻¹³ |

The paragraph on Chrono was checked for accuracy by the Chrono team before it went into the manuscript.

### 2. Dynamics engine conformance page

[dynamics-conformance](https://github.com/Noah-Parsons/dynamics-conformance) · [live results](https://noah-parsons.github.io/dynamics-conformance/)

The study turned into a running service. Every day, a GitHub Actions workflow checks whether SymPy, MechanicsDSL, Drake or Project Chrono has published a new release.
- Each new release is installed on a clean runner and scored on 21 cases in five families: pendulum chains of 1 to 8 links; near-singular coupling ending in an exactly singular system; mass ratios to 10¹²; a light cart-pole; and a slider-crank through dead centre.
- Each case is probed at 8 to 18 states. The score is max |a − r| / max(|r|, 1) at a tolerance of 10⁻⁸.
- Verdicts are pass, silent, warned, error or timeout. *Silent*, a wrong answer with no warning, is the one that matters. For an exactly singular system, a refusal counts as a pass.
- Adapters translate conventions such as state ordering, relative joint angles and axis direction. They never correct an engine's answer.

### 3. A shared blind spot in numerical quadrature

[shared-blindspot](https://github.com/Noah-Parsons/shared-blindspot) · [doi:10.5281/zenodo.22557771](https://doi.org/10.5281/zenodo.22557771)

A pre-registered replication of the dynamics result in a second domain, with a different mechanism. A narrow Gaussian bump centred at x = 1/3 was integrated over [−1, 1] by five quadrature routines from three independent algorithm families:
- `scipy.integrate.quad` (QUADPACK);
- R's `integrate()` (QUADPACK);
- `mpmath.quad` (tanh–sinh);
- adaptive Simpson;
- fixed-grid Simpson.

Results:
- At width 10⁻⁶ the exact answer is 1.772454 × 10⁻⁶. Every routine returns 0.0 and reports success, and four of the five claim an error of exactly zero.
- At the five narrowest widths, all five return bit-identical values: the maximum pairwise spread is 0.000.
- Comparing implementations detects nothing; only the closed form does. Tightening tolerances (`limit=10000, epsabs=1e-16`) never finds the error.
- SciPy and R present as independent but agree in all 18 cells, because both descend from QUADPACK. Independence of authorship is not independence of algorithm.

### 4. Benchmark problem for the IFToMM multibody library

[light-cartpole-benchmark](https://github.com/Noah-Parsons/light-cartpole-benchmark)

*Cart-pole with a light cart.* A cart of mass 10⁻⁶ kg carries a 1 m massless pole with a 1 kg point mass, released from horizontal and simulated for 10 s.
- At each of the 11 vertical crossings the mass-matrix determinant falls 10⁶ times and |θ̇| peaks at 4,429 rad/s, with a full width at half maximum of 1.08 µs.
- All six SciPy ODE solvers report success at their default tolerances, with errors of 0.09 to 3.8 against an acceptance threshold of 10⁻⁶.
- **Reference solution.** The equations of motion were derived by hand and integrated with DOP853 at rtol 10⁻¹³. The solution was checked against an independent 30-digit quadrature with mpmath, which needs no time integration. The two agree to e = 9.1 × 10⁻¹², and the crossing times to 2 × 10⁻¹² s.

Francisco González (Universidade da Coruña) confirmed the problem was ready for the library. It was submitted in October 2026 and is awaiting the library's review.

### 5. Orbit propagator conformance

[orbit-propagator-conformance](https://github.com/Noah-Parsons/orbit-propagator-conformance)

**Libraries.** hapsira 0.18.0, Orekit 13.1.9.0 and Basilisk 2.12.0, checked against references computed independently in 40-digit arithmetic.

**Method.** Each library is evaluated with its own gravitational parameter, J2 and Earth radius. Propagation times avoid whole periods. Four reference cases:
- two-body motion at eccentricities from 0 to 0.95;
- J2 secular drift at four inclinations, including the critical inclination;
- hyperbolic and near-parabolic orbits;
- ten Lambert problems, plus a sweep of 300 random multi-revolution problems.

**Findings.**
- **hapsira's Mikkola and Pimienta solvers** are wrong beyond one revolution (17,700 km and 17,000 km after 10.71 periods at e = 0.3), and Mikkola returns `nan` for negative mean anomaly. Fixed in [#24](https://github.com/pleiszenburg/hapsira/pull/24): 85 of 360 test cases fail before the fix and none after.
- **hapsira's Danby solver** reduces the hyperbolic mean anomaly modulo 2π, giving errors up to 56 million km. Its Gooding solver stops iterating at |f| < 10⁻⁴ instead of the documented accuracy. Both are fixed in [#25](https://github.com/pleiszenburg/hapsira/pull/25).
- **hapsira's Vallado Lambert solver**: its `prograde` flag selects the short or long way round, not the direction of motion, giving 15 km/s errors when used as documented ([#26](https://github.com/pleiszenburg/hapsira/issues/26)).
- **Basilisk's `lambertSolver`, Gooding method**: three sign and term errors in the second starting value against Gooding's XLAMB. As a result, 124 of 297 multi-revolution problems return the same solution twice, both flagged valid, and in 55 of those neither solution is the known orbit. Confirmed by compiling Basilisk's own C++ unchanged and corrected ([#1651](https://github.com/AVSLab/basilisk/issues/1651)).
- **Basilisk's `lambertSolver`, both methods**: 15 km/s errors on a retrograde orbit, flagged valid ([#1652](https://github.com/AVSLab/basilisk/issues/1652)).

Both Basilisk faults were fixed in [#1653](https://github.com/AVSLab/basilisk/pull/1653). Basilisk's task rate and default RKF78 tolerance are recorded as configuration, not defects, following Professor Hanspeter Schaub's explanation of the design.

### 6. Coverage of withdrawal dates in the Western Interconnection queue

*Who Reports Withdrawal Dates in the Western Interconnection Queue, and Does It Matter?* [doi:10.5281/zenodo.22547678](https://doi.org/10.5281/zenodo.22547678) · [western-queue-reporting](https://github.com/Noah-Parsons/western-queue-reporting) · submitted to *The Electricity Journal*, November 2026.

**Question.** Berkeley Lab's *Queued Up* reports a median time from interconnection request to withdrawal for the non-ISO West. Do the records behind it represent the region?

**Findings.**
- **Coverage.** Only 636 of 5,277 western withdrawals (12.1%) carry a usable date, from six of 31 transmission providers.
  - BPA, Idaho Power, APS, NorthWestern, NV Energy and WAPA record none.
  - PacifiCorp has 1,627 withdrawals, 2.7 times the next-largest provider, but dates only 6.0% of them.
- **Composition.** The dated subset differs from the region in technology, cohort and service type (p < 10⁻¹⁰, Holm-corrected).
- **Effect on the median.** Standardising composition moves the median only from 1.83 to 1.77 years (95% CI −0.23 to 0.00), and +0.19 years under a truncation-matched window, so the direction of bias is not identified.
- **Validation.** The estimator was validated on four ISO regions (n = 11,281; induced bias 0.021 years).
- **Withdrawal risk.** A logistic model of 7,991 requests places 26% of the latent variation in withdrawal risk between providers.

The binding limitation is coverage, not composition. Berkeley Lab's lead author confirmed that no non-public withdrawal dates are used for the West and gave permission to cite the communication. The analysis is in R, seeded and reproducible.

### 7. EIA-860 data consistency audit

[eia-860-consistency-audit](https://github.com/Noah-Parsons/eia-860-consistency-audit)

A plant-by-plant check of EIA-860 2025 (1,368 operable onshore wind plants, 159,560 MW) against the US Wind Turbine Database v9.1 (76,165 turbines) and the US Large-Scale Solar Photovoltaic Database v4.0. Neighbouring plant codes within 10 km are grouped, and every disagreement is classified and checked by hand against developers' announcements, trade press and satellite imagery.

**EIA-860.**
- Cedro Hill (TX) and Hawkeye (IA) are repowerings counted twice. A national search found no others.
- Bearkat II (TX) is listed as cancelled but is a 162 MW operating plant.
- Palo Duro (TX) is overstated by about 32 MW.
- Six solar plants are recorded 26 to 118 km from their arrays, confirmed on imagery.

**USWTDB.**
- Turbines are missing from 13 otherwise complete projects (about 1,100 MW).
- There are plant-code and repowering errors, including Foote Creek I in Wyoming.

**Effect on totals.** The confirmed EIA-860 wind errors nearly cancel: about +52 MW nationally, or 0.03%. They matter for plant-level use, not for national or state totals.

Reported to EIA on 22 and 23 October 2026, and to the USWTDB team at Lawrence Berkeley National Laboratory on 22 October 2026.

### 8. Lower bounds for mixed covering codes

[covering-codes](https://github.com/Noah-Parsons/covering-codes)

K(t, b, R) is the minimum number of codewords in F₃ᵗ × F₂ᵇ covering every word within Hamming distance R. The reference values are Gerzson Kéri's tables, last updated in 2011.

| Entry | Kéri's table | New bound |
|---|---|---|
| K(2,5,1) | 32–36 | **≥ 34** |
| K(1,7,1) | 42–48 | **≥ 45** |
| K(2,6,1) | 57–64 | **≥ 59** |

**Method.** A codeword-distribution method in the style of Östergård and Blass (2001). Each bound is supported by:
- two independent solvers on every case, Gurobi 13 and CPLEX 22.2, with SCIP and HiGHS as further checks;
- the counting inequality recomputed from Hamming distances alone;
- a brute-force enumeration of the cell distributions;
- a model check (a real code is accepted, and the same code minus one word is rejected);
- controls on four known values.

K(2,5,1) is also certified by SAT (CaDiCaL, with LRAT proofs checked by lrat-trim). Certification of the other two is under way.

**Companion notes on Zenodo.**
- Any K(1,7,1) code with at most 47 words has a trivial automorphism group: [doi:10.5281/zenodo.24057238](https://doi.org/10.5281/zenodo.24057238).
- Rainbow domination numbers of hypercubes from the covering-code tables, γ_r3(Q_n) = K(1,n,1) and γ_r2(Q_n) = γ(Q_{n+1}): [doi:10.5281/zenodo.24057306](https://doi.org/10.5281/zenodo.24057306).

### 9. Galactic algorithms, measured: the fusion tree and ClusterJump

[fusion-tree-benchmark](https://github.com/Noah-Parsons/fusion-tree-benchmark) · [doi:10.5281/zenodo.22718523](https://doi.org/10.5281/zenodo.22718523)

**Does a correctly implemented fusion tree (Fredman and Willard, 1993) ever beat a B-tree on real hardware?** No.
- At 2²⁵ keys it takes 527–579 ns per query against 186 ns for a branch-free 8-key B-tree, and the absolute gap grows with size.
- It does beat binary search from 2²² keys, as its theory predicts. But an ordinary comparison-based B-tree beats binary search sooner and by more, so the win is the multiway node's, not the fusion tree's.
- Four independent lines of evidence locate the cause:
  - it executes 2.2 times the instructions (Intel VTune: 441 against 200 per query);
  - its node search is a long dependency chain;
  - with identical node size and cache-line traffic it is still slower;
  - its absolute deficit rises from 18 to 102 ns, so no crossover exists.
- The 1993 multiplication sketch packs fields only for K ≤ 4 in a 64-bit word. The implementations are viable only because of `PEXT` (BMI2).
- **Scale.** 48,600 timings across 10 structures, sizes 2⁸ to 2²⁵, two compilers and three sessions. More than 20 million correctness checks with zero failures.

**ClusterJump**, a two-level radix structure similar to a Hist-Tree, was tested under pre-registered plans:
- **S+ tree.** About 2.2 to 2.5 times the S+ tree's throughput on synthetic keys.
- **Real data.** 1.6 to 2.3 times the S+ tree's throughput on all four SOSD datasets (books, wiki, fb, osm).
- **Learned indexes.** 1.3 to 2.6 times faster than RadixSpline and 2.2 to 2.4 times faster than PGM-index in throughput; the learned indexes win on latency by 6 to 31%.
- **ClusterJumpD**, a dynamic variant, beats ALEX and the TLX B+ tree on five of six key sets.
- **Weakness.** Nested clusters defeat it. That is confirmed and reported, as is a bad worst case on fb.
- **Bugs found in ALEX** along the way are recorded.

### 10. Uncertainty in the neutron drip line

[neutron-drip-line](https://github.com/Noah-Parsons/neutron-drip-line)

**How sure can anyone be about where the neutron drip line is?** All eight phases are complete.
- A five-term mass formula fitted to 2,455 AME2020 nuclei.
- Garvey–Kelson relations.
- A blind test on nuclei measured after AME2003, repeated on all six AME editions since 1993.
- A comparison of seven published predictors.
- The drip line as a probability band.

Findings:
- The usual quoted uncertainty on the formula's constants understates their real movement between editions by 7 to 10 times. The constants drift the same way at every edition, accumulating to about −9σ from 1993 to 2020, driven by newly measured nuclei rather than revised ones.
- The parameter-free Garvey–Kelson relations of 1966 are competitive with modern global models: 0.35 MeV rms against WS4's 0.36.
- For a mid-mass element the honest band on the drip line is about 18 to 20 neutrons wide.

---

## Software

### MechanicsDSL

[github.com/MechanicsDSL](https://github.com/MechanicsDSL) · [doi:10.5281/zenodo.17771040](https://doi.org/10.5281/zenodo.17771040) · `pip install mechanicsdsl-core` · MIT licence

A domain-specific language and compiler for physical systems. You write a Lagrangian or Hamiltonian in LaTeX-inspired notation; the symbolic engine, built on SymPy, derives the equations of motion; and the compiler emits standalone code. The same system can become a Python script or libm-free C that cross-compiles for an ARM Cortex-M4. The path from textbook physics to firmware is a single step.

- **Twelve code-generation targets:** C++, Python, Rust, Julia, CUDA, Fortran, MATLAB, JavaScript, OpenMP, WebAssembly, Arduino and bare-metal ARM. A separate JAX runtime backend gives GPU execution and automatic differentiation. Modelica is an integration, not a generator.
- **Compile-verified embedded output.** Five representative systems build for Cortex-M4 with `arm-none-eabi-gcc -mthumb -mfpu=fpv4-sp-d16 -mfloat-abi=hard -Os -Wall -Wextra` with zero warnings: a 1-DOF oscillator, a pendulum, a 2-DOF coupled system, 3-DOF attitude, and a power in a denominator. A system that needs a libm function bare metal cannot provide gets an explicit `#error` instead of code that fails at link time.
- **Also included:** inverse problems (parameter estimation, sensitivity analysis, MCMC), a language server, Jupyter magic commands, a FastAPI server, a plugin architecture, and more than 40 examples from harmonic oscillators to SPH fluids, across 12 physics domains.
- **Size**, measured with cloc:
  - installed package: 26,615 lines of code in 151 files;
  - tests: 17,115 lines in 111 files;
  - whole repository: 74,083 lines.
- **Validation:**
  - 2,194 tests pass at 2.1.3;
  - the 55-case adversarial suite found zero silent failures at the frozen release;
  - agreement with the independent reference is within 5.5 × 10⁻¹⁵ relative on every case both could compute.
- **2.1.3, a correctness release.** The project's own adversarial work found and fixed faults in which the compiler produced wrong results while reporting success:
  - an integer power in a denominator lost its parentheses (`a/b**2` emitted as `a/b*b`);
  - constrained Lagrangian systems froze;
  - the Modelica generator emitted a failure marker as the equation of motion;
  - generated Rust never compiled;
  - the command line could reach only one of eleven targets;
  - a coordinate named `y` broke three generators;
  - the ARM generator ignored the system and emitted a hard-coded pendulum.

  Integration tolerance now scales with the mass matrix's condition number: at a condition number of 2 × 10⁸, energy drift fell from 3.7 × 10⁻² to 1.7 × 10⁻⁶. Stiffness detection now runs for every explicit method.
- **2.1.4** (November 2026) was a further code-generator correctness release.
- **Installs.** I audited them myself in BigQuery with a stated rule that excludes mirrors, CI and bot signatures: 373 organic installs from 947 raw, across 19 countries, between November 2025 and 10 November 2026.

| Package | Purpose |
|---|---|
| [mechanicsdsl](https://github.com/MechanicsDSL/mechanicsdsl) | Core compiler, on PyPI as `mechanicsdsl-core` |
| [mechanicsdsl-desktop](https://github.com/MechanicsDSL/mechanicsdsl-desktop) | MechanicsDSL Studio, the desktop worksheet (below) |
| [mechanicsdsl-embedded](https://github.com/MechanicsDSL/mechanicsdsl-embedded) | Deployment to Arduino, Raspberry Pi and ARM devices; C++ and `no_std` Rust for real-time closed-loop control. On PyPI as `mechanicsdsl-embedded` |
| [mechanicsdsl-ros2](https://github.com/MechanicsDSL/mechanicsdsl-ros2) | Compiles physical systems to ROS 2 packages: CMakeLists, message definitions, topics and launch files. On PyPI as `mechanicsdsl-ros2` |
| [mechanicsdsl-unity](https://github.com/MechanicsDSL/mechanicsdsl-unity) | Simulation components for Unity (C#) and Unreal Engine (C++). On PyPI as `mechanicsdsl-unity` |
| [mechanicsdsl-datasets](https://github.com/MechanicsDSL/mechanicsdsl-datasets) | Reference datasets for parameter estimation and inverse problems: synthetic data with ground truth, experimental trajectories, and paired MCMC posteriors. On PyPI as `mechanicsdsl-datasets` |
| [mechanicsdsl-notebooks](https://github.com/MechanicsDSL/mechanicsdsl-notebooks) | Notebooks across classical and quantum mechanics, electromagnetism, relativity, statistical mechanics, thermodynamics and fluid dynamics. On PyPI as `mechanicsdsl-notebooks` |

**MechanicsDSL Studio** ([releases](https://github.com/MechanicsDSL/mechanicsdsl-desktop/releases)) is a desktop worksheet for Windows and macOS (Apple silicon and Intel). Write a system's Lagrangian or Hamiltonian and the worksheet shows:
- the typeset equations of motion, copyable as LaTeX;
- an animation drawn without setup;
- live sliders for every parameter;
- coordinate, phase and energy-drift plots;
- generated code in all twelve languages.

Worksheets mix systems with notes and become self-contained printable handouts for a lesson. Computation runs in a separate process, so a long run can be stopped. Releases:
- 1.0.0 (31 October 2026);
- 1.1.0, which added handouts and macOS builds produced by GitHub Actions on every release;
- 1.1.1;
- 1.2.0, which added symplectic integration for conservative systems.

### NexusOS

[NexusOS](https://github.com/Noah-Parsons/NexusOS) · [doi:10.5281/zenodo.22313291](https://doi.org/10.5281/zenodo.22313291) · Book: [*Build Your Own OS*](https://leanpub.com/build-your-own-os)

An x86-64 operating system written from scratch in assembly and C, with no GRUB, Limine, gnu-efi, EDK2 or tutorial framework.

- **Two boot paths, one kernel.** A 512-byte legacy-BIOS MBR loader collects the E820 map, sets a VBE linear framebuffer and enters protected mode. A custom PE32+ UEFI application opens the Graphics Output Protocol, loads the kernel from the EFI System Partition and exits boot services. Both leave the same hand-off in low memory.
- **Kernel:**
  - long mode;
  - a full 256-entry IDT with a register-dump panic handler;
  - a remapped 8259A PIC and a 100 Hz PIT;
  - PS/2 keyboard and mouse;
  - an E820-driven bitmap frame allocator;
  - four-level paging with a 4 KiB map/unmap/translate API;
  - a first-fit, coalescing kernel heap above the identity map.
- **Concurrency.** A preemptive round-robin scheduler with sleep and an idle task, plus a mutex, counting semaphore and condition variable built on its blocked state with FIFO hand-off.
- **Storage.** An interrupt-driven PIO ATA driver and a read-only FAT12 filesystem.
- **Graphics.** A compositing window manager with an off-screen back buffer, z-ordered draggable windows, close and minimise buttons, a cursor overlay, a taskbar with an uptime clock, and the shell (`help`, `ticks`, `mem`, `tasks`, `prod`, `ls`, `cat`, `halt`) in a terminal window, mirrored to serial.
- **Real hardware.** Boots to the desktop by legacy BIOS on an ASUS H81M-C machine; the UEFI loader has run on a Braswell Chromebook.
- **Five-hour soak test on real hardware:**
  - 1,800,915 timer ticks and 2,984,689 context switches;
  - the mutex invariant held exactly (a + b − shared = 0), with both counters equal;
  - heap and frame use byte-identical across four samples, so no leak;
  - a bounded producer–consumer queue holding at 8 items.

  The soak found two defects: static heap sizing, and an uptime clock that wrapped every 100 minutes. The clock is fixed.
- **Next:** per-window keyboard focus, a syscall interface with ring-3 user mode and an ELF loader, a VFS with write support, and SMP, ACPI and APIC.

### Legacy software recovery: a DBL accounting system in production since 1980

[dibol-accounting-analysis](https://github.com/Noah-Parsons/dibol-accounting-analysis) · [doi:10.5281/zenodo.22554733](https://doi.org/10.5281/zenodo.22554733) · [dbl-data-to-sql-converter](https://github.com/Noah-Parsons/dbl-data-to-sql-converter)

A multi-module accounting system written in DBL by Custom Computer Services, a company that no longer exists. It has 161,973 lines in 519 programs across eight subsystems (AP, AR, BR, GL, PR, SC, SY and the shared XC library). It ran on at least six platforms: DEC RT-11 on a PDP-11, RSTS/E, VAX, Unix, Novell NetWare and MS-DOS.

- **Archived and audited.** The source went into a private repository with its operator's written permission, after a sweep for personal data and credentials. Live data, security files and the licensed vendor runtime are excluded.
- **Rebuilt on its original toolchain.** Rebuilt from that source on the original 1991 compiler (DBL 4.41) in a FreeDOS virtual machine. The rebuilt shared library is byte-identical to the one in production apart from embedded build timestamps, which rules out source drift.
- **Traced.** Its history was traced from 46 years of source: 604 of 990 source files carry conditional compilation, with UNIX, RT-11 and VAX maintained in parallel. A second class of conditionals switches optional modules, which indicates a configurable product. Authorship was reconstructed from comment headers across three development teams. The original developer was identified, starting from a licensee name embedded in the runtime.
- **Ported to Synergy/DE v12**, with Synergex's support:
  - 742 of 775 source files compile unmodified, 35 years after the toolchain they were written for;
  - six root causes account for the remainder;
  - with 57 lines of fixes the system builds and runs end to end on 64-bit Windows. Against a freshly created test company, it signs on, runs its menus, stores records and prints reports;
  - three programs (AUTOGL, PD121 and PG175) depend on source files that no longer exist and cannot be rebuilt.
- **Documented:**
  - `SCHEMA.md`, 339 record layouts and 2,425 fields with computed byte offsets;
  - `XREF.csv`, 2,567 program-to-record dependencies;
  - `PROVENANCE.md`;
  - a technical report.

  Documentation is CC BY 4.0 and the tools are MIT. The system's own source is not published, because its rights holders have not been identified.
- **DBL Data Converter 1.0.0.** A Windows application and Python package that converts the system's data files, both relative files and ISLOAD unloads of ISAM files, to Excel-compatible CSV and a single SQLite database, using all 339 record layouts.
  - It identifies each file's layout from its name and record length, and never guesses.
  - It decodes DBL's signed decimal fields exactly.
  - It opens sources read-only, runs offline on the Python standard library alone, and writes a conversion report.
  - Its tests round-trip synthetic records through every layout.
- **Guest article.** *Restoring and Migrating a Legacy DBL Accounting System to Synergy/DE v12*, written for Synergex at their invitation.

### High Plains Open Energy Data

[high-plains-open-energy-data.github.io](https://high-plains-open-energy-data.github.io) · [GitHub organisation](https://github.com/high-plains-open-energy-data)

An independent open-data project on the energy system of Wyoming and the High Plains, with three lines of work: checked datasets, a public monitor of what is proposed, built, delayed and retired, and teaching material on the same data. Every dataset is built from [PUDL](https://catalyst.coop/pudl/) and checked against EIA's own releases, with the checks published alongside it. Data is CC BY 4.0 and code is MIT.

- **Wyoming generators, 2025.** 132 existing generators totalling 12,735.6 MW, matching EIA-860 exactly.
- **Proposed and retiring generators.**
  - 17 active proposed generators, 7,206.6 MW: wind 4,060.6, solar 1,427, batteries 1,099, nuclear 500 and gas 120.
  - 3,550.5 MW of that is under construction.
  - Cancelled and indefinitely postponed projects are listed separately, not counted as proposed.
  - Planned retirements include Dave Johnston Unit 3 (229.5 MW, December 2027).
- **Generation and fuel mix, 2025.** 45.58 TWh, of which coal is 57.8% and wind 27.9%.
- **Where it goes, 2001–2025.** In 2025, 62% of Wyoming's net generation was not sold to Wyoming retail customers, against 71.1% in 2001.
- **Teaching.** An undergraduate lesson, *Wyoming Electricity with PUDL*, with a Jupyter notebook, a student worksheet and teacher notes.

### Other software

- [annotation-app](https://github.com/Noah-Parsons/annotation-app): a small annotation platform with role-based access, built with FastAPI, Next.js, TypeScript and Supabase.
- [noah-parsons.github.io](https://noah-parsons.github.io): my personal site, with essays and links to my work.

---

## Contributions to other projects

| Project | Contribution | Status |
|---|---|---|
| [Project Chrono](https://github.com/projectchrono/chrono) | Acceleration-level `DoAssembly` omitted the quadratic-velocity term, giving an error of exactly ω²L ([#846](https://github.com/projectchrono/chrono/issues/846)); missing Python bindings for `ChState`, `ChStateDelta`, the system descriptor and wrench members ([#847](https://github.com/projectchrono/chrono/issues/847)); a fault in `DoFrameKinematics` ([#851](https://github.com/projectchrono/chrono/issues/851)) | Fixed on main (#846 in [#852](https://github.com/projectchrono/chrono/pull/852)). `DoAssembly` now also returns a new `ACCELERATION_INACCURATE` flag, with new documentation on solver choice |
| Project Chrono | Regression test of acceleration-level `DoAssembly` on coupled mechanisms: pendulum chains of N = 2, 3 and 5, a cart-pole, and a slider-crank through both dead centres. It covers three solvers and checks that default PSOR returns the new flag in near-degenerate cases ([#856](https://github.com/projectchrono/chrono/pull/856)); follow-up for a sixth near-degenerate configuration ([#863](https://github.com/projectchrono/chrono/pull/863)) | Merged |
| Project Chrono | Discussion of NSC contacts during assembly ([#850](https://github.com/projectchrono/chrono/issues/850)) | Commented |
| Project Chrono | Per-vertex UV export in the Blender exporter (issue #865, [#867](https://github.com/projectchrono/chrono/pull/867)) | In review |
| [Basilisk](https://github.com/AVSLab/basilisk) | Lambert-solver faults found in the orbit-propagator conformance check: duplicate multi-revolution solutions with the Gooding method ([#1651](https://github.com/AVSLab/basilisk/issues/1651)) and wrong retrograde solutions flagged valid ([#1652](https://github.com/AVSLab/basilisk/issues/1652)) | Fixed in [#1653](https://github.com/AVSLab/basilisk/pull/1653) |
| Basilisk | Documentation of the adaptive integrators' step size and tolerances ([#1678](https://github.com/AVSLab/basilisk/issues/1678), [#1679](https://github.com/AVSLab/basilisk/pull/1679)); an accuracy comparison for `scenarioVariableTimeStepIntegrators.py`, requested by the maintainer | In review; the follow-up is ready to open after #1679 |
| [FilterPy](https://github.com/rlabbe/filterpy) | NumPy 2 compatibility, building from source with current pip, and `batch_filter` with missing measurements; a least-squares residual fix | Three merged and released in 2.0.0; one open. Listed as a contributor |
| [hapsira](https://github.com/pleiszenburg/hapsira) | Mikkola and Pimienta Kepler solvers wrong beyond one revolution ([#24](https://github.com/pleiszenburg/hapsira/pull/24)); Danby wrong on hyperbolic orbits and Gooding stopping early ([#25](https://github.com/pleiszenburg/hapsira/pull/25)); Vallado's `prograde` flag ([#26](https://github.com/pleiszenburg/hapsira/issues/26)) | Open |
| [SciPy](https://github.com/scipy/scipy) | Stiff-solver regression in `integrate.ode` (`vode`, BDF) since 1.17.0, with "excess work done" on stiff problems ([#26384](https://github.com/scipy/scipy/issues/26384)) | Fixed in [#26387](https://github.com/scipy/scipy/pull/26387) |
| [CFAST](https://github.com/firemodels/cfast) (NIST) | Input-guide limits that disagree with the source, found in my PyCFAST review ([#2553](https://github.com/firemodels/cfast/issues/2553)) | Accepted; code and guides to be made consistent |
| [PyCFAST](https://github.com/bewygs/pycfast) | Issues found in review ([#231](https://github.com/bewygs/pycfast/issues/231), [#232](https://github.com/bewygs/pycfast/issues/232)) | Fixed in [#236](https://github.com/bewygs/pycfast/pull/236), [#237](https://github.com/bewygs/pycfast/pull/237) |
| [Picht](https://github.com/rolypolytoy/picht) | Issues found in review:<br>• Windows installation conflict ([#7](https://github.com/rolypolytoy/picht/issues/7))<br>• Getting Started example that does not run on 2.2.0 ([#8](https://github.com/rolypolytoy/picht/issues/8))<br>• tests that check structure but not physics ([#9](https://github.com/rolypolytoy/picht/issues/9))<br>• demo script inside the package ([#10](https://github.com/rolypolytoy/picht/issues/10))<br>• inconsistent packaging metadata ([#11](https://github.com/rolypolytoy/picht/issues/11))<br>• untagged releases ([#12](https://github.com/rolypolytoy/picht/issues/12))<br>• physics and documentation findings ([#13](https://github.com/rolypolytoy/picht/issues/13)–[#17](https://github.com/rolypolytoy/picht/issues/17)): Neumann boundary conditions, a planar rather than axisymmetric solver, the paraxial magnetic force, the version string, and an outdated CONTRIBUTING.md | Reported |
| [pyvisco](https://github.com/NatLabRockies/pyvisco) | From my JOSS review: verification assertions (#16), pandas deprecations (#17), missing software citations (#18), and the README's statement of need (#19) | Reported |
| [PUDL archiver](https://github.com/catalyst-cooperative/pudl-archiver) (Catalyst Cooperative) | Archiver for PacifiCorp's OASIS interconnection queue. Queue pages are discovered from the OASIS menu and fetched with Playwright ([#1409](https://github.com/catalyst-cooperative/pudl-archiver/pull/1409), merged as [#1435](https://github.com/catalyst-cooperative/pudl-archiver/pull/1435)) | Merged |
| PUDL archiver | PacifiCorp's other queues ([#1443](https://github.com/catalyst-cooperative/pudl-archiver/pull/1443), moved to [#1466](https://github.com/catalyst-cooperative/pudl-archiver/pull/1466)) | Approved; being merged |
| PUDL archiver | BLS Consumer Price Index archiver ([#1469](https://github.com/catalyst-cooperative/pudl-archiver/pull/1469)); unit tests using the fixture data package, FERC 2 browser clean-up, a continuity-check pandas fix and removal of unused `rate_limit_tasks` ([#1436](https://github.com/catalyst-cooperative/pudl-archiver/pull/1436)–[#1439](https://github.com/catalyst-cooperative/pudl-archiver/pull/1439)); further fixes ([#1470](https://github.com/catalyst-cooperative/pudl-archiver/pull/1470)–[#1472](https://github.com/catalyst-cooperative/pudl-archiver/pull/1472)); the missing `nrelcambium2024` DOI (issue [#1440](https://github.com/catalyst-cooperative/pudl-archiver/issues/1440)); an `epadcejp` metadata entry (issue [#1441](https://github.com/catalyst-cooperative/pudl-archiver/issues/1441)); triage of open issues | In review |
| [PUDL](https://github.com/catalyst-cooperative/pudl) (Catalyst Cooperative) | `operational_status` groups cancelled and indefinitely postponed generators with proposed ones: 1,018 generators and 123,106 MW for 2025 | Reported |
| [GridSFM](https://github.com/microsoft/GridSFM) (Microsoft Research) | Check of the open Wyoming, Colorado and Montana grid models against EIA-860 and the state grid inventory | Reported |
| EIA-860 (US Energy Information Administration) | Repowering double counts, a cancelled plant in operation, capacity and location errors (see [Research §7](#7-eia-860-data-consistency-audit)) | Reported to EIA |
| US Wind Turbine Database (USGS and LBNL) | Missing turbines, plant-code assignments and repowering records | Reported to LBNL |

I also took part in maintainers' public discussions on Drake (CENIC and constraints in continuous-time plants) and Pinocchio (constrained accelerations from LCABA), and reviewed pull requests on Catalyst's PUDL archiver.

---

## Peer review and editorial work

- **Founding editor, [Examen Silentii](https://examen-silentii.github.io)** (ExSil), a journal of software and data verification founded on 10 October 2026.
  - It publishes independent examinations of scientific software and public research data: tests against an independent reference, whether the tool signals its errors, and how maintainers responded.
  - Submissions come through GitHub issue forms with open review, and articles are deposited in a Zenodo community.
  - Its AI policy rests on disclosure, with reviewers re-running results.
  - The inaugural editorial, reviewed beforehand by Dan Negrut (UW–Madison, Project Chrono), is at [doi:10.5281/zenodo.23290573](https://doi.org/10.5281/zenodo.23290573).
- **Founder, [High Plains Open Energy Data](https://high-plains-open-energy-data.github.io).**
- **Editor, pyOpenSci** (from November 2026): [xarray-binfile](https://github.com/pyOpenSci/software-submission/issues/373), my first submission as editor.
- **Reviewer, pyOpenSci:**
  - Picht ([#242](https://github.com/pyOpenSci/software-submission/issues/242)), an electron and ion optics simulator, reviewed on Windows and Linux with eleven issues filed;
  - PyCFAST ([#318](https://github.com/pyOpenSci/software-submission/issues/318)), a Python interface to NIST's CFAST fire model.
- **Reviewer, Journal of Open Source Software:** pyvisco ([openjournals/joss-reviews#11504](https://github.com/openjournals/joss-reviews/issues/11504)), a library for identifying Prony-series parameters of linear viscoelastic materials.
- **PREreview, open preprint review:**
  - Heidari, *The U.S. Interconnection Queue System: Cascading Vulnerability Analysis and a Resilience Engineering Framework* ([doi:10.5281/zenodo.24095185](https://doi.org/10.5281/zenodo.24095185));
  - a second review, of a preprint on generative AI in K–12 education.
- **Member**, US Research Software Engineer Association (US-RSE).

---

## Energy policy and public engagement

- **Stakeholder, Wyoming Electricity Transmission Study** (Wyoming Energy Authority, under SF0102 of 2026).
  - I take part in its stakeholder workshops.
  - I submitted a formal comment letter on the study's draft Task 2 grid inventory to its contractor, Energy Strategies, in October 2026.
- **Independent map of Wyoming's transmission network.** It covers lines at 69 kV and above and is built from OpenStreetMap and Census data as a cross-check of the study's draft inventory. I sent it to Energy Strategies with a supplementary workbook covering substation locations, in-service dates and a PacifiCorp queue check.
- **Introduced PUDL to the study team** as a volunteer contributor to Catalyst Cooperative.
- **Federal Energy Regulatory Commission, Office of Public Participation.** A letter on the 12.1% coverage of western withdrawal dates, asking the proper route to propose consistent reporting (November 2026).
- **Federation of American Scientists, Day One Project.** A submitted idea on making federally funded research software verified by default.
- **Correspondence and commentary submitted:**
  - to *Nature*, on research-software verification;
  - to WyoFile's opinion pages, on the transmission provisions of Senate permitting bill S. 5653 and gaps in western withdrawal-date reporting.
- **Constituent letters** to Wyoming's senators on the transmission provisions of S. 5653, taking no position for or against.

---

## Publications

**Peer-reviewed**
- Parsons, N. (2025). Strategic grid modernization for enhanced energy security and industrial competitiveness: A multi-pillar framework for the United States. *Applied Journal of Economics, Law and Governance*, 1(2), 149–172. [doi:10.57017/ajelg.v1.i2(2).03](https://doi.org/10.57017/ajelg.v1.i2(2).03)

**Editorial**
- Parsons, N. (2026). Silent failures in scientific software: On the founding of Examen Silentii. *Examen Silentii*, 1. [doi:10.5281/zenodo.23290573](https://doi.org/10.5281/zenodo.23290573)

**Book**
- Parsons, N. *Build Your Own OS*. Leanpub. [leanpub.com/build-your-own-os](https://leanpub.com/build-your-own-os)

**Under review**
- Parsons, N. Who reports withdrawal dates in the Western Interconnection queue, and does it matter? Submitted to *The Electricity Journal*, November 2026.

**Preprints and archived studies**
- Parsons, N. (2026). Who reports withdrawal dates in the Western Interconnection queue, and does it matter? Working paper. [doi:10.5281/zenodo.22547678](https://doi.org/10.5281/zenodo.22547678)
- Parsons, N. (2026). *Limits of Differential Testing: Three Rigid-Body Dynamics Engines Under Library-Independent Adjudication*. Manuscript and artefacts. [doi:10.5281/zenodo.22315172](https://doi.org/10.5281/zenodo.22315172)
- Parsons, N. (2026). A shared blind spot in numerical quadrature. [doi:10.5281/zenodo.22557771](https://doi.org/10.5281/zenodo.22557771)
- Parsons, N. (2026). Fusion tree: galactic algorithms, measured. [doi:10.5281/zenodo.22718523](https://doi.org/10.5281/zenodo.22718523)
- Parsons, N. (2026). Analysis of a legacy DBL accounting system (1980–2026). [doi:10.5281/zenodo.22554733](https://doi.org/10.5281/zenodo.22554733)
- Parsons, N. (2026). Note on the covering code K(1,7,1): codes of at most 47 words have trivial automorphism group. [doi:10.5281/zenodo.24057238](https://doi.org/10.5281/zenodo.24057238)
- Parsons, N. (2026). Rainbow domination numbers of hypercubes from covering-code tables. [doi:10.5281/zenodo.24057306](https://doi.org/10.5281/zenodo.24057306)

**Software archives**
- Parsons, N. MechanicsDSL: a domain-specific language and compiler for physical systems. [doi:10.5281/zenodo.17771040](https://doi.org/10.5281/zenodo.17771040)
- Parsons, N. NexusOS. [doi:10.5281/zenodo.22313291](https://doi.org/10.5281/zenodo.22313291)

**Reviews**
- PREreview of Heidari, *The U.S. Interconnection Queue System* (2026). [doi:10.5281/zenodo.24095185](https://doi.org/10.5281/zenodo.24095185)

**Essays**
- Parsons, N. (2026). *Abstracted Atrocities: How Burgess and Klimov Filtered Violence in Opposite Directions*. [noah-parsons.github.io](https://noah-parsons.github.io) (CC BY 4.0)

---

## Experience and recognition

- **Director of Civic Innovation** (volunteer), American Forge Institute, August 2025 to February 2026. I led the institute's civic-innovation work and wrote on medicine, energy and the workforce. The organisation has since dissolved.
- **Research proposal with Dr. Priya Bhardwaj** (WashU Medicine), in progress, drafted to NIH grant standards. It applies MechanicsDSL to orthopaedic biomechanics.
- **Awards** at the High Plains Regional Science and Engineering Fair, from sponsors including Citadel Securities, the Office of Naval Research and the Air Force Research Laboratory.
