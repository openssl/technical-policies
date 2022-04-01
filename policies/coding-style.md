# OpenSSL coding style

This document describes the coding style for the OpenSSL project. It is
derived from the [Linux kernel coding style][1].

This guide is not distributed as part of OpenSSL itself. Since it is
derived from the Linux Kernel Coding Style, it is distributed under the
terms of the [kernel license][2].

Coding style is all about readability and maintainability using commonly
available tools. OpenSSL coding style is simple. Avoid tricky expressions.

## Chapter 1: Indentation

Indentation is four space characters. Do not use the tab character.

Pre-processor directives use one space for indents:

```c
    #if
    # define
    #else
    # define
    #endif
```

## Chapter 2: Breaking long lines and strings

Don't put multiple statements, or assignments, on a single line.

```c
    if (condition) do_this();
    do_something_everytime();
```

The limit on the length of lines is _80_ columns. Statements longer
than _80_ columns must be broken into sensible chunks, unless exceeding
_80_ columns significantly increases readability and does not hide
information. Descendants are always substantially shorter than the parent
and are placed substantially to the right. The same applies to function
headers with a long argument list. Never break user-visible strings,
however, because that breaks the ability to grep for them.

## Chapter 3: Placing Braces and Spaces

The other issue that always comes up in C styling is the placement
of braces. Unlike the indent size, there are few technical reasons to
choose one placement strategy over the other, but the preferred way,
following Kernighan and Ritchie, is to put the opening brace last on the
line, and the closing brace first:

```c
    if (x is true) {
        we do y
    }
```

This applies to all non-function statement blocks (`if`, `switch`, `for`,
`while`, `do`):

```c
    switch (suffix) {
    case 'G':
    case 'g':
        mem <<= 30;
        break;
    case 'M':
    case 'm':
        mem <<= 20;
        break;
    case 'K':
    case 'k':
        mem <<= 10;
        /* fall through */
    default:
        break;
    }
```

Note, from the above example, that the way to indent a switch statement
is to align the switch and its subordinate case labels in the same column
instead of _double-indenting_ the case bodies.

There is one special case, however. Functions have the
opening brace at the beginning of the next line:

```c
    int function(int x)
    {
        body of function
    }
```

Note that the closing brace is empty on a line of its own, __except__ in the
cases where it is followed by a continuation of the same statement, such
as a `while` in a do-statement or an `else` in an if-statement, like this:

```c
    do {
        ...
    } while (condition);
```

and

```c
    if (x == y) {
        ...
    } else if (x > y) {
        ...
    } else {
        ...
    }
```

In addition to being consistent with K&R, note that that this brace-placement
also minimizes the number of empty (or almost empty) lines. Since the
supply of new-lines on your screen is not a renewable resource (think
25-line terminal screens here), you have more empty lines to put comments on.

Do not unnecessarily use braces around a single statement:

```c
    if (condition)
        action();
```

and

```c
    if (condition)
        do_this();
    else
        do_that();
```

If one of the branches is a compound statement, then use braces on both parts:

```c
    if (condition) {
        do_this();
        do_that();
    } else {
        otherwise();
    }
```

Nested compound statements should often have braces for clarity, particularly
to avoid the dangling-else problem:

```c
    if (condition) {
        do_this();
        if (anothertest)
            do_that();
    } else {
        otherwise();
    }
```

### Chapter 3.1: Spaces

OpenSSL style for use of spaces depends (mostly) on whether the name is
a function or keyword. Use a space after most keywords:

```c
    if, switch, case, for, do, while, return
```

Do not use a space after `sizeof`, `typeof`, `alignof`, or `__attribute__`.
They look somewhat like functions and should have parentheses
in OpenSSL, although they are not required by the language. For `sizeof`,
use a variable when at all possible, to ensure that type changes are
properly reflected:

```c
    SOMETYPE *p = OPENSSL_malloc(sizeof(*p) * num_of_elements);
```

