Policy for Creating Designs
===========================

From time to time the OTC may require that certain problems should create a
design document before implementation should start. In that case this policy
will apply.

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
5) The individual(s) that will work on developing the design (refered to as the
   "design team" in this document)

Typically these will be identified during an OTC meeting and documented in the
meeting minutes.

Outputs
-------

The result of this process should be a design document in markdown format,
reviewed via a pull request and approved for merge into the otc git repository.

Other outputs may include feedback on the requirements and constraints that
were the input into the process. For example some candidate solutions that are
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
5. Agree solution

### (Optional) Identify key design sub-problems

Certain large problem domains may be split into smaller problem areas and a
separate design document produced for each sub-problem. In such a case this
policy should be applied recursively to address the design for each sub-problem
individually before incorporating all of the outputs into a single large
design document.

For such large problems a design workshop would normally be held to identify
the sub-problems that require individual designs.

### Identify candidate solutions

Once the problem area is understood candidate solutions (one or more) that meet
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
candidate solutions, or it could be in the form of an open invite for community
members to join the workshop where the solution is selected.

Optionally the OTC could select no solution and instead direct the design team
to iterate over the candidate solutions again and either make refinements or
identify additional options.

### Refine and document

In this step the design team provide further detail on the selected solution
option. There should be sufficient detail to enable the implementation work to
progress and to understand the trajectory of the solution into the future. Some
details may be omitted until a later stage of the development project if
appropriate and they are not needed until later.

The design document should be available for public comment in the form of a
pull request.

### Agree solution

In this step the OTC agree the solution as it is described in the design
document as produced by the design team. Once agreed the implementation may
proceed and the design document should be merged into the otc repository.

The OTC may choose not to agree a solution. In this case the process should
iterate back to the "Refine and document" step to incorporate feedback from the
OTC. In some cases more significant rework may be required, in which case the
OTC may choose to step back to any previous step in this design process.

In some cases the OTC may agree a solution which has certain details
deliberately omitted in order to defer work on those details until a later stage
of the implementation project. In such cases this process iterates back to the
"Refine and document" stage to fill in those details when they are eventually
required, and the subsequent amended design document must be agreed again by the
OTC.

Transparency and Community Involvement
--------------------------------------

It should be possible for community members to see the progress of designs
through the process and to pass comment on the proposed design prior to its
eventual agreement by OTC. As a minimum:

* The draft design document containing the candidate solutions should be
available as a pull request for public comment for at least one week prior to
the selection of the solution. As an alternative community members may be
offered an open invite to join the solution selection meeting.

* The eventual refined documented design should be available for public comment
as a pull request for at least one week prior to eventual agreement of the
solution
