---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 1
title: Template
layout: home
# These are optional elements. Feel free to remove any of them.
# status: {proposed | rejected | accepted | deprecated | … | superseded by [ADR-0005](0005-example.md)}
status: proposed
# date: {YYYY-MM-DD when the decision was last updated}
# deciders: {list everyone involved in the decision}
consulted: @utf, @jmmshn
# informed: {list everyone who is kept up-to-date on progress; and with whom there is a one-way communication}
---
<!-- we need to disable MD025, because we use the different heading "ADR Template" in the homepage (see above) than it is foreseen in the template -->
<!-- markdownlint-disable-next-line MD025 -->
# VASP atomate2 settings

## Context and Problem Statement

*Note* This mostly affects specific settings in `atomate2` but will be noted here for greater awareness by core developers.

Current default VASP calculation settings for `atomate2` causes various issues
leading to calculation failure.  Most of these are related using newer VASP settings.

Specifically, the following issues are observed:

1. Using the `KSPACING` setting with sometimes causes the following error message for many calculations:

```
|-----------------------------------------------------------------------------|
|                     _     ____    _    _    _____     _                     |
|                    | |   |  _ \  | |  | |  / ____|   | |                    |
|                    | |   | |_) | | |  | | | |  __    | |                    |
|                    |_|   |  _ <  | |  | | | | |_ |   |_|                    |
|                     _    | |_) | | |__| | | |__| |    _                     |
|                    (_)   |____/   \____/   \_____|   (_)                    |
|                                                                             |
|     internal error in: rot.F  at line: 793                                  |
|                                                                             |
|     EDWAV: internal error, the gradient is not orthogonal 1 1 -1.817e-3     |
|                                                                             |
|     If you are not a developer, you should not encounter this problem.      |
|     Please submit a bug report.                                             |
|                                                                             |
|-----------------------------------------------------------------------------|
```

2. HSE calculations with `ALGO = Normal` errors out after ~10 electronic steps.
This is seems to happen more with smaller simulation cells with more K-points.

3. `LREAL = FALSE` is the recommended setting for smaller simulation cells.
While `LREAL = Auto` is recommended for larger simulation cells.  The idea is
that `LREAL = Auto` is less accurate, but faster but it's not clear to what extent.

The fortran code VASP uses to raise the typical LREAL warning is below:
This has been added to `atomate2` but not turned on by default.

```fortran
!-----------------------------------------------------------------------
!  set default value for LREAL if not given in INCAR
!-----------------------------------------------------------------------
      LREALT=P(1)%LREAL
      DO NT=2,NTYP
         LREALT=LREALT.AND.P(NT)%LREAL
      ENDDO
      IF (LREALD) INFO%LREAL=.FALSE.
!---- 'very large' cell and no real-space-projection scheme ???
      IF ((.NOT.INFO%LREAL).AND.(NIONS>16)) THEN
         IF (LREALT) THEN
            CALL vtutor%write(isAdvice, NoRealSpaceAndYouCould)
         ELSE
            CALL vtutor%write(isAdvice, NoRealSpaceAndYouShould)
         ENDIF
      ENDIF
!---- 'very small' cell and still real-space projection scheme ???
      IF (INFO%LREAL.AND.(NIONS<=8)) THEN
         CALL vtutor%write(isAdvice, RealSpaceNoMoreRecommended)
      ENDIF
!
```

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* HSE calculations on smaller simulation are breaking pretty often (> 50% of the time).
The cause is mostly due to the issues above.

## Considered Options

* `KSPACING` should be removed from the default `atomate2` settings.
* `ALGO = All` should be used as the default ALGO for HSE calculations.
* `LREAL` should be set with VASP internal recommendation by default.

## Decision Outcome

Chosen option: "{title of option 1}", because
{justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

<!-- This is an optional element. Feel free to remove. -->
### Consequences

* GOOD: Should result in more finished calculation with `atomate2`.
* BAD: the calculations will be a little slower, `KSPACING` usually allows for fewer K-points and `ALGO = All` is slower than `ALGO = Normal`.

<!-- This is an optional element. Feel free to remove. -->
## Validation

Since all these settings are speed/accuracy tradeoff settings in VASP, results should not be affected in a meaningful way.


