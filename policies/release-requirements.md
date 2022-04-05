Release Requirements Policy
===========================

The OpenSSL project team creates the following three types of OpenSSL software
releases:

- [stable] releases
- [alpha] (pre-)releases
- [beta] (pre-)releases

This policy defines the requirements on the state of the source tree that
must be met before the release can be done.

Alpha Pre-releases
------------------

As this is just a preview release for testing things that have been worked
on the development branch of the source code the requirements are minimal.

- The CI must pass on tip of the development branch before the release commits
  were added to the tree.

Beta Pre-releases
-----------------

The API and ABI should be stable and the source code should be feature complete
by the first beta pre-release for the stable release. The following release
requirements apply to beta pre-releases.

- The code is functionaly complete in regards to the particular release
  objectives as set by OMC and OTC.
- There is no remaining refactoring required by OMC or OTC for the release.
- There are no remaining API changes required for the release.
  _This applies only to beta releases of a major release as API changes
  are not allowed on minor releases._
- All untriaged issues must be triaged.
- All regressions on the development branch from which the
  release is to be done must have a milestone assigned by OTC.
  _Regressions are considered from the previous stable release. The process
  how OTC assigns the milestone is not exactly defined on purpose._
- All issues or pull requests with beta milestone for the beta release
  are closed.
- There is no outstanding untriaged Coverity issue.
- Coveralls coverage has not decreased overall from the previous release.
- The CI must pass on tip of the development branch before the release commits
  were added to the tree, including the daily CI builds.
- The tree must be frozen at least for one day, which also ensures the daily CI
  builds run on the development tree tip.
- In case of the first beta release the OTC should explicitly approve
  that the source is ready for a release with a vote.

Stable Releases
---------------

For stable releases the requirements are basically the same as the release
requirements for the beta releases but they are repeated here for clarity.
As the release comes after the beta releases there is no need to repeat the
stability requirements as those should be held already by the beta releases.

- All untriaged issues must be triaged.
- All regressions on the development branch from which the
  release is to be done must have a milestone assigned by OTC.
  _Regressions are considered from the previous stable release. The process
  how OTC assigns the milestone is not exactly defined on purpose._
- All issues or pull requests with milestone for the release are closed.
- There is no outstanding untriaged Coverity issue.
- Coveralls coverage has not decreased overall from the previous release.
- The CI must pass on tip of the development branch before the release commits
  were added to the tree, including the daily CI builds.
- The tree must be frozen at least for one day, which also ensures the daily CI
  builds run on the development tree tip.
- In case of the first stable release from the development branch the OTC should
  explicitly approve that the source is ready for a release with a vote.

Triage Process
--------------

The issues and pull requests in GitHub must be assigned a `triaged: *` label by
an OTC member according to what is the type (feature, bug, documentation,
refactoring, ...) of the issue or pull request. When the triage happens for an
issue or pull request that is a bug/bug fix, it must be assessed whether the
bug is a regression or not. In general regressions are not allowed in stable
releases so they should be fixed as soon as possible, optimally before the
release is done. However sometimes that might not be reasonably possible.
In that case OTC should explicitly acknowledge that the regression is not to be
fixed before the release is done. That is done by assigning a milestone by
which the regression must be fixed and the `triaged: OTC evaluated` label.

[stable]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release
[alpha]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#alpha-release
[beta]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#beta-release
