---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 1
title: Updating the MP parameter sets
layout: home

# These are optional elements. Feel free to remove any of them.
# status: {proposed | rejected | accepted | deprecated | … | superseded by [ADR-0005](0005-example.md)}
# date: {YYYY-MM-DD when the decision was last updated}
# deciders: {list everyone involved in the decision}
# consulted: {list everyone whose opinions are sought (typically subject-matter experts); and with whom there is a two-way communication}
# informed: {list everyone who is kept up-to-date on progress; and with whom there is a one-way communication}
---
<!-- we need to disable MD025, because we use the different heading "ADR Template" in the homepage (see above) than it is foreseen in the template -->
<!-- markdownlint-disable-next-line MD025 -->
# Updating the MP parameter sets

## Context and Problem Statement

The last systematic audits of parameters used in the Materials Project workflows occurred in 2011 for PBE, and in 2020-2021 for r$^2$SCAN. Over those years, various parameters in those workflows have been updated as need arose.

This work aims to systematically update a few critical parameters used in the workflows that need updating: `ISMEAR`, `LREAL`,  `LMAXMIX`, `KSPACING`, and `POTCARs`.

[Link to relevant issue with early discussion.](https://github.com/materialsproject/foundation/issues/25).

This document is a summary of a longer document which includes, for each parameter recommendation, a background and motivation section which explains physically what a parameter controls. These sections can safely be skipped if one is already familiar with the parameter. The method and discussion sections present all required descriptions of how tests were conceived, executed, and interpreted.

At present, this [longer document](https://drive.google.com/file/d/1fUUx0wrrtMRcSss5yv3NiQuC7J5IiEKL/view?usp=sharing) is a living document. After a community discussion and foundation vote, it will be frozen with a specific set of recommended parameter changes.


<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* MP is a global leader in data reliability; periodically updating our computational parameters ensures consistent data quality.

## Considered Options

### Current data-driven recommendation

For INCAR settings:

-   `ALGO` = "NORMAL", as this is robust enough and "ALL" can be quite slow.

-   For relaxations in any solid, `ISMEAR`= 0 (Gaussian smearing) with
    smearing width (SIGMA) 0.05 eV

-   For statics in any solid, `ISMEAR`= -5 (unchanged from prior works)

-   LMAXMIX = 6 in all solids and for plain DFT without Hubbard $U$

-   LREAL = False always

-   Bringing the PBE workflow parameters (ENCUT, EDIFF, EDIFFG, etc.) in
    line with the r$^2$SCAN workflow

For KPOINTS updates: Use $\Gamma$-centered meshes with the following
formula for KSPACING, based on bandgap $$\begin{aligned}
    \mathrm{KSPACING} &= \frac{1}{2} \left\{ \Delta k_\text{min} + \Delta k_\text{max} + (\Delta k_\text{max} - \Delta k_\text{min})\frac{\delta}{[1 + \delta^c]^{1/c}} \right\}, \\
    \delta &= a(E_g - b), \\
    \Delta k_\text{min} &= 0.2, \\
    \Delta k_\text{max} &= 0.45, \\
    a &= 0.9,\\
    b &= 2.35,\\
    c &= 8. \\
\end{aligned}$$

For POTCAR updates:

-   The current actinide series of POTCARs used by MP is inconsistent
    with all-electron data and must be updated.

-   Some issues are also noted for Ba and Xe

-   Recommendations for new POTCARs are given in Ref. 1,
    which results in GW-derived pseudopotentials being recommended for
    Ba and Xe. We have also benchmarked these for higher accuracy, and
    present them in Table [1](#tab:potcar_changes){reference-type="ref"
    reference="tab:potcar_changes"}

::: {#tab:potcar_changes}
    Element   MP r$^2$SCAN POTCAR   New POTCAR   New POTCAR ENMAX (eV)
  --------- --------------------- ------------ -----------------------
         Ba                 Ba_sv     Ba_sv_GW                  267.02
         Dy                  Dy_3         Dy_h                 405.886
         Er                  Er_3         Er_h                 429.583
         Ho                  Ho_3         Ho_h                  415.91
         Nd                  Nd_3         Nd_h                 402.016
         Pm                  Pm_3         Pm_h                 404.406
         Pr                  Pr_3         Pr_h                 400.742
         Sm                  Sm_3         Sm_h                 405.382
         Tb                  Tb_3         Tb_h                 405.043
         Tm                  Tm_3         Tm_h                 419.812
         Xe                    Xe        Xe_GW                 179.547
         Yb                  Yb_3         Yb_h                 409.285

  :  Summary of recommended POTCAR changes. The POTCARs used in the
  r$^2$SCAN are listed in the second column for each element in the
  first column (from the left). The recommended POTCARs from Ref.
  1 are listed in the third column, and their minimum
  required plane-wave cutoff energies are listed in the rightmost column
  (ENMAX).
:::

For Hubbard $U$ updates:

-   PBE+$U$ is demonstrably worse for describing formation enthalpies

-   An attempt to determine optimal $U$'s for PBE (and later r$^2$SCAN)
    using experimental formation enthalpies for the whole $d$-block was
    unsuccessful

-   Fitting redox enthalpies may represent one path to expanding the
    $U$'s used by MP

We do not present data for PBE$+U$, as this may go into a separate
publication (this can be shared privately).

<sup> 1 </sup> E. Bosoni <i> et al. </i>, Nature Rev. Phys. <b> 6 </b>, 45 (2024). DOI: [10.1038/s42254-023-00655-3](https://doi.org/10.1038/s42254-023-00655-3)


### Alternatives

A few other alternatives are listed in the longer document.

## Decision Outcome

N/A right now.

<!-- This is an optional element. Feel free to remove. -->

## Implementation Plan

The updated parameters currently in [this fork of atomate2](https://github.com/esoteric-ephemera/atomate2/tree/updated_mp), but will be migrated to a pymatgen PR pending a change in atomate2 to move input sets there. (Hence the `~`)

- [~] `pymatgen`: ...
- [~] `atomate2`: ...
- [N/A] `emmet`: ...
- [N/A] `crystal-toolkit`: ...
- [N/A] `jobflow`: ...
- [N/A] `maggma`: ...

<!-- This is an optional element. Feel free to remove. -->
## More Information

See the longer document for extensive validation of these recommendations by a large set of VASP calculations.

This work was prepared with valuable suggestions and contributions by
(alphabetical): Matthew Horton, Patrick Huck, Anubhav Jain, Ryan
Kingsbury, Matthew Kuner, Jason Munro, Kristin Persson, Janosh
Riebesell, Andrew Rosen, and Ruoxi Yang.