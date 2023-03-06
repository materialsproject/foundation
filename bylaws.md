# Bylaws of the Materials Project Software Foundation

Effective January 2023

## Preamble

This document is provided as a preliminary charter defining how the Materials Project Software Foundation ("the Foundation" or "MPSF") will operate. It should be viewed as a living document whose provisions will evolve over time.

These Bylaws may be modified and updated from time to time according to the same process used for Decision Records, detailed below.

## Purpose

The mission of the Materials Project Software Foundation is described in its [Mission Statement](decisions/0001-mission-statement.md). It is a coordinated effort by Materials Project staff and volunteer developers and does not constitute a nonprofit foundation in the legal sense.

## Organization

The Materials Project Software Foundation comprises a Steering Committee and various ad-hoc working groups or teams. Their purpose is to coordinate development activities among selected Materials Project codes ("Represented Codes") as enumerated below.

### Represented codes

 1. The Foundation seeks to coordinate development activities among Materials Project codes that 1) are public-facing in the sense that they are used by many users outside the Materials Project and 2) have a high degree of interdependence.
 2. Currently represented codes include `pymatgen`, `atomate2`, `emmet`, `jobflow`, `maggma`, and `crystal-toolkit`.
 3. Represented codes are expected to send at least one representative to each Steering Committee meeting, to adopt and enforce the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/), and to adhere in large part to the Foundation's decisions.
 4. Notwithstanding the previous bullet, MPSF decisions are not binding. Maintainers of the respective codes retain full autonomy to implement (or not) the recommendations of the MPSF as documented in Decision Records. The Decision Record process (detailed below) is intended to capture the reasoning behind adopting or not adopting a particular decision, including points of technical disagreement, for internal and external reference.

### Steering Committee

1. The Steering Committee shall comprise 5-10 members that actively maintain at least one of the represented codes. Here, "actively maintain" means that the members of the committee have to regularly be either committing code themselves or reviewing and merging pull requests from the community.
2. At least one additional Steering Committee member should be from outside the Materials Project collaboration to ensure external perspectives are heard. Here "outside" could mean working at another institution not formally a part of the Materials Project, or working in industry.
3. Steering Committee members will nominally serve for a term of 2 years.

### Meetings

1. The Steering Committee will meet every two months to conduct business.
2. Steering Committee meetings will also be open to community members that actively contribute to at least one of the represented codes and are invited by a Steering Committee member. The Steering Committee may specifically invite such members from time to time to seek additional input on a particular decision.
3. Meetings will be held virtually (or hybrid), and one meeting per year may be held in-person in conjunction with the annual MP Workshop.

### Officers and Duties

1. Each Steering Committee meeting shall have a Chairperson, a Notetaker, and a Repository Keeper
2. The Chairperson is responsible for establishing the agenda for the meeting, sending reminder emails containing the agenda preferably 1 week in advance of the meeting, and leading discussion during the meeting.
3. The Notetaker is responsible for recording minutes during the meeting.
4. The Repository Keeper is responsible for managing the Foundation GitHub Repository (see below)
5. The Chairperson shall rotate every 2 meetings (4 months), with a rotation schedule established roughly one year in advance. Each Steering Committee member is expected to serve as Chairperson once during their two year term, and the current Chairperson shall be responsible for determining the next member to add to the rotation.
6. The Notetaker and Repository Keeper may be assigned on a rotating, per-meeting basis or on a more permanent basis, with a term not to exceed two years for one person in one role.

## Decision Process

### GitHub Repository and Decision Records

1. The MPSF maintains a public GitHub repository at https://github.com/materialsproject/foundation/ that contains written records of its decisions and recommendations.
2. Decisions will be documented using the `MADR` or "Markdown Any Decision Record" format which captures 1) the Context and Problem Statement, 2) the options considered, and 3) the chosen outcome.
3. Decision records will be numbered sequentially according to their Pull Request number (see next section) for easy reference.

### Proposing Items for Discussion

1. The Steering Committee will discuss and document major architectural decisions and significant backward-incompatible changes, ideally prior to their implementation in released versions of any code.
2. Any Steering Committee member can propose an item for discussion by opening a pull request against the MPSF repository. Such pull requests should contain draft Decision Records that capture the Context and Problem statement and preferably enumerate some alternative options for how to proceed.
3. Pull Requests will be added to the Steering Committee meeting agenda by the Chairperson as time allows. Pull requests should be discussed approximately in the order they were opened, subject to the Chairperson's judgment.
4. Discussion Items should be communicated to the MPSF Steering Committee approximately 1 week before a meeting.
5. Prior to the meeting, MPSF members are encouraged to review the proposed PRs and use GitHub's discussion features and/or the MPSF Slack workspace to offer feedback and introduce additional alternatives.


### Making Decisions

1. During the meeting, the Chairperson will lead a discussion of each PR while the Notetaker captures significant points of agreement or disagreement and options considered.
2. The MPSF will make decisions guided by the principle of "Rough Consensus" as described by the [Internet Engineering Task Force](https://www.rfc-editor.org/rfc/rfc7282#page-7). Rough Consensus makes a distinction between members seeing a "fundamental flaw" with a proposed decision vs. thinking an alternative is "not the best choice", as described [here](https://async.twist.com/decision-making-flat-organization/). E.g., “I don’t believe Solution A is the best choice, because XYZ. I believe Solution B would be better, but I accept that Solution A can work too.” vs. “I believe Solution A is unacceptable because XYZ.”
3. The Chairperson will lead the discussion, trying to ensure that all alternatives and concerns are heard and debated within the group. When the Chairperson believes this has happened, they can call for a vote to adopt an alternative. 
4. If a member feels their concern has not been adequately heard, they may object to the vote. In this case, the member must explicitly re-state their concern and the Chairperson will extend the discussion to address that specific point. Members may only object to a vote one time per concern. In other words, if the same member wishes to object to a vote a second time, they must state a substantively different concern.
5. Each Steering Committee member gets a single vote, irrespective of how the code(s) they are most closely associated with. Members who are not present at the meeting may register their votes asynchronously via the Slack workspace prior to the subsequent meeting.
6. When a vote is taken and a majority has voted in favor, the PR will be updated before the next MPSF meeting by its author and/or the Repository Keeper to capture the decision outcome and major discussion points (including minority viewpoints / major objections as appropriate). At the beginning of the next meeting, the Chairperson will make a final call for new objections, and then the PR will be merged, signifying its adoption as an MPSF recommendation. Only objections that are new and substantially different from those discussed in the previous meeting(s) would be grounds for preventing adoption.
7. When a vote is taken and a majority does not vote in favor, the PR will be left open and revisited at the next meeting.
8. If a PR has been discussed a 2nd time (i.e. at multiple meetings) and not yet approved, this should be recorded in the GitHub discussion and the PR will be closed.
9. Decision Records are not set in stone. They may be superceded or deprecated by future decisions at the discretion of the Steering Committee
