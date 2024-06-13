---

## Context and Problem Statement

As stated in the MPSF [bylaws](https://github.com/materialsproject/foundation/blob/main/bylaws.md), represented codes are expected to adopt and enforce the [Contributor Code of Conduct](https://www.contributor-covenant.org/). This PR serves to formally implement that provision.

## Considered Options

### Reference in README and include a copy in the reposotiry

To put this into practice, MPSF codes will

1. Include a `CODE_OF_CONDUCT.md` in the root of the repository that contains the text of the Contributor Covenant, a copy of which is
   included in the Foundation repository as part of this PR. Note that language has been added to the Contributor Covenant to clarify
   that reports are reviewed by MP Staff members and that they are subject to LBNL's required reporting policies.
3. Include a contact email address (conduct@materialsproject.org) as the contact point in the above file.
4. Include a statement in the README file such as the following:
    > New contributors are welcome, please see our Code of Conduct (with link to the .md file).

## Decision Outcome

TBD

## Implementation Plan

{List changes to be made in affected codes, as applicable, or list "N/A"}

- [ ] `pymatgen`: Update README, add `CODE_OF_CONDUCT.md`.
- [ ] `atomate2`: Update README. Update `CODE_OF_CONDUCT.md` with this version.
- [ ] `emmet`: Update README. Update `CODE_OF_CONDUCT.md` with this version.
- [x] `crystal-toolkit`: Already implemented.
- [ ] `jobflow`: Update README. Update `CODE_OF_CONDUCT.md` with this version.
- [ ] `maggma`: Update README. Update `CODE_OF_CONDUCT.md` with this version.
