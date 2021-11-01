Policy for Creating Designs
===========================

From time to time the OTC may decide that certain problems should have a
design document created for them before implementation should start. Such a
decision should be minuted in OTC meeting minutes or recorded via a vote. In
that case this policy will apply.

Pull Requests that implement a solution, or part of a solution, covered by a
design document should clearly reference that design document. Pull requests
that modify a solution covered by a design document should not be accepted
unless the design document is also updated to describe the modified solution.

The design approach described in this document should be considered iterative.
Only "just enough" design should be done to get the implementation project to
the next stage. Certain design decisions and sub-problems may be deferred until
some later stage.

Inputs
------

Prior to commencing design work the OTC shall identify:

1) The business requirements for the problem to be solved (obtained from the OMC)
2) The scope of the specific problem area to be addressed
3) Any additional design constraints that the OTC wishes to impose
4) Any other constraints that may apply (e.g. timescales)
5) The individual(s) that will work on developing the design (referred to as the
   "design team" in this document)

Typically these will be identified during an OTC meeting and documented in the
meeting minutes.

Outputs
-------

The result of this process should be a design document in markdown format,
reviewed via a pull request and approved for merge into the main source git
repository via an OTC decision (minutes in OTC meeting minutes or recorded via
a vote). The design document must include:

 - Any assumptions that have been made
 - Any omissions that may be filled in later
 - Any APIs that the implementation will provide. This should include some
   minimal documentation of the APIs (not necessarily end-user focussed) to show
   how they should be used.
 - A specification of the tests that will be expected as part of the
   implementation. This should cover the APIs as they are meant to be called,
   what the return values are, etc.

Other outputs may include feedback on the requirements and constraints that
were the input into the process. For example, some candidate solutions that are
considered may not satisfy all constraints or requirements. In such a case the
candidate solution should be rejected unless feedback on the requirements and
constraints modifies them to allow the solution to be selected.

Design Steps
------------

The following design steps should be used to create a design document:

1. (Optional) Identify key design sub-problems
2. Identify candidate solutions
3. Select solution
4. Refine and document
5. Approve solution

### (Optional) Identify key design sub-problems

Certain large problem domains may be split into smaller problem areas and a
separate design document produced for each sub-problem. In such a case this
policy should be applied recursively to address the design for each sub-problem
individually before incorporating all of the outputs into a single large
design document.

For such large problems a design workshop would normally be held to identify
the sub-problems that require individual designs.

### Identify candidate solutions

Once the problem area is understood, candidate solutions (one or more) that meet
the requirements and constraints should be identified. Each candidate solution
should be documented in only as much detail as is required to explain the
primary characteristics of the solution approach so that it can be compared
against the other candidate solutions and to determine how well it meets the
requirements and constraints.

In some cases a candidate solution may be identified that meets most of the
requirements and constraints but not all. Where this happens the requirements
and constraints that are not met by the candidate solution should be clearly
stated.

Typically the design team will be the people that identify and document the
candidate solutions. In some cases it may be appropriate to hold a design
workshop to collectively identify the candidate solutions. In this case it will
typically still be necessary for the design team to document the solution
options outside of the workshop.

The design team may choose to make recommendations about the preferred solution
option.

### Select solution

Once the candidate solutions have been identified and documented a solution
must be selected by the OTC. There should be an opportunity for the OpenSSL
community or non-OTC members to provide input into the decision. This could
either be in the form of comments on a draft Pull Request describing the
candidate solutions, or it could be in the form of an invite for community
members to join the workshop where the solution is selected.

Optionally the OTC could select no solution and instead direct the design team
to iterate over the candidate solutions again and either make refinements or
identify additional options.

### Refine and document

In this step the design team provide further detail on the selected solution
option. There should be sufficient detail to enable the implementation work to
progress and to understand the trajectory of the solution into the future. Some
details may be omitted until a later stage of the development project if
appropriate and such a level of detail is not needed until later. The
assumptions of a solution should be clearly listed along with any omissions.

The design document should be available for public comment in the form of a
pull request.

### Approve solution

In this step the OTC approve the solution as it is described in the design
document as produced by the design team. Once approved the implementation may
proceed and the design document should be merged into the main source repository.

The OTC may choose not to approve a solution. In this case the process should
iterate back to the "Refine and document" step to incorporate feedback from the
OTC. In some cases more significant rework may be required, in which case the
OTC may choose to step back to any previous step in this design process.

In some cases the OTC may approve a solution which has certain details
deliberately omitted in order to defer work on those details until a later stage
of the implementation project. In such cases this process iterates back to the
"Refine and document" stage to fill in those details when they are eventually
required, and the subsequent amended design document must be approved again by
the OTC.

Transparency and Community Involvement
--------------------------------------

It should be possible for community members to see the progress of designs
through the process and to pass comment on the proposed design prior to its
eventual agreement by OTC. As a minimum:

* The draft design document containing the candidate solutions should be
available as a pull request for public comment for at least one week prior to
the selection of the solution. In addition to that, community members may be
offered an invite to join the solution selection meeting.

* The refined documented design should be available for public comment as a pull
request for at least one week prior to eventual agreement of the solution
