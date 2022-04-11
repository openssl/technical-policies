Policy on Proposing Technical Policy Changes
============================================

This policy represents the way that any additions or non-trivial changes to the
existing policies are proposed, edited, finalized, and approved.

For minor changes see the [Exceptions](#exceptions) section.

Policy Change Proposal
----------------------

The policy changes or additions are submitted as pull requests in the
technical-policies repository on GitHub OpenSSL project. Anyone with
a GitHub account can submit a policy change proposal pull request.

Each policy is placed in an individual file in Markdown format in the
policies subdirectory.

Any policy change proposal can modify any number of policies as required.

Any policy change proposal SHOULD have a single topic.

The description of the pull request SHOULD provide an overview of the changes
and the reasons why the change is proposed.

After the pull request has been created the author MUST announce the policy
change proposal on the openssl-project mailing list.

The Review Process
---------------------

If the submitter is not a member of OTC, an OTC member is selected to watch
over the review process and propose the final approval vote.

Adjustments to the change proposal happen via the normal GitHub pull request
review interaction. The pull request MUST be opened for at least two weeks
after the initial announcement of the change proposal.

The OTC SHOULD discuss the proposal during a meeting.

The OTC SHOULD seek consensus when finalizing the policy change however
it is not an absolute requirement.

The review process is fully public in the sense that anyone can add
comments to the pull request and see comments made by others.

Withdrawal
----------

To withdraw the change the submitter of the pull request just closes the
pull request.

The Approval Process
--------------------

When there are no further changes proposed on the pull request and the
minimum time for which it must be open passes the pull request is marked
with the `Ready To Vote` label. The pull request is frozen for any changes
other than typo fixes or minor formatting changes after that.

The policy change is approved by means of a regular OTC vote. If the vote
passes, the policy change is approved, otherwise it is rejected.

Approval is marked by labelling the pull request with the `Accepted` label.

Rejection is marked by labelling the pull request with the `Rejected` label
and closing the pull request without merging.

If the policy change is approved, the pull request is merged to the
master branch of the technical-policies repository.

Exceptions
----------

Minor policy edits that do not change the existing meaning of the edited
policies do not require this voting process. These edits are done via
pull requests that are approved by two OTC members where neither of them
is the author of the submission. The pull request should be labelled with
the `minor edit` label.

Approved submissions shall only be applied after a 24-hour delay from the
approval.
