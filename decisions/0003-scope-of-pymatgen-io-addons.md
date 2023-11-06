# Clarify Scope of pymatgen addons

## Context and Problem Statement

Beginning in 2022, [pymatgen addon packages](https://pymatgen.org/addons) became available, allowing `io`, `analysis`, and `ext` code to be maintained and installed separately from pymatgen itself.

Recent development activity around improvement to existing IO and development of new IO has raised questions about the intended scope of `pymatgen-io-xxx` packages. Is the long-term goal for ALL IO to live in addon packages, or only newly-developed codes?

Specific recent cases that are relevant include
- [New LAMMPS IO work by @gbrunin](https://github.com/materialsproject/pymatgen/issues/2754)
- Updated VASP `InputSet` / `InputGenerator` in `atomate2`
- [WIP updates to Q-Chem IO by @rdguha1995](https://github.com/materialsproject/atomate2/pulls) for compatibility with `atomate2`
- A [related question](https://github.com/materialsproject/atomate2/issues/223) from external contributors concerning addon packages for `atomate2`


## Decision Drivers

- Developers of IO code must have highly specialized knowledge of that particular code. There are typically only a few who know the external package well enough to write and review robust IO
- pymatgen dependency bloat makes installation cumbersome, especially in space-constrained environments
- `atomate2` `Maker` classes expect IO classes to conform to the new Abstract IO interface in `pymatgen` (i.e, `InputSet` / `InputGenerator` paradigm). Hence, many legayc IO modules will need to be updated to work well with `atomate2`.
- `atomate2` is creating renwed interest among external users in developing new workflows, which are likely to involve IO for new codes. This increases the importance of clarifying the intended scope of pymatgen addon packages.

## Considered Options

### Option 1: Migrate all IO codes to dedicated addon packages

In this proposal, **all IO would be moved to dedicated addon packages**. The addon packages would presumably be maintained by the most active / invested developers that are experts in the respective codes. For example, @shyuep and/or @utf for VASP, @samblau for Q-Chem, etc.

- Good, because it will empower the most expert and invested developers to directly maintain their IO modules, without the need for a pymatgen maintainer as a "middle man"
- Good, because it reduces dependency bloat. A typical user will probably only need IO for 2-3 codes. This way they can only install what they need which is beneficial on, e.g., HPC systems with limited disk quotas
- Good, because it will reduce the number of unnecessary CI tests that are required on every PR. For example, a PR in the Q-Chem addon part of pymatgen really doesn't need to trigger unit tests of Lobster. Reducing CI tests will have positive impacts in terms of energy and climate emissions over the long-term
- Neutral, because it will require a user to install more packages in most cases (e.g. `pip install pymatgen pymatgen-io-vasp`)
- Bad, because it will require a lot of work to implement
- Bad, because it could cause some IO addon packages to fall out of date and stop working as pymatgen updates.
- Bad, because it could result in less stringent code quality control for IO codes

### Option 1a - same as above, but keep VASP IO in pymatgen because VASP is so central to MP and to provide a concrete example of how pymatgen IO is supposed to work

### Option 2: Use addon packages for all new codes AND for `atomate2` compatibility upgrades of existing IO

This option would place updated IO of ANY code into a dedicated addon package (e.g. `pymatgen-io-vasp`). Users that want to use `atomate2` would install the associated addon packages, which would supercede whatever IO is in `pymatgen`. Existing `atomate1` compatible IO in `pymatgen` could remain as-is.

- Good, because it preserves backwards compatibility of `pymatgen` IO with `atomate1`
- Bad, because it might cause duplication of effort or confusion among users (e.g., use the old VASP IO or the new VASP IO)?
- Bad, because it could result in less stringent code quality control for IO codes

### Option 3: Keep updating IO for existing codes in `pymatgen`, let future codes use addon packages

- Good, because it simplifies installation (`pip install pymatgen`)
- Bad, because it may confuse users that some codes are "built in" while others require a separate addon installation
- Bad, because it requires pymatgen maintainers to have knowledge of many codes
- Bad, because it may be difficult to maintain simultaneous `atomate1` and `atomate2` compatibility in IO classes (needs further research)

### Option 4: Per discussion on GitHub in May 2023

This option is a hybrid of option 1a and 3. In this option:

- IO for codes that are central to MP or to the work of pymatgen maintainers (especially VASP and LAMMPS) will stay in pymatgen.
- IO for other codes (such as Q-Chem) can either stay where they are or be moved at the maintainer's discrection.
- Concerns about installed size of the `git` repository can be addressed using `git sparse-checkout`
- Discussion / concerns about `atomate1` vs `atomate2` compatibility are deemed out of scope and will be addressed separately if needed.
- We should clarify the suggested license(s) for pymatgen addons in the documentation and by adding a template license to the addon repo

Assessment:
- Good, because it does not require significant re-work of existing code
- Good, because it makes it possible for individuals with expert knowledge of specific codes to maintain their own repos if desired (and potentially lessen the burden on pymatgen maintainers)
- Neutral, because it does not directly do anything to address dependency bloat or the volume of CI tests run on every PR
- Bad, because it may confuse users that some codes are "built in" while others require a separate addon installation (though this can be addressed via documentation updates)

## Decision Outcome

TBD 

## Implementation Plan

- [x] [pymatgen contributing page](https://pymatgen.org/contributing.html#direct-contributions-to-pymatgen-main-distribution) was updated to included instructions for `git sparse-checkout` (ALREADY DONE)
- [ ] Update [pymatgen developer installation page](https://pymatgen.org/installation.html#step-2-install-pymatgen-in-developmental-mode) to add `git sparse-checkout` instructions and remove reference to `git-lfs`
- [ ] Update the [pymatgen contributing page](https://pymatgen.org/contributing.html#writing-add-ons-for-pymatgen) with the outcome of this decision, to clarify how IO modules are handled.
- [ ] Update the [pymatgen-addon-template repo]([url](https://github.com/materialsproject/pymatgen-addon-template)) with a suggested pymatgen-compatible license (and clarify suggested licenses)

## More Information

https://pymatgen.org/addons

[atomate2 #223](https://github.com/materialsproject/atomate2/issues/223)

[pymatgen #2754](https://github.com/materialsproject/pymatgen/issues/2754)
