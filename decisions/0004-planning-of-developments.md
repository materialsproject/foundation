# Planning and coordination of developments in Materials Project Software

## Context and Problem Statement

If developers would like to contribute an interface or workflow to the Materials Project software infrastructure, it is currently not possible to find out if other developers have already started with this development (except pull requests or issues have been made). 
This could potentially lead to duplicated work. Could we encourage developers to at least raise an issue or similar before working on such an interface which is potentially of interest for many users and developers?

One example for this are the LAMMPS workflows where multiple teams were interested in their development and only found out about each other by chance: https://github.com/materialsproject/atomate2/issues/173


<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Collecting such planned developments could foster collaboration 
* Collaboration could lead to faster availability of certain features
* It would avoid duplication of work
* It could strengthen the Materials Project software infrastructure and also attract new external developers and contributors
* Developers would need to disclose a part of their project early on
* We would need to encourage developers to communicate with us

## Considered Options
**Issues in individual software packages**
 * Good because it is at least somehow documented
 * Bad because developments might be in multiple packages and hard to discover
 * Bad as it might distract from bugs or other relevant issues and add noise to the repo

**Discussoins in individual software packages**
 * Good because it is documented
 * Good because it be easier to maintain
 * Bad because maintainers might overlook these discussions

**Public MP org github project board**
 * Good because developers can see quickly and with once glance what developments are on-going
 * Good because you can link developments in multiple software packages
 * Bad because you need to know github project boards
 * Bad because maybe hard to discover
 * Not clear so far if external users not members of MP can use this
 
**Forum entries**
 * Good because it is easy to use
 * Bad because the forum might be hard to navigate 



## Decision Outcome

Chosen option: "{title of option 1}", because
{justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

<!-- This is an optional element. Feel free to remove. -->
### Consequences



* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}
* … <!-- numbers of consequences can vary -->

<!-- This is an optional element. Feel free to remove. -->
## Validation

{describe how the implementation of/compliance with the ADR is validated. E.g., by a review or an ArchUnit test}

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### {title of option 1}

<!-- This is an optional element. Feel free to remove. -->
{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
<!-- use "neutral" if the given argument weights neither for good nor bad -->
* Neutral, because {argument c}
* Bad, because {argument d}
* … <!-- numbers of pros and cons can vary -->

### {title of other option}

{example | description | pointer to more information | …}

* Good, because {argument a}
* Good, because {argument b}
* Neutral, because {argument c}
* Bad, because {argument d}
* …

<!-- This is an optional element. Feel free to remove. -->
## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or
 document the team agreement on the decision and/or
 define when this decision when and how the decision should be realized and if/when it should be re-visited and/or
 how the decision is validated.
 Links to other decisions and resources might here appear as well.}