Do not add spaces around the inside of parenthesized expressions.
This example is wrong:

```c
    s = sizeof( struct file );
```

When declaring pointer data or a function that returns a pointer type,
the asterisk goes next to the data or function name, and not the type:

```c
    char *openssl_banner;
    unsigned long long memparse(char *ptr, char **retptr);
    char *match_strdup(substring_t *s);
```

Use one space on either side of binary and ternary operators,
such as this partial list:

```c
    =  +  -  <  >  *  /  %  |  &  ^  <=  >=  ==  !=  ?  : +=
```

Do not put a space after unary operators:

```c
    &  *  +  -  ~  !  defined
```

Do not put a space before the postfix increment and decrement unary
operators or after the prefix increment and decrement unary operators:

```c
    foo++
    --bar
```

Do not put a space around the '.' and "->" structure member operators:

```c
    foo.bar
    foo->bar
```

Do not leave trailing whitespace at the ends of lines. Some editors with
_smart_ indentation will insert whitespace at the beginning of new lines
as appropriate, so you can start typing the next line of code right away.
But they may not remove that whitespace if you leave a blank line, however,
and you end up with lines containing trailing, or nothing but, whitespace.

Git will warn you about patches that introduce trailing whitespace, and
can optionally strip the trailing whitespace; however, if applying
a series of patches, this may make later patches in the series fail by
changing their context lines.

## Chapter 4: Naming

C is a Spartan language, and so should your naming be. Do not use long
names like _ThisVariableIsATemporaryCounter_. Use a name like _tmp_, which
is much easier to write, and not more difficult to understand.

Except when otherwise required, avoid mixed-case names.

Do not encode the type into a name (so-called Hungarian notation).

Global variables (to be used only if you REALLY need them) need to
have descriptive names, as do global functions. If you have a function
that counts the number of active users, you should call that
_count_active_users()_ or similar, you should NOT call it _cntusr()_.

Local variable names should be short, and to the point. If you have
some random integer loop counter, it should probably be called _i_.
Calling it _loop_counter_ is non-productive, if there is no chance of it
being mis-understood. Similarly, _tmp_ can be just about any type of
variable that is used to hold a temporary value.

If you are afraid that someone might mix up your local variable names,
perhaps the function is too long; see Chapter 6.

## Chapter 5: Typedefs

OpenSSL uses typedef's extensively. For structures, they are all uppercase
and are usually declared like this:

```c
    typedef struct name_st NAME;
```

For examples, look in [ossl_typ.h][7], but note that there are many exceptions
such as BN_CTX. Typedef'd enum is used much less often and there is no
convention, so consider not using a typedef. When doing that, the enum
name should be lowercase and the values (mostly) uppercase.  Note that enum
arguments to public functions are not permitted.

The ASN.1 structures are an exception to this. The rationale is that if
a structure (and its fields) is already defined in a standard it's more
convenient to use a similar name. For example, in the CMS code, a CMS_
prefix is used so ContentInfo becomes CMS_ContentInfo, RecipientInfo
becomes CMS_RecipientInfo etc. Some older code uses an all uppercase
name instead. For example, RecipientInfo for the PKCS#7 code uses
PKCS7_RECIP_INFO.

Be careful about common names which might cause conflicts. For example,
Windows headers use X509 and X590_NAME. Consider using a prefix, as with
CMS_ContentInfo, if the name is common or generic. Of course, you often
don't find out until the code is ported to other platforms.

A final word on struct's. OpenSSL has historically made all struct
definitions public; this has caused problems with maintaining binary
compatibility and adding features. Our stated direction is to have struct's
be opaque and only expose pointers in the API. The actual struct definition
should be defined in a local header file that is not exported.

## Chapter 6: Functions

Ideally, functions should be short and sweet, and do just one thing.
A rule of thumb is that they should fit on one or two screenfuls of text
(25 lines as we all know), and do one thing and do that well.

