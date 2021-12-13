Testing Policy
==============

This applies to all stable and development branches of the main code repository.
Except where noted below:

- All Pull Requests adding new functionality to the applications, libraries,
providers or engines must include suitable tests.
- All Pull Requests fixing a functional behavior defect in the applications,
libraries, providers or engines must include a test for that defect.

Pull Requests that do not change the functional behaviour of the applications,
libraries, providers or engines do not require tests to be added. For example
the following types of changes do not require tests:
 - Changes to comments, formatting, internal naming or similar
 - Fixes for performance
 - Refactoring

To be explicit the above statement means that tests are not required for changes
in:
 - Documentation (including CHANGES.md/NEWS.md)
 - The test suite
 - perl utilities
 - Include files
 - Build system
 - Demos

Pull Requests that only affect minor cosmetic output do not require tests

Performance Testing
-------------------

Performance testing should be performed automatically via CI on a regular basis
for certain defined components.

Components that should be performance tested via CI include:
 - openssl speed for all supported algorithms
 - openssl s_time

Performance figures should be collected and tracked over time. Alerts should be
sent if performance drops below an agreed threshold versus an agreed baseline
as set from time to time by the OTC.
