# OpenSSL documentation policy

This document describes the code documentation and commenting
requirements for the OpenSSL project.

The project's documentation is all about making the libraries and tools
more accessible to our users and making the code more maintainable.
This policy applies to new submissions, existing code is below par and will
be gradually improved.

## Chapter 1: Command line commands and arguments

All new or modified arguments to the commands must be documented in the
`doc/man1` directory.  This documentation is in _POD_ format.

All new commands must be documented in the `doc/man1` directory.  This
documentation is in _POD_ format.

## Chapter 2: Public symbols in the libraries

All new public symbols must be documented in a _POD_ manual page in the
`doc/man3` directory.  This includes both macros and functions.

The allowed exceptions are:

- guard macros preventing a header file being included twice
- new OPENSSL_NO_DEPRECATED_ macros
- new symbols generated automatically via `make update` (errors, objects, etc)

## Chapter 3: Overviews, conventions, et al

Where additional user facing information is required, it should be
included in the `doc/man7` section.  This includes, but is not limited to:

- descriptions of data structures and their usage
- provider calls and call backs
- algorithm descriptions and parameters
- descriptions of architectural decisions

## <a name="fsgm"></a>Chapter 4: Internal functions, structures, globals and macros

Internal functions and macros are those defined in the `include/crypto`
and `include/internal` directories.

These should all be documented at the point of implementation.  A comment
describing their purpose and the input and output arguments and return value
for functions suffices.

For _trivial_ items, where their operation is obvious from their
implementation, the documentation requirement is not mandated.  The following
are generally representative of trivial items, however it is quite
possible for any of these to be non-trivial in specific instances and
therefore require documentation:

- OSSL_DISPATCH tables
- upref functions
- free functions
- simple getter/setter functions
- wrappers for other functions (a function that calls a more recent `_ex`
  variant or a group of functions that call a common internal routine)

For structures, each of the fields should be commented stating its
purpose.  Again, a _trivial_ exception applies where the purpose is
obvious.  Some representative examples:

- `OSSL_LIB_CTX *ctx;` where there is only one library context referenced in
  the structure.
- `struct *next;` in a linked list implementation.
- `CRYPTO_REF_COUNT refcnt;`

## Chapter 5: Static functions and globals and local structures and macros

These are functions, structures, globals and macros local to a specific
C file or defined for a single directory as part of a local .h file.

These should all be documented at the point of implementation.  Follow the
rules and exceptions listed [above](#fsgm).  In some cases slightly more
leniency with respect to _trivial_ can be tolerated.

## Chapter 6: Code comments

Comments in code should explain what the algorithm is doing and why.
It should not parrot the effect of each statement.  As the complexity of
the code increases, the size and detail of comments should also increase.

## Chapter 7: Assembly code

Assembly code should include a good description of the algorithm and
approach being used.  This should be followed by a performance comparison
and then the assembly code itself.  The assembly code should be well
commented, but it isn't necessary to comment every line.  A comment
describing each block of code suffices.

There are no _trivial_ exceptions for assembly code.

## Chapter 8: Configure options

New options added to the configuration scripts must be documented in the
`INSTALL.md` file.

## Chapter 9: Changes and news

Significant modifications should be documented in the `CHANGES.md` file.

Very significant features and changes should be documented in the `NEWS.md`
file.

In both cases, the added note should be short and to the point.

## Chapter 10: Automated sanity checking

The `make doc-nits` command should be run before submitting a pull
request and any problems it locates must be addressed.

## Chapter 11: Common sense

Comments in the code are to improve readability and comprehension.
Where the code is obvious, there is no need to include a comment.
However, common sense applies.  Always err in favour of including more
comments than less or none.  Code that you've just written that is
_obvious_ will not necessarily be to someone else two years later.

