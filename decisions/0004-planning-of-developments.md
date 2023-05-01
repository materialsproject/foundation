# Planning and coordination of developments in Materials Project Software

## Context and Problem Statement

If developers would like to contribute an interface or workflow to the Materials Project software infrastructure, it is currently not possible to find out if other developers have already started with this development (except pull requests or issues have been made).
This could potentially lead to duplicated work. Could we encourage developers to at least raise an issue or similar before working on such an interface which is potentially of interest for many users and developers?

One example for this are the LAMMPS workflows where multiple teams were interested in their development and only found out about each other by chance: <https://github.com/materialsproject/atomate2/issues/173>

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* Collecting such planned developments could foster collaboration
* Collaboration could lead to faster availability of certain features
* It would avoid duplication of work
* It could strengthen the Materials Project software infrastructure and also attract new external developers and contributors
* Developers would need to disclose a part of their project early on
* We would need to encourage developers to communicate with us

## Considered Options

### Issues in Individual Software Packages

The following points are the summary of our discussion:

* Good because it is at least somehow documented
* Bad because developments might be in multiple packages and hard to discover
* Bad as it might distract from bugs or other relevant issues and add noise to the repo

### Usage of Github Discussions in Individual Software Packages

The following points are the summary of our discussion:

* Good because it is documented
* Good because it be easier to maintain
* Bad because maintainers might overlook these discussions
* Bad because maybe hard to discover

### Public MP Org Github Project Board

The following points are the summary of our discussion:

* Good because developers can see quickly and with once glance what developments are on-going
* Good because you can link developments in multiple software packages
* Bad because you need to know github project boards
* Bad because maybe hard to discover
* External users that are not members of MP cannot use it

### Forum Entries

* Good because it is easy to use
* Bad because the forum might be hard to navigate
* Bad because developer-oriented discussions might get lost among all the user support questions

### Multi-Step Solution Including Website, Readme.txt and Discussions (version of the 6th of March 2023)

The multi-step solution includes the following points:

* Create a New Developer Guide on the MP Docs page that describes, at a high level, how codes work together, what is expected of new PRs, and who to contact.
* Update to MP Website and Open Source Software Section with link to New Developer Guide
* Update to Readme.txt of individal repos with link to New Developer Guide
* Create a GitHub discussions board in MP Foundation repo where developers could discuss/announce new additions. Link to this from the New Devleoper Guide
The following points are the summary of our discussion:
* Good as it would help developers to get started
* Good as it would point developers of all codes to one guide and they would understand how the codes work together
* Good developers would only have one place to look
* Bad because MP Foundation repo might not attract many users

### Multi-Step Solution Including Website, Readme.txt and Discussions (version of the 1st of May 2023)

The multi-step solution includes the following points:

* Create a New Developer Guide on the MP Docs page that describes, at a high level, how codes work together, what is expected of new PRs, and who to contact.
* Update to MP Website and Open Source Software Section with link to New Developer Guide
* Update to Readme.txt of individal repos with link to New Developer Guide
* Optional:  Create a GitHub discussions board in MP Foundation repo where developers could discuss/announce new additions. Link to this from the New Devleoper Guide
* Optional: Have a "Dev Project" discussion board in every single MP repo with a pinned comment at the top linking the "MP Dev Guide"

## Decision Outcome

* Multi-step solution (version of the 6th of March, 2023) was approved by unanimous consent (6th of March, 2023)
* After feedback from additional members of the software foundation, an alternative version of the multi-step solution was proposed (version of the 1st of May 2023)
* Multi-step solution (version of the 1st of May, 2023) was approved by unanimous consent (1st of May 2023)
