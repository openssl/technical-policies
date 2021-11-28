Policy on API compatibility in minor releases
=============================================

**No changes in existing public API functions and data are allowed.**

Only API additions are allowed in minor releases.

Although there might be some kinds of changes that are ABI compatible such
as constification of parameters, changing a return value type from void
to int to be able to indicate an error in the call, or changes of an API
call from a macro to a function, these kinds of changes are allowed only in
major releases.

If necessary, a new API call can be added to implement the required changes in
minor releases.
