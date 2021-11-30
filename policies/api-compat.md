Policy on API compatibility in minor releases
=============================================

Public API of the OpenSSL libraries is defined as functions, macros, data
structure declarations, typedefs, and data variables in header files in the
`include/openssl` subdirectory of the source tree and `include/openssl`
subdirectory of the build tree.

**No changes to existing public API functions and data are permitted.** This
includes, but is not limited to:

- constification of arguments;
- changing `void` returns to `int` returns;
- changing a macro to a function and
- corrections of spelling.

Only API additions are allowed in minor releases.

Although the changes as listed above might be regarded as ABI compatible, they
cause various possible breakage when building applications depending on these
APIs and thus they are not allowed in minor releases.

If necessary, a new API call can be added to implement the required changes in
minor releases.
