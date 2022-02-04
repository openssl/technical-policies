Stable Release Updates Policy
=============================

This policy covers allowed changes on stable release branches.

Definitions
-----------

A **stable release** is a series beginning with a major or minor release that
is not a pre-release, and all its updates.

A **patch release** is an update within a stable release.

A **public interface** is any function, structure or macro declared in a public
header file.

A **bug fix** is a fix of functionality of the libraries, modules,
applications, or the build system that (all or any items might apply):

- makes the functionality conform with the existing end-user documentation
  where such a change does not break existing common usage
- makes the end-user documentation conform with the existing behavior of the
  software

A **bug fix** is also a fix for an unexpected behavior (not explicitly
documented in one way or another) of the software when such unexpected behavior
is a security vulnerability.

A **bug fix** is also a fix for an unexpected behavior of the following kinds
even if such behavior is not a security vulnerability:

- a memory leak
- a crash
- a hang/deadlock or a race condition
- an out of bounds read or write
- an uninitialized value read
- a memory use after free
- C language undefined behavior

A **bug fix** is also a build failure or test failure fix for platforms that
are noted as supported for the stated release.

A **bug fix** might also be a fix for an unexpected behavior (not explicitly
documented in one way or another) where the implementation does not conform to
existing public specifications that we claim to conform to. Where the
documentation explicitly contradicts the specifications the documented behavior
is what matters.

A **bug fix** is **not**:

- performance enhancement
- memory usage reduction
- replacement implementation of algorithms
- refactoring
- addressing deviations from the [coding style policy].

[coding style policy]: https://github.com/openssl/technical-policies/blob/master/policies/coding-style.md

An **end-user documentation** is:

- manual pages and other documentation in `doc` directory excluding the
  `doc/internal` directory
- various documentation files in the top-level directory
- demo code in `demos`

An **end-user documentation** is **not**:

- comments in the code (including public header files)
- internal documentation (doc/internal)

Changes allowed in stable releases
----------------------------------

No API or ABI breaking changes are allowed in a minor or patch release.

Only bug fixes, fixes for security issues, and end-user documentation
additions and fixes are allowed in stable releases.

The **addition** of new platforms to LTS branches is acceptable so long as the
required changes consist solely of **additions to configuration**.

A documentation addition allowed in stable releases is any addition to the
documentation that documents the existing behavior of the software. I.e., the
documentation additions in stable releases cannot add new API contract
constraints, or implicitly create new bugs in the software by documenting
behavior that is different from the existing behavior of the software.

Comment or whitespace fixes are allowed only as part of a bug fix to avoid
later merge conflicts.

New tests and test cases are allowed only as part of a bug fix.

Patch release commits are obviously allowed (updates to CHANGES.md, NEWS.md,
version, and copyright updates).

**Exceptions to this policy require OTC approval.**
