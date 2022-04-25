The Public Voting Procedure of OTC
==================================

The following regulations complement the [OTC Voting Procedures] stated
in the project bylaws. This policy affects only public votes.

[OTC Voting Procedures]: https://www.openssl.org/policies/omc-bylaws.html#otc-voting

Vote Proposal
-------------

The votes are proposed in pull requests and issues of the technical-policies
repository on GitHub OpenSSL project.

The vote regarding a policy change proposal is recorded directly in the
pull request of the policy change proposal.

Any other votes are recorded as separate issues in the repository.

All votes governed by this procedure must be announced through an
e-mail to the [OpenSSL Project mailing list].
The announcement email must contain a hyperlink to the GitHub issue
or pull request where the vote is carried out.

Casting the Votes
-----------------

The individual members of [OTC] cast their votes directly in the issue or
pull request where the vote was proposed.

When the votes are cast during an OTC meeting, the person responsible for
taking the meeting minutes or the proposer of the vote copies the votes
cast during the meeting into the issue.

The Final Vote Records
----------------------

After the vote is closed the proposer of the vote records the final outcome
and individual member votes in a separate file in the votes subdirectory of
the repository. The commit with the vote record is pushed directly into
the master branch of the repository. No pull request is needed.

The file is formatted as follows:

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

The vote files are named `vote-yyyymmdd-vote-short-id.txt` where the `yyyymmdd`
is the date when the vote was proposed and the `vote-short-id` is a short
mnemonic identifier of the vote such as `voting-procedure` or `accept-pr-1234`
or similar.

Closing the Issue
-----------------

The issue or pull request where the vote was proposed is then labelled with
the `Accepted` or `Rejected` label based on whether the vote was accepted or
not.

The issue is then closed. In case the vote is in a pull request for a policy
change and the vote passed the pull request for the policy change is squashed
and merged into the repository.

[OTC]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#otc
[OpenSSL Project mailing list]: https://mta.openssl.org/mailman/listinfo/openssl-project