The maximum length of a function is often inversely proportional to the
complexity and indentation level of that function. So, if you have a
conceptually simple function that is just one long (but simple) switch
statement, where you have to do lots of small things for a lot of different
cases, it's okay to have a longer function.

If you have a complex function, however, consider using helper functions
with descriptive names. You can ask the compiler to in-line them if you
think it's performance-critical, and it will probably do a better job of
it than you would have done.

Another measure of complexity is the number of local variables. If there are
more than five to 10, consider splitting it into smaller pieces. A human
brain can generally easily keep track of about seven different things;
anything more and it gets confused. Often things which are simple and
clear now are much less obvious two weeks from now, or to someone else.
An exception to this is the command-line applications which support many
options.

In source files, separate functions with one blank line.

In function prototypes, include parameter names with their data types.
Although this is not required by the C language, it is preferred in OpenSSL
because it is a simple way to add valuable information for the reader.
The name in the prototype declaration should match the name in the function
definition.

### Chapter 6.1: Checking function arguments

A _public_ function should verify that its arguments are sensible.
This includes, but is not limited to, verifying that:
- non-optional pointer arguments are not NULL and
- numeric arguments are within expected ranges.

Where an argument is not sensible, an error should be returned.

### Chapter 6.2: Extending existing functions

From time to time it is necessary to extend an existing function. Typically this
will mean adding additional arguments, but it may also include removal of some.

Where an extended function should be added the original function should be kept
and a new version created with the same name and an `_ex` suffix. For example,
the `RAND_bytes` function has an extended form called `RAND_bytes_ex`.

Where an extended version of a function already exists and a second extended
version needs to be created then it should have an `_ex2` suffix, and so on for
further extensions.

When an extended version of a function is created the order of existing
parameters from the original function should be retained. However new parameters
may be inserted at any point (they do not have to be at the end), and no longer
required parameters may be removed.

## Chapter 7: Centralized exiting of functions

The goto statement comes in handy when a function exits from multiple
locations and some common work such as cleanup has to be done. If there
is no cleanup needed then just return directly. The rationale for this is
as follows:

- Unconditional statements are easier to understand and follow
- It can reduce excessive control structures and nesting
- It avoids errors caused by failing to updated multiple exit points when the code is modified
- It saves the compiler work to optimize redundant code away ;)

For example:

```c
    int fun(int a)
    {
        int result = 0;
        char *buffer = OPENSSL_malloc(SIZE);

        if (buffer == NULL)
            return -1;

        if (condition1) {
            while (loop1) {
                ...
            }
            result = 1;
            goto out;
        }
        ...
    out:
        OPENSSL_free(buffer);
        return result;
    }
```

## Chapter 8: Commenting

Use the classic "/* ... */" comment markers.  Don't use "// ..." markers.

Comments are good, but there is also a danger of over-commenting. NEVER try
to explain HOW your code works in a comment. It is much better to write
the code so that it is obvious, and it's a waste of time to explain badly
written code. You want your comments to tell WHAT your code does, not HOW.

The preferred style for long (multi-line) comments is:

```c
    /*-
     * This is the preferred style for multi-line
     * comments in the OpenSSL source code.
     * Please use it consistently.
     *
     * Description:  A column of asterisks on the left side,
     * with beginning and ending almost-blank lines.
     */
```

Note the initial hyphen to prevent indent from modifying the comment.
Use this if the comment has particular formatting that must be preserved.

It's also important to comment data, whether they are basic types or
derived types. To this end, use just one data declaration per line (no
commas for multiple data declarations). This leaves you room for a small
comment on each item, explaining its use.

## Chapter 9: Macros and Enums

Names of macros defining constants and labels in enums are in uppercase:

```c
    #define CONSTANT 0x12345
```

Enums are preferred when defining several related constants.  Note, however,
that enum arguments to public functions are not permitted.

Macro names should be in uppercase, but macros resembling functions may
be written in lower case. Generally, inline functions are preferable to
macros resembling functions.

Macros with multiple statements should be enclosed in a do - while block:

