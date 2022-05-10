Release Requirements Policy
===========================

The OpenSSL project team creates the following three types of OpenSSL software
releases:

- [stable] releases
- [alpha] (pre-)releases
- [beta] (pre-)releases

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

- The code is functionally complete in regards to the particular release
  objectives as set by OMC and OTC.
- There is no remaining refactoring required by OMC or OTC for the release.
- There are no remaining API changes required for the release.
  _This applies only to beta releases of a major release as API changes
  are not allowed on minor releases._
- There are no remaining API additions required for the release.
- All untriaged issues older than 4 days must be triaged.
- All issues triaged as regressions on the development branch from which the
  release is to be done must have a milestone assigned by OTC.
  _Regressions are considered from the previous stable release. The process
  of how OTC assigns the milestone is not exactly defined on purpose._
- All issues or pull requests with beta milestone for the beta release
  are closed.
- There are no outstanding untriaged Coverity issues.
- Coveralls coverage has not decreased overall from the previous release.
- The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- The tree must be frozen for at least 4 days. No changes apart from regression
  or security fixes should be merged during the freeze.
- For 1 day before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- Embargoed security fixes are excepted from the rule above as they cannot
  be merged to the public tree before the release is being prepared.
- In case of the first beta release the OTC should explicitly approve
  that the source is ready for a release with a vote.

Stable Releases
---------------

For stable releases the requirements are basically the same as the release
requirements for the beta releases but they are repeated here for clarity.
As the release comes after the beta releases there is no need to repeat the
stability requirements as those should be held already by the beta releases.

- All untriaged issues older than 4 days must be triaged.
- All issues triaged as regressions on the development branch from which the
  release is to be done must have a milestone assigned by OTC.
  _Regressions are considered from the previous stable release series and the
  previous stable release from the branch being released. The process
  how OTC assigns the milestone is not exactly defined on purpose._
- All issues or pull requests with milestone for the release are closed.
- There are no outstanding untriaged Coverity issues.
- Coveralls coverage has not decreased overall from the previous release from
  the particular development branch.
- The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- The tree must be frozen for at least 4 days. No changes apart from regression
  or security fixes should be merged during the freeze.
- For 1 day before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- Embargoed security fixes are excepted from the rule above as they cannot
  be merged to the public tree before the release is being prepared.
- In case of the first stable release from the development branch the OTC should
  explicitly approve that the source is ready for a release with a vote.

Triage Process
--------------

The issues and pull requests in GitHub must be assigned a `triaged: *` label by
an OTC member according to what is the type (feature, bug, documentation,
refactoring, ...) of the issue or pull request. When the triage happens for an
issue or pull request that is a bug/bug fix, it must be assessed whether the
bug is a regression or not.

In general regressions are not allowed in stable releases so they should be
fixed as soon as possible, optimally before the release is done. However
sometimes that might not be reasonably possible or an issue is identified
to be a regression later than during the initial triage.

In that case OTC should explicitly acknowledge that the regression is not to be
fixed before the release is done. That is done by assigning a milestone by
which the regression must be fixed and the `triaged: OTC evaluated` label.

Responsibilities
----------------

The OTC is responsible to ensure the releases confirm to these requirements.
How exactly the OTC handles this responsibility is undefined here on purpose
except for the explicit votes required for the first beta release and the first
stable release from a particular development branch.

For example the responsibility to follow the release requirements can be
delegated by the OTC to the person (or the team) preparing the release.

[stable]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release
[alpha]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#alpha-release
[beta]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#beta-release
