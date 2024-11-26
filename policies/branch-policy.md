# Branch Policy

The openssl repository contains the following maintained branches:

## The default development branch

- Any type (bug fix, feature, refactoring, ...) of pull requests is allowed.
- The development of the next minor or major release happens there.
  API/ABI breaking changes are allowed on this branch only if the next
  release will be a major release.
- Any changes merged to this branch must be ported to the future major
  and future minor branches if they are applicable. This can be done by
  directly cherry-picking the changes when merging if there are no conflicts.
  By this we must ensure that no features or bug fixes are unintentionally
  lost in future major or minor releases.

## The supported release branches

- The development of the next patch releases of supported stable releases
  happens there.
- According to [stable release update policy] only bug fixes and
  documentation changes are allowed.
- By exception given by OMC also other types of pull requests can be merged.
- Bug fix and documentation pull requests must be always merged to the
  latest branch where the bug or documentation deficiency is present including
  the future major and minor branches.
  It can be then merged (backported or directly cherry-picked) to all
  older branches where the deficiency is present.

## A future major branch

- The development of a future major release happens there. Implicitly it
  means that any API/ABI breaking changes are allowed but OMC can (and
  usually will) limit the extent of the breakage allowed.
- Major features are allowed. Examples of a major feature: A completely
  new implementation of a protocol. New API for pluggable crypto modules.
- Major refactoring is allowed. Examples of major refactoring: Splitting
  libcrypto into multiple hierarchically dependent libraries.
- There might be no future major branch if the currently developed release
  is a major release and there are no changes accepted for a future major
  release yet.
- All changes specifically targetting this branch instead of the default
  development branch must be approved by OTC by consensus during
  a meeting or a formal vote.

## A future minor branch

- The development of the minor release that is supposed to be released
  after the release currently being developed at the default development branch
  happens there.
- No API/ABI breaking changes are allowed.
- No major features are allowed unless explicitly acked by OMC as targeted for
  the minor release.
- No major refactoring is allowed.
- Any changes (features, bug-fixes, documentation, ...) done on the future
  minor branch must be ported or directly cherry-picked to the future major
  branch if applicable.
- Exceptions are possible for example when we are removing deprecated
  functionality in the future major branch.
- There might be no future minor branch when the expected future release would
  be a major release or there are no changes accepted for a future minor
  release yet.
- All changes specifically targetting this branch instead of the default
  development branch must be approved by OTC by consensus during
  a meeting or a formal vote.

## Branch and tag naming

The branch where the development of the next release is happening is called
`openssl-x.y` where `x` is the current major version number and `y` is the
version number of the release being developed. This is the default branch
of the repository.

The existing stable release branches are also named `openssl-x.y`.

As a legacy exception to the rule above, the branch where the development of
OpenSSL-1.1.1 fix releases is happening is called `OpenSSL_1_1_1-stable`.

Future-major: The branch where the development of the future major release is
happening is called `openssl-x.0` where `x` is the next major version number.

Future-minor: The branch where the development of a future minor release is
happening is called `openssl-x.y` where `x` is the current major version number
and `y` is the version number of a version that will be released after the
version currently developed at the default development branch.

Release tags: The releases are tagged with tags named `openssl-x.y.z` for stable
patch releases, `openssl-x.y.0-alphaN` for alpha releases, and
`openssl-x.y.0-betaN` for beta releases. As a legacy exception the fix releases
of OpenSSL-1.1.1 are named `OpenSSL_1_1_1<fix-letter(s)>`.

## Branch creation

The exact times when the future major and minor branches are created are
undefined by the policy as that is an OMC responsibility to decide.

[stable release update policy]: https://github.com/openssl/technical-policies/blob/master/policies/stable-release-updates.md