```c
    #define macrofun(a, b, c)   \
        do {                    \
            if (a == 5)         \
                do_this(b, c);  \
        } while (0)
```

Do not write macros that affect control flow:

```c
    #define FOO(x)                 \
        do {                       \
            if (blah(x) < 0)       \
                return -EBUGGERED; \
        } while(0)
```

Do not write macros that depend on having a local variable with a magic name:

```c
    #define FOO(val) bar(index, val)
```

It is confusing to the reader and is prone to breakage from seemingly
innocent changes.

Do not write macros that are l-values:

```c
    FOO(x) = y
```

This will cause problems if, e.g., FOO becomes an inline function.

Be careful of precedence. Macros defining constants using expressions
must enclose the expression in parentheses:

```c
    #define CONSTANT 0x4000
    #define CONSTEXP (CONSTANT | 3)
```

Beware of similar issues with macros using parameters. The [GNU cpp manual][8]
deals with macros exhaustively.

## Chapter 10: Allocating memory

OpenSSL provides the following general purpose memory allocators:
`OPENSSL_malloc()`, `OPENSSL_realloc()`, `OPENSSL_strdup()` and `OPENSSL_free()`.
Please refer to the API documentation for further information about them.

## Chapter 11: Function return values and names

Functions can return values of many different kinds, and one of the
most common is a value indicating whether the function succeeded or
failed. Usually this is:

    1: success
    0: failure

Sometimes an additional value is used:

    -1: something bad (e.g., internal error or memory allocation failure)

Other APIs use the following pattern:

    >= 1: success, with value returning additional information
    <= 0: failure with return value indicating why things failed

Sometimes a return value of -1 can mean "should retry" (e.g., BIO, SSL, et al).

Functions whose return value is the actual result of a computation,
rather than an indication of whether the computation succeeded, are not
subject to these rules. Generally they indicate failure by returning some
out-of-range result. The simplest example is functions that return pointers;
they return NULL to report failure.

## Chapter 12:  Editor modelines

Some editors can interpret configuration information embedded in source
files, indicated with special markers. For example, emacs interprets
lines marked like this:

    -*- mode: c -*-

Or like this:

```c
    /*
    Local Variables:
    compile-command: "gcc -DMAGIC_DEBUG_FLAG foo.c"
    End:
    */
```

Vim interprets markers that look like this:

```c
    /* vim:set sw=8 noet */
```

Do not include any of these in source files. People have their own personal
editor configurations, and your source files should not override them.
This includes markers for indentation and mode configuration. People may
use their own custom mode, or may have some other magic method for making
indentation work correctly.

## Chapter 13:  Processor-specific code

In OpenSSL's case the only reason to resort to processor-specific code
is for performance. As it still exists in a general platform-independent
algorithm context, it always has to be backed up by a neutral pure C one.
This implies certain limitations. The most common way to resolve this
conflict is to opt for short inline assembly function-like snippets,
customarily implemented as macros, so that they can be easily interchanged
with other platform-specific or neutral code. As with any macro, try to
implement it as single expression.

You may need to mark your `asm` statement as `volatile`, to prevent GCC from
removing it if GCC doesn't notice any side effects. You don't always need
to do so, though, and doing so unnecessarily can limit optimization.

When writing a single inline assembly statement containing multiple
instructions, put each instruction on a separate line in a separate quoted
string, and end each string except the last with `\n\t` to properly indent
the next instruction in the assembly output:

```c
        asm ("magic %reg1, #42\n\t"
             "more_magic %reg2, %reg3"
             : /* outputs */ : /* inputs */ : /* clobbers */);
```

Large, non-trivial assembly functions go in pure assembly modules, with
corresponding C prototypes defined in C. The preferred way to implement this
is so-called "perlasm": instead of writing real .s file, you write a perl
script that generates one. This allows use symbolic names for variables
(register as well as locals allocated on stack) that are independent on
specific assembler. It simplifies implementation of recurring instruction
sequences with regular permutation of inputs. By adhering to specific
coding rules, perlasm is also used to support multiple ABIs and assemblers,
see [crypto/perlasm/x86_64-xlate.pl][9] for an example.

