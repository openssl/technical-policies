OpenSSL Technical Policies
==========================

This repository contains the technical policies and procedures established by
the OTC in accordance with the [project bylaws] and the requirements specified
by the OMC.

[project bylaws]: https://www.openssl.org/policies/omc-bylaws.html

The policies
------------

The policies are stored in the [policies](./policies) subdirectory, each in
a separate markdown file called `policy-name.md` where `policy-name` is a short
memorable description of the policy such as `voting-procedure`, `design-process`,
or similar.

New policies or changes to existing policies are proposed and discussed in pull
requests and issues of this repository, and finally merged after an approval by
an OTC vote. The details are regulated by the [policy-change-process] and the
[voting-procedure] policy.

[policy-change-process]: ./policies/policy-change-process.md
[voting-procedure]: ./policies/voting-procedure.md


The voting records
------------------

Each formal vote of the OpenSSL Technical Comittee (OTC) is in the [votes](./votes)
subdirectory in a separate file.

The voting records are named `yyyymmdd-vote-name.txt` where the `yyyymmdd` is the
date when the vote was proposed and the `vote-name` is a short memorable
description of the vote such as `voting-procedure`, `accept-pr-1234`, or similar.


The voting records are formatted as follows:

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
