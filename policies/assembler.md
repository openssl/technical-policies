Policy for Accepting Assembler Optimisations
============================================

New assembler optimisations for any algorithm having a C based implementation in
any provider are always acceptable (subject to standard review procedures) for
all platforms in the master branch.

New assembler optimisations are never acceptable for any platform or provider in
a stable release branch.

Updates to existing assembler optimistations in a stable release branch are only
acceptable where such updates would be allowed under the ["Stable Release
Updates" policy][1].

Where assembler optimisations are acceptable they should be implemented using
[perlasm][2].

[1]: https://github.com/openssl/technical-policies/blob/master/policies/stable-release-updates.md
[2]: https://github.com/openssl/openssl/blob/master/crypto/perlasm/README.md
