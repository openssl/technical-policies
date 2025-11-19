# Testing Policy

This applies to all [stable] and development branches of the main code repository.

Within this policy _functional behaviour_ means what the system does, i.e.
given a set of inputs it will produce a set of outputs. This does not include
how the system does it. For example refactoring or performance improvements do
not affect _functional behaviour_.

Except where noted below:

- All Pull Requests adding new functionality to the applications, libraries,
  providers or engines must include suitable tests.
- All Pull Requests fixing a _functional behaviour_ defect in the applications,
  libraries, providers or engines must include a test for that defect.

Pull Requests that do not change the _functional behaviour_ of the applications,
libraries, providers or engines do not require tests to be added. For example
the following types of changes do not require tests:

- Changes to comments, formatting, internal naming or similar
- Fixes for performance
- Refactoring

To be explicit the above statement means that tests are not required for changes
in:

- Documentation (including [CHANGES]/[NEWS])
- The test suite
- perl utilities
- Include files
- Build system
- Demos

Pull Requests that only affect minor cosmetic output do not require tests.

It is acceptable for the tests to be added via a different Pull Request to the
main Pull Request.

A test may be omitted where writing the test would result in disproportionately
more effort than writing the code being tested. For example, difficult to
reproduce error conditions.

## Triage Labels

Before approving a PR, the applicability of the testing policy to the PR must
be assessed and an appropriate label applied to the PR. One of the following
labels must be applied:

- `tests: present`, to be added where suitable tests are included in the same PR.
- `hold: tests needed`, where the testing policy requires tests but they are not
  currently included in a PR.
- `tests: exempted`, where tests are not included in a PR but are not required
  by this policy (for example, because the PR concerns only documentation,
  or because writing the test would result in disproportionately more effort;
  see above).
- `tests: deferred`, where the tests are required by the testing policy
  but it is intended to add these tests in a subsequent PR. The label should
  be removed (for example from a closed PR) once subsequent tests have
  been merged.

The `hold: tests needed` label blocks merging of the PR and constitutes a hold.
None of the other labels listed above block merging of a PR.

Only one of the above labels should be set on a PR at a given time.

It will generally be readily apparent which label is applicable
at any given time. However, if there is a lack of agreement over the
status of a PR in regards to the test policy, this should be resolved
via the normal review process. For example, OpenSSL Committers are not required
to agree to use of the `tests: deferred` label if they do not feel it is
appropriate.

Use and approval of the `tests: deferred` label is at the discretion of the
OpenSSL Committers. It is recommended that this label be used only when a
subsequent PR with tests is anticipated, but no specific rule is imposed on when
`tests: deferred` may be used at this time. The intention is to begin
surveillance and obtain visibility into how decisions under the testing policy
are being made prior to making any more specific prescriptions. For example,
this labelling allows obtaining a list of merged PRs for which a decision was
made to defer adding tests, but for which tests have not yet been added.

## Performance Testing

Performance testing should be performed automatically via [CI] on a regular basis
for certain components as defined by the OpenSSL Foundation and the OpenSSL
Corporation engineering managers.

Examples of performance testing that should be considered include:

- Individual algorithm performance operating over different input sizes
- SSL/TLS handshake time over multiple handshakes and for different protocol
  versions and resumption/non-resumption handshakes

Performance figures should be collected and tracked over time.

## Recommendations

This section makes recommendations that are not mandatory but should be
considered.

Pull requests that implement significant new functionality should consider
whether fuzz tests should be added.

As per the policy wording above, pull requests that implement refactoring are
not required to add new tests. However before refactoring is a good time to
check that there are sufficient tests and that all corner cases are covered.

Where performance fixes are implemented consideration should be given to whether
we need to add a performance test to the performance testing suite.


[CHANGES]: /policies/general/glossary/#changes
[CI]: /policies/general/glossary/#ci
[NEWS]: /policies/general/glossary/#news
[stable]: /policies/general/glossary/#stable-release
