Record of votes
===============

Each formal vote of the OpenSSL Technical Comittee (OTC) is
recorded here in a separate file.

Naming of the files
===================

The vote files are named `yyyymmdd-vote-short-id.txt` where the `yyyymmdd`
is the date when the vote was proposed and the `vote-short-id` is a short
mnemonic identifier of the vote such as `voting-procedure` or `accept-pr-1234`
or similar.

Formatting of the files
=======================

The files are formatted as follows:

```
Topic: .
Proposed by: .
Issue link: https://github.com/openssl/technical-policies/issues/...
Public: yes
Opened: yyyy-mm-dd
Closed: yyyy-mm-dd
Accepted:  yes/no  (for: X, against: Y, abstained: Z, not voted: T)

  OTC Member A  [  ]
  OTC Member B  [  ]
  ...
```

The individual member votes are recorded as `[+1]` a vote in favour, `[-1]`
a vote against, `[+0]` an abstention with an inclination in favour,
`[ 0]` a neutral abstention, `[-0]` an abstention with an inclination
against, and `[  ]` meaning not voted.
