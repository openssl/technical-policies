Testing Policy
==============

This applies to all stable and development branches of the main code repository.

Within this policy "functional behaviour" means what the system does, i.e.
given a set of inputs it will produce a set of outputs. This does not include
how the system does it. For example refactoring or performance improvements do
not affect functional behaviour.

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

By agreement of the Pull Request reviewers it is acceptable for the tests to be
added via a different Pull Request to the main Pull Request.

By agreement of the Pull Request reviewers tests may be omitted for difficult
to reproduce error conditions.

Performance Testing
-------------------

Performance testing should be performed automatically via CI on a regular basis
for certain components as defined by the OTC from time to time.

Examples of performance testing that should be considered include:
- Individual algorithm performance operating over different input sizes
- SSL/TLS handshake time over multiple handshakes and for different protocol
versions and resumption/non-resumption handshakes

Performance figures should be collected and tracked over time. Alerts should be
sent if performance drops below an agreed threshold versus an agreed baseline
as set from time to time by the OTC.

Recommendations
---------------

This section makes recommendations that are not mandatory but should be
considered.

Pull requests that implement significant new functionality should consider
whether fuzz tests should be added.

As per the policy wording above, pull requests that implement refactoring are
not required to add new tests. However refactoring is a good time to check that
there are sufficient tests and that all corner cases are covered.

Where performance fixes are implemented consideration should be given to whether
we need to add a performance test to the performance testing suite.
