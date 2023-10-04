Release Requirements Policy
===========================

The OpenSSL project team creates the following 5 types of OpenSSL software
releases:

- [alpha] (pre-)releases
- [beta] (pre-)releases
- [major] releases
- [minor] releases
- [patch] releases

This policy defines the requirements on the state of a branch in the source
tree that must be met before a release from that branch can be done.

Alpha Pre-releases
------------------

As this is just a preview release for testing things that have been worked
on in the development branch, the requirements are minimal.

- The CI must pass on the tip of the development branch before the release
  commits were added to the tree.

Beta Pre-releases
-----------------

The API and ABI should be stable and the source code should be feature complete
by the first beta pre-release. The following release requirements apply to beta
pre-releases.

- [ ] The code is functionally complete in regards to the particular release
  objectives as set by OMC and OTC.
- [ ] There is no remaining refactoring required by OMC or OTC for the release.
- [ ] There are no remaining API changes required for the release.
  _This applies only to beta releases of a major release as API changes
  are not allowed on minor releases._
- [ ] There are no remaining API additions required for the release.
- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous stable release or previous
  beta release._
- [ ] All issues or pull requests with the milestone for the beta release
  are closed.
- [ ] There are no outstanding untriaged Coverity issues.
- [ ] Coveralls coverage has not decreased overall from the previous release.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 3 business days. No changes apart from
  regression or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] In case of the first beta release the OTC should explicitly approve
  that the source is ready for a release with a vote.

Major and Minor Releases
------------------------

As the release comes after the beta releases there is no need to repeat the
stability requirements as those should be held already by the beta releases.

- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous stable release series._
- [ ] All issues or pull requests with the milestone for the release are closed.
- [ ] There are no outstanding untriaged Coverity issues.
- [ ] Coveralls coverage has not decreased overall from the previous release from
  the particular development branch.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 7 days. No changes apart from regression
  or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] The OTC should explicitly approve that the source is ready for a release with
  a vote.

Patch Releases
--------------

The patch releases follow a similar process to major and minor releases with
some simplifications as they are much more frequent and the tree stability
requirements for the stable development branches should ensure there is
a minimum amount of regressions in between the patch releases.

- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous minor, major or patch release
  from the development branch._
- [ ] All issues or pull requests with the milestone for the release are closed.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 3 business days. No changes apart from
  regression or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] Embargoed security fixes are excepted from the rule above as they cannot
  be merged to the public tree before the release is being prepared.

Triage Process
--------------

The issues and pull requests in GitHub must be assigned a `triaged: *` label by
an OTC member according to what is the type (feature, bug, documentation,
refactoring, ...) of the issue or pull request. When the triage happens for an
issue or pull request that is a bug/bug fix, it must be assessed whether the
bug is a regression or not.

In general regressions should be fixed as soon as possible, optimally before
the next release from the development tree is done. However sometimes that
might not be reasonably possible due to time, resource, or fix complexity
constraints.

In that case OTC should explicitly acknowledge that the regression is not to be
fixed before the release is done. That is done by assigning a milestone by
which the regression must be fixed and the `triaged: OTC evaluated` label.

The triage ideally happens as soon as possible, however the triage process can
sometimes be costly, so we aim to have issues triaged no later than 4 days
after they are reported.

Responsibilities
----------------

The OTC is responsible to ensure the releases conform to these requirements.
How exactly the OTC handles this responsibility is undefined here on purpose
except for the explicit votes required for the first beta release and the
major or minor releases.

For example the responsibility to follow the release requirements can be
delegated by the OTC to the person (or the team) preparing the release.

[alpha]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#alpha-release
[beta]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#beta-release
[major]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#major-release
[minor]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#minor-release
[patch]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#patch-release
[triaged]: #triage-process
