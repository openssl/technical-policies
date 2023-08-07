# Time-based Release Policy
This policy outlines the systematic process followed for the time-based release
of OpenSSL software library. The approach aims to deliver regular, predictable
updates and innovations to users while maintaining optimal workflow and
efficient resource management within the OpenSSL organisation.

This document covers the release schedule and the various phases that comprise
our release cycle: planning, release definition, development, and release stages
including alpha, beta, and final release. It also outlines the support lifecycle
following each release.

The focus of this policy is on adhering to the timeline of releases, rather than
on ensuring the inclusion of new features. Accordingly, if a feature isn't ready
by the set release date, the release proceeds as scheduled instead of being
delayed for that feature.

## Schedule
The OpenSSL release schedule follows a biannual model, with new versions being
launched every April and October. Multiple releases may be active concurrently,
resulting in overlapping release cycles. Each release is divided into the
following phases:
* **Planning**:
Continuous process, provides input to the Release Definition phase.
* **Release Definition**:
Defines release backlog, lasts up to 4 weeks.
* **Development**:
Execution of the release backlog, spans from 20 to 24 weeks.
* **Release**:
Addressing issues discovered by the community in pre-releases. Up to 6 weeks.
* **Support**:
A support phase.

## Phases
### 1. Planning
Planning is a continuous process of backlog refinement, running outside of
release cycles, leading up to the Release Definition phase. This phase involves
regular planning and backlog refinement sessions where the prioritised product
backlog is developed, including epics and estimated work items. Work items refer
to features that have passed acceptance criteria[^1] and bugs requiring a
substantial time to resolve.

### 2. Release Definition
The Release Definition phase begins concurrently with the Alpha phase of the
preceding release and can extend up to four weeks. A shorter phase duration
allows for a more extensive development phase. In this phase, the release's
scope is established. A release steering committee[^2] assumes responsibility for
defining the release theme and priorities, taking into consideration the
decomposed and estimated product backlog items. The phase's outcome includes a
finalised release backlog and a release plan, both of which require sign-off by
the OpenSSL Management Committee (OMC). Following the sign-off, the release
plans are communicated externally.

### 3. Development
The Development phase centres on the implementation and execution of tasks
identified in the release backlog. The phase can span from 20 to 24 weeks. To
ensure timely release, commitments are periodically verified, and necessary
adjustments are made. While the release backlog is generally maintained as
initially defined, modification may be authorised by the release steering
committee[^2] under specific circumstances, such as:
* A task, initially underestimated, poses a risk of not being completed.
* The emergence of an unexpected high-priority task necessitates immediate
  resolution.

Any modifications to the release backlog should be conducted with an intent to
preserve the balance. Thus, whenever a task is added, an equivalent effort lower
priority task(s) must be removed. Conversely, when a task is removed, another
may be added to the release backlog provided that such a task fits within the
available time and is not prioritised higher than any existing task within the
release backlog.

This phase concludes with an alpha release readiness check by the steering
committee. Upon successful completion of this check, an alpha release is
created, marking the beginning of the Alpha phase.

### 4. Release
The Release phase of OpenSSL library commences with the creation of an alpha
release at the end of the Development phase and spans over a period of six
weeks. In the Release phase, no new features can be added, nor can any code
refactoring be planned to be undertaken. Effective communication at this stage
is crucial to ensure the quality of the release and, consequently, the success.

  * **Alpha**:
  During this phase, feature development is complete and feedback from the
  community is being actively addressed. Testing, bug fixing, and documentation
  updates are ongoing. Any critical issues discovered may lead to the removal of
  the offending code.
  * **Beta**:
  This phase signifies the library is nearing its final release. Testing remains
  intensive, but the focus is on ensuring stability. While all identified
  regressions and critical concerns have been addressed, only crucial,
  last-minute fixes are expected.
  * **Final**:
  The Final phase is focused on release preparation. The tasks involved include
  updating the list of known issues, tagging the code git tree, and issuing
  digital signatures among others. The phase concludes with the new release
  becoming publicly available and communicated.

See [Release Requirements Policy] for details on each type of release.

### 5. Support[^3]
  * **Full Support**:
  Upon the final release a one-year Full Support is initiated for regular
  releases, and a four-year period for LTS releases. During this phase, bugs and
  security issues are addressed and fixed according to the [Stable Release
  Updates Policy].
  * **Maintenance Support**:
  Immediately after the Full Support phase ends, the Maintenance Support phase
  begins, lasting for one year. During this phase, the primary focus is on
  fixing security issues, although other bugs may be addressed at the discretion
  of OpenSSL engineering.

[Stable Release Updates Policy]: https://www.openssl.org/policies/technical/stable-release-updates.html
[Release Requirements Policy]: https://www.openssl.org/policies/technical/release-requirements.html

[^1]: Feature Acceptance Criteria - 🚧 The document is a work in progress.
[^2]: Release Steering Committee - A group comprised of four individuals: one
    internal member from OpenSSL, two specially invited representatives from the
    community, and the engineering manager. This committee is dedicated to
    guiding the release cycle, defining release priorities, authorizing release
    backlog modifications.
[^3]: We are currently re-evaluating our stable updates release policy. As we
    transition to time-based releases, adjustments may be necessary to maintain
    a sustainable support model.