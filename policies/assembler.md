# Policy for Accepting Assembler Optimisations

New assembler optimisations for any algorithm having a C based implementation in
any provider are always acceptable (subject to standard review procedures) for
all platforms in the master branch.

New assembler optimisations are never acceptable for any platform or provider in
a [stable release] branch.

Updates to existing assembler optimisations in a stable release branch are only
acceptable where such updates would be allowed under the
[stable release update policy].

Where assembler optimisations are acceptable they should be implemented using
[perlasm].

[perlasm]: /policies/general/glossary/#perlasm
[stable release]: /policies/general/glossary/#stable-release
[stable release update policy]: /policies/technical/stable-release-updates/
