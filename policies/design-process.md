Design Process Policy
=====================

Objectives
----------

The objective of the design process is to increase the quality of the software
engineering process. The production of design documents confers the following
benefits:

  - Prior to implementation, the present understanding of the problem domain is
    documented in a readily accessible fashion. The understanding of other
    OpenSSL contributors is enhanced, as is their ability to identify any
    potential issues in the design, or to make related code contributions.

  - After implementation, the design document serves as documentation of
    the architectural and design decisions and rationale which served as the
    basis for the implementation of the relevant functionality. This is
    beneficial both to contributors who wish to understand the relevant code,
    or evolve the implementation, but also to contributors who wish to implement
    related functionality or understand non-obvious rationales behind given
    design decisions.

It is recognised that designs will often necessarily change once implementation
begins. In the majority of cases, the understanding of the problem domain will
evolve and improve after implementation begins and this will indicate further
changes to the design. This is an iterative process of progressive refinement.
It is an explicit objective of this policy to support and encourage this
agile-style process, as opposed to a waterfall-style process in which designs
must be approved and finalised prior to implementation.

This policy adopts a graded system of review in which the degree of formal
approval by the OTC which a design must undergo is proportionate to the scope
and risks of the design. For example, a design which involves new or evolved
public APIs may require a greater amount of scrutiny, whereas a purely internal
design may require that the OTC simply be notified of the design document and
invited to comment, with implicit approval in the absence of objections.

Requirement for Design Documents
--------------------------------

A design document is required for any proposed enhancement which adds
significant new APIs or non-trivially evolves or modifies existing APIs.

For any other kind of proposed enhancement, a design document should be created
if it incorporates design decisions or aspects significant enough to warrant
one. For example, if an enhancement adds a new internal module with clearly
delineated boundaries with a documented internal API which can be consumed by
other code internal to OpenSSL, a design document is desirable. This example is
not exhaustive. The proposer may use their discretion in determining whether a
design document is desirable, but any OTC member may require that a design
document be produced.

Levels of Scrutiny
------------------

There are three levels of scrutiny which can be applied to a design, listed
below in ascending order of severity:

 - Notify
 - Present
 - Approve

These levels work as follows:

 - At the **Notify** level, the OTC is notified of a new design
   when it is available for review, via an email to the openssl-project mailing list.
   OTC members and committers can review and comment on the design.
   A minimum waiting time of one week after the notification is made applies to
   ensure OTC members have the opportunity to review the design.

   The notification does not need to be made by the author of the design
   document.

 - At the **Present** level, the OTC is notified of a new design
   in the same way that it is at the Notify level. The same minimum waiting time
   applies. The design is also introduced and explained in a presentation given
   to the OTC in a meeting of the OTC. The OTC has opportunities to ask
   questions and raise concerns at this meeting. This presentation may be given
   by the author of the design but need not be.

 - At the **Approve** level, the OTC must explicitly approve the design
   by making a decision as the OTC. The OTC should be notified of a
   new design in the same way they are notified at the Notify level.
   A presentation to the OTC may be made but is not required.

When a design is produced, it should be submitted to the OpenSSL repository as a
PR. It should be determined which level of scrutiny is appropriate according to
this policy and this should be noted in the PR. Any applicable actions (such as
notifying the OTC via the openssl-project list) should be carried out once the
design is ready for review.

Any OTC member may object to the processing of a design at a given level of
scrutiny and require that a higher level be used.

A proposer may choose to use a higher level of scrutiny than is required.

Selecting a Level
-----------------

To determine the level of scrutiny which must be applied to a design by default,
follow the following process:

  - Any design which proposes to create new public APIs, or non-trivially evolve
    or modify existing public APIs, must use at least the Present level of
    scrutiny.

  - Any other design may use the Notify level of scrutiny.

Checklists
----------

### Checklist for the Notify Level

  - Design document published as a PR on GitHub
  - OTC notified and invited to comment or object via an email to
    openssl-project list
  - At least one week has passed from OTC notification

### Checklist for the Present Level

  - Design document published as a PR on GitHub
  - OTC notified and invited to comment or object via an email to
    openssl-project list
  - Presentation given to a quorate OTC meeting by the design's proposer, and
    OTC has had opportunity to ask questions and discuss the proposal
  - At least one week has passed from OTC notification

### Checklist for the Approve Level

  - Design document published as a PR on GitHub
  - OTC makes a decision approving the design. The decision is made according to
    standard OTC policies.

Implementation
--------------

It is not required to wait for a design document to be approved and merged
before beginning implementation. Implementation should generally begin
immediately. This facilitates an agile process and helps to improve the design
document, as implementation will often lead to an improved understanding
of the problem domain, leading in turn to an improved design document.

A design document PR, or a PR implementing said design, should not be merged
until the relevant requirements for the level of scrutiny used have been
satisfied. It is permissible for a design document and an implementation to be
part of the same PR.

Revisions to Pending Designs
----------------------------

Where changes to a design document need to be made (for example, due to an
evolved understanding of the problem domain arising from an implementation in
progress), if the design document has already been merged, a new PR should be
raised and this will go through the normal process described above.

If the design document has not yet merged:

  - if the Notify or Present level of scrutiny is being used, it may be changed
    by the proposer freely. Another notification to the openssl-project list may
    be made if the changes are deemed very major but is not required.

  - if the Approve level of scrutiny is being used, and the approval has already
    been finalised or a vote is ongoing, the design should not be changed and a
    new PR should be raised. The document may be changed freely if it has been
    decided that the Approve level of scrutiny is to be used but a vote has not
    yet opened.

