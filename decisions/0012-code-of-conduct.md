---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 1
title: Template
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
# Adopt Contributor Code of Conduct

## Context and Problem Statement

As stated in the MPSF [bylaws](https://github.com/materialsproject/foundation/blob/main/bylaws.md), represented codes are expected to adopt and enforce the [Contributor Code of Conduct](https://www.contributor-covenant.org/). This PR serves to formally implement that provision.

## Considered Options

### Reference in README and include a copy in the reposotiry

To put this into practice, MPSF codes will

1. Include a `CODE_OF_CONDUCT.md` in the root of the repository that contains the text of the Contributor Covenant. See examples [here](https://github.com/materialsproject/maggma/blob/main/CODE_OF_CONDUCT.md) and [here](https://github.com/materialsproject/atomate2/blob/main/CODE_OF_CONDUCT.md)
2. Include a contact email address (conduct@materialsproject.org) as the contact point in the above file.
3. Include a statement in the README file such as the following:
    > New contributors are welcome, please see our Code of Conduct (with link to the .md file).

## Decision Outcome

TBD

## Implementation Plan

{List changes to be made in affected codes, as applicable, or list "N/A"}

- [ ] `pymatgen`: Update README, add `CODE_OF_CONDUCT.md`.
- [ ] `atomate2`: Update README. , add email to `CODE_OF_CONDUCT.md`.
- [ ] `emmet`: Update README. (`CODE_OF_CONDUCT.md` already present)
- [x] `crystal-toolkit`: Already implemented.
- [ ] `jobflow`: Update README, add email to `CODE_OF_CONDUCT.md`.
- [ ] `maggma`: Update README. (`CODE_OF_CONDUCT.md` already present)
