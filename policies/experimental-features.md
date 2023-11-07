Experimental Feature Policy
===========================

A feature in OpenSSL may be designated as an experimental feature.

No stability or compatibility guarantees are offered for experimental features.
An experimental feature, or any API, protocol or file format which is part of an
experimental feature, may be changed arbitrarily and in compatibility-breaking
ways, or removed entirely at any time, including between releases.

An experimental feature is not enabled by default and must be explicitly enabled
at build time in order to be used. The enable flag to enable an experimental
feature must have the form `enable-unstable-XXX`. The corresponding `ifdef`
shall have the form `OPENSSL_NO_UNSTABLE_XXX`.

A prominent warning should be issued by the configure script if any experimental
feature is enabled, with a link to a webpage where people can learn more about
experimental features.

Experimental features may have associated documentation. This documentation is
not built by default unless the corresponding experimental feature is enabled.
Man pages for experimental features shall feature a prominent warning that the
man page relates to an experimental feature.

Experimental features exist to support the release engineering process where the
use of a feature branch is not feasible or desirable. Feature branches should be
used instead of experimental features where it is reasonable to do so.

Experimental features are not required to be in a buildable or usable state at
the time of a release or at the time of the creation of a release branch.

Nothing relating to an experimental feature shall be considered a CVE or handled
under the security process.

An experimental feature may have an associated feature scope definition
document, which is a Markdown file under `doc/experimental-features` which
provides any relevant context about the feature. In particular, it may clarify
what is and is not part of the experimental feature (and therefore unstable)
where this is not automatically implied via the use of build-time flags,
`ifdefs`, etc. This document is authoritative for the purposes of what
constitutes an experimental feature, subject to this policy.

Merging a PR which creates a new experimental feature requires OTC discussion
and approval. Non-trivial changes to an existing feature scope definition
document may be subject to OTC review if needed via the standard OTC hold
process.
