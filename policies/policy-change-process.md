Policy change process policy
============================

This policy represents the way how any additions or changes to the existing
policies are proposed, edited, finalized, and approved.

Policy change proposal
----------------------

The policy changes or additions are submitted as pull requests in the
technical-policies repository on GitHub OpenSSL project.

Each policy is placed in an individual file in the MarkDown format in the
policies subdirectory.

Any policy change proposal can modify any number of policies as required.

Any policy change proposal SHOULD have a single topic.

The description of the pull request SHOULD provide overview of the changes
and the reasons why the change is proposed.

After the pull request is created the author SHOULD announce the policy
change proposal on the openssl-project mailing list.

The editorial process
---------------------

Adjustments of the change proposal happens via the normal GitHub pull request
review interaction. The pull request MUST be opened for at least two weeks
after the initial announce of the change proposal.

The OTC SHOULD discuss the proposal during a meeting.

The OTC SHOULD seek for consensus when finalizing the policy change however
it is not an absolute requirement.

The editorial process is fully public in the sense that anyone can add
comments to the pull request and see comments made by others.

Withdrawal
----------

To withdraw the change the submitter of the pull request just closes the
pull request.

Approval
--------

The policy change is approved by means of a regular OTC vote. If the vote
passes, the policy change is approved, rejected otherwise.

Approval is marked by labelling the pull request with `Approved` label.

Rejection is marked by labelling the pull request with `Rejected` label
and closing the pull request without merging.

If the policy change is approved, the pull request is merged to the
master branch of the technical-policies repository.