Another option for processor-specific (primarily SIMD) capabilities is
called _compiler intrinsics_. We avoid this, because it's not very much
less complicated than coding pure assembly, and it doesn't provide the
same performance guarantee across different micro-architecture. Nor is
it portable enough to meet our multi-platform support goals.

## Chapter 14:  Portability

To maximise portability the version of C defined in ISO/IEC 9899:1990
should be used. This is more commonly referred to as C90. ISO/IEC 9899:1999
(also known as C99) is not supported on some platforms that OpenSSL is
used on and therefore should be avoided.

## Chapter 15: Expressions

Avoid needless parentheses.<br/>
For example, do not write
```c
    if ((p == NULL) && (!f(((2 * x) + y) == (z++))))
 ```
but
```c
    if (p == NULL && !f(2 * x + y == z++)).
```

For clarity, always put parentheses when mixing `&&` and `||` operations.<br/>
For example,
 ```c
    if ((a && b) || c)
 ```

Put parentheses around macro bodies that can be used as expressions.<br/>
Put parentheses around uses of macro arguments
(unless they are passed on as-is to a further macro or function).<br/>
For example,
 ```c
#define SQUARE(a) ((a) * (b))
```

In comparisons with constants (including `NULL`)
place the constant on the right-hand side of the comparison operator.<br/>
For example,
```c
    while (i++ < 10 && p != NULL)
```

Do not use implicit checks for
numbers (not) being `0` or pointers (not) being `NULL`.<br/>
For example, do not write
```c
    if (i)
    if (!(x & MASK))
    if (!strcmp(a, "FOO"))
    if (!(p = BN_new()))
```
but do this instead:
```c
    if (i != 0)
    if ((x & MASK) == 0)
    if (strcmp(a, "FOO") == 0)
    if ((p = BN_new()) == NULL)
```

Do not place binary logical operators `&&` and `||` at the end of a line
but put them at the beginning of the following line.<br/>
They may get an extra indentation (+4 characters).<br/>
For example,
```c
    if (long_condition_expression_1
            && condition_expression_2) {
        statement_1;
        statement_2;
    }
```

## Chapter 16: References

[The C Programming Language][3], Second Edition
by Brian W. Kernighan and Dennis M. Ritchie.
Prentice Hall, Inc., 1988.
ISBN 0-13-110362-8 (paperback), 0-13-110370-9 (hardback).

[The Practice of Programming][4]
by Brian W. Kernighan and Rob Pike.
Addison-Wesley, Inc., 1999.
ISBN 0-201-61586-X.

[GNU manuals][5] - where in compliance with K&R and this text - for cpp, gcc,
gcc internals and indent.

[WG14][6] is the international standardization working group for the programming
language C.

[1]: <https://www.kernel.org/doc/Documentation/CodingStyle> "Linux Kernel Coding Style"
[2]: <https://www.kernel.org/pub/linux/kernel/COPYING> "Linux Kernel License"
[3]: <http://cm.bell-labs.com/cm/cs/cbook> "The C Programming Language, Second Edition"
[4]: <http://cm.bell-labs.com/cm/cs/tpop/> "The Practice of Programming"
[5]: <https://www.gnu.org/manual/> "GNU manuals"
[6]: <http://www.open-std.org/JTC1/SC22/WG14/> "International standardization working group for the programming language C"
[7]: <https://github.com/openssl/openssl/blob/master/include/openssl/ossl_typ.h> "include/openssl/ossl_typ.h"
[8]: <https://gcc.gnu.org/onlinedocs/> "GCC online documentation"
[9]: <https://github.com/openssl/openssl/blob/master/crypto/perlasm/x86_64-xlate.pl> "crypto/perlasm/x86_64-xlate.pl"
