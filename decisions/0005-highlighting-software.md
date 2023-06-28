# Highlighting MP-Adjacent Software

## Context and Problem Statement

There are several software packages that use or are built around the core Materials Project software stack. An incomplete list can be found in the Pymatgen docs [here](https://pymatgen.org/addons#external-tools), which includes the ones that rely on Pymatgen in particular.

The aim of this decision is to decide where and how MP-adjacent software will be highlighted with the main goals being:

1. Increasing visibility of MP-adjacent software
2. Preventing the development of redundant software
3. Advertising the impact of the Materials Project ecosystem

## Decision Drivers

- Should be somewhere "central" with high visibility
- Should be easy to update from potential developers
- Should have some set of criteria for inclusion/exclusion

## Considered Options

### Option 1: Materials Project Website

Codes that are part of the greater MP universe could be listed on the Materials Project website. This could be submitted via the `feedback` email or, better yet, with a clearly defined Google form that would request all the necessary information (e.g. GitHub repo, logo, description, etc.).

Pros:

- Good visibility
- Benefits both parties, MP and the code developers

Cons:

- Places a minor burden on the staff to update and maintain the list

### Option 2: Contributor Guide Gitbook

Codes that are part of the greater MP universe could be listed in the proposed contributor gitbook. This would be a natural place, thematically, for such content. The relevant section of the Gitbook could then be linked on the MP website.

Pros:

- Easy to update

Cons:

- May be slightly harder to stumble upon

## Related Discussion

A discussion was raised by @mkhorton about assigning credit _within_ a code, beyond simply putting a DOI in the docstring. A discussion was raised about using [duecredit](https://github.com/duecredit/duecredit), which is a lightweight decorator that can be put around functions that will automatically assemble a list of citable references for the user. It was agreed upon that this would be on an opt-in basis both for the code maintainer and the code contributor. @utf raised an equally important point about the need to ensure that the documentation reflects the citation information even when the decorator is applied.

### Decision Outcome

Option 2: Contributor Guide Gitbook was selected as the preferred option.

### Implementation Plan

- [ ] Come up with a list of criteria for inclusion/exclusion.
- [ ] Create a list of codes we should consider adding.
- [ ] Add the list to the handbook along with minimal information for each (e.g. hyperlink, logo, GitHub description).
- [ ] Link to the section somewhere prominent on the MP website.

## More Information

- [Pymatgen PR 3107](https://github.com/materialsproject/pymatgen/pull/3107)
