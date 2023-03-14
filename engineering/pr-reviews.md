---
description: How we review Pull Requests at Cal.com
---

# ✅ PR Reviews

### Auto-update and auto-merge

**How we use kodiak bot to auto-update and auto-merge approved PR's.**

You will notice some PR's have the **`autoupdate`** and **`automerge`** tags assigned, those make sure that the PR is fresh and rebased automatically to main or whatever branch is based too, and the automerge one, will automatically merge the PR once it has the minimum required approval reviews (1).

{% hint style="danger" %}
Please do a thorough review and test the code, before approving, as it will get probably auto-merged once you do so.&#x20;
{% endhint %}

We wouldn't want to merge stuff that hasn't been tested properly to main, and the PR might have one of such tags that would do so, so please don't approve before running the code and testing the bug has been fixed or the feature works as expected.

### What to look for?

You can rely on the tools we already have, like all `github checks` being green on `types`, `eslint`, `e2e tests` and other tools.

First of all, if you're dealing with any bug fix, make sure that you're able to reproduce the fix (and maybe the prior bug in main too), and that there are not any other edge cases that the author might have missed.

Read the code changes, and try to think if the logic updates makes sense, or is there any other changes that could also improve it. Always try to simplify, don't overdo it though. Don't extract code until necessary.

If you see anything you think could be improved, make a comment on that line, open a discussion about it and the author will resolve it either fixing it or providing their reasoning for their option.

### Drafts

If your PR is not ready yet for review, please keep the  `draft` tag in it until it's ready, once you're happy with your work, move it out of draft and ask for review either to a teammate specifically (if you know they're already familiar with that part of the codebase, or else) or you can tag `calcom/core` or `calcom/reviewers` team which will pick someone randomly for the team and notify them.

Likewise, don't review any PR's that are on `draft` status, as they might not be yet ready for your excellent feedback!

It's possible that either as part of `calcom/core` or `calcom/reviewers` team, or because a teammate has tagged you personally, they'll show up in your github review requests page.

[https://github.com/pulls/review-requested](https://github.com/pulls/review-requested)

###
