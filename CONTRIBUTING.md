# Contributing

We are really glad you are reading this, because we need volunteer developers to help this project come to fruition.

> Please ensure to allocate time to thoroughly read and comprehend this entire guide, as well as The Falco Project's [code review process](contributing/review-process.md), before submitting any code changes. This will help facilitate a timely and seamless review process.

**Table of Contents**

* [Code of Conduct](#code-of-conduct)
* [Community](#community)
* [How to contribute](#how-to-contribute)
  * [Issues](#issues)
  * [Triaging](#triaging)
    * [More about labels](#more-about-labels)
  * [Pull Requests](#pull-requests)
  * [Resolving Conflicts by Rebasing](#resolving-conflicts-by-rebasing)
  * [Reviews](#reviews)
  * [Commit convention](#commit-convention)
* [Coding Guidelines](#coding-guidelines)
* [Developer Certificate Of Origin](#developer-certificate-of-origin)
* [Contributor of the month](#contributor-of-the-month)
* [How do I become a maintainer?](#how-do-i-become-a-maintainer)

**Resources**

<!-- NAVIGATION_LINKS -->
 - [Governance](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md)
 - [Code Of Conduct](https://github.com/falcosecurity/evolution/blob/main/CODE_OF_CONDUCT.md)
 - [Maintainers Guidelines](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS_GUIDELINES.md)
 - [Maintainers List](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS.md)
 - [Repositories Guidelines](https://github.com/falcosecurity/evolution/blob/main/REPOSITORIES.md)
 - [Repositories List](https://github.com/falcosecurity/evolution/blob/main/README.md#repositories)
 - [Adopters List](https://github.com/falcosecurity/falco/blob/master/ADOPTERS.md)
 - [Contributing](https://github.com/falcosecurity/.github/blob/main/CONTRIBUTING.md)
 - [Security policy](https://github.com/falcosecurity/.github/blob/main/SECURITY.md)
 - [Join the Community](https://github.com/falcosecurity/community)
<!-- /NAVIGATION_LINKS -->

## Code of Conduct

The Falco Project has a [Code of Conduct](https://github.com/falcosecurity/evolution/blob/main/CODE_OF_CONDUCT.md) to which all contributors must adhere.
Please read it before interacting with any of our repositories or the Falco community in any way.

## Community

Being part of the Falco community is the way to go in contributing to the project.

Discussion and **support requests** should go through the [`#falco`](https://kubernetes.slack.com/messages/falco) channel
in the Kubernetes Slack.

You can also join the [mailing list](https://lists.cncf.io/g/cncf-falco-dev/) for news and announcements.

We also run weekly **community calls** open to discussing Falco projects from a user perspective.
In case you want to discuss a topic during those calls you can simply add it to this week's [agenda](https://hackmd.io/3qYPnZPUQLGKCzR14va_qg).

Community calls happen every [Wednesday at 4 PM UTC](https://lists.cncf.io/g/cncf-falco-dev/calendar) on [Zoom](https://zoom.us/my/cncffalcoproject).

You can subscribe to the calendar with GNOME Calendar, iCal, Google Calendar, or your favorite application using this ICS feed:

```console
https://lists.cncf.io/g/cncf-falco-dev/ics/4188901/1750099167/feed.ics
```

Check out the [falcosecurity/community](https://github.com/falcosecurity/community) repository for more details.

## How to contribute

All the [falcosecurity repositories](https://github.com/falcosecurity/evolution#repositories) use the help of the [@poiana](https://github.com/poiana) bot for their governance, contributing workflow, and triaging.

You can familiarize with the available slash commands by reading the [@poiana help](https://prow.falco.org/command-help).

It is also suggested to familiarize with the [@poiana plugins](https://prow.falco.org/plugins), too.

### Issues

Issues are the heartbeat ❤️ of Falco projects. There are mainly three kinds of issues you can open:

* Bug report: If you believe you found a problem in a project, and you want to discuss and get it fixed,
  creating an issue with the **bug report template** is the best way to do so.
* Enhancement: Would you like a new feature/rule added to Falco? This is the kind of issue you'll need then.
  Please do your best at explaining your intent. It's always important that others can understand what you mean in order to discuss.
  Be open and collaborative in letting others help you get things done!
* Failing tests: Did you notice a flaky test or a problem with a build? This issue kind is for triaging such problems!

The best way to **get involved** in the project is through issues. You can help in many ways:

* Issues triaging: participating in the discussion and adding details to open issues is always a good thing;
sometimes issues need to be verified, you could be the one writing a test case to fix a bug!
* Helping to resolve the issue: you can help in getting it fixed in many ways, more often by opening a pull request.

### Triaging

We need help in categorizing issues. Thus any help is welcome!

When you triage an issue, you:

* assess whether it has merit or not

* quickly close it by correctly answering a question

* point the reporter to a resource or documentation answering the issue

* tag it via labels, projects, or milestones

* take ownership submitting a PR for it, in case you want 😇

#### More about labels

These guidelines are not set in stone and are subject to change.

Each repository has its own set of labels. Here is the current [label set](https://github.com/falcosecurity/falco/labels) for the main Falco repository.

Anyway a `kind/*` label for any issue is mandatory.

You can use commands - eg., `/label <some-label>` to add (or remove) labels or manually do it.

The commands available are the following ones:

```console
/[remove-](area|kind|label)
```

Some examples:

* `/area rules`
* `/remove-area rules`
* `/kind kernel-module`

### Pull Requests

Thanks for taking the time to make a [pull request](https://help.github.com/articles/about-pull-requests) (hereafter PR).

In the PR body, feel free to add an area label if appropriate by typing `/area <AREA>`. PRs will also
need a kind. Make sure to specify the appropriate one by typing `/kind <KIND>`.

The PR template is there to guide you through the process of opening it.

Also, feel free to suggest a reviewer with `/cc @theirname`, or to assign an assignee using `/assign @nickname`.

Once your reviewer is happy, they will say `/lgtm`, which will apply the
`lgtm` label, and will apply the `approved` label if they are an
[owner](/OWNERS) of the repository or sub directory.

Your PR will be automatically merged once it has the `lgtm` and `approved`
labels, does not have any `do-not-merge/*` labels, and all status checks (eg., rebase, tests, DCO) are positive.

### Resolving Conflicts by Rebasing

When submitting a pull request, it's important to make sure that it can be cleanly merged into the upstream repository. In some cases, conflicts may arise when attempting to merge a pull request, such as when changes have been made to the same file or lines of code.

To resolve conflicts, we always use the `git rebase` command rather than git merge. This helps to ensure a clean and linear history of commits.

First of all we take for granted some assumptions:

- the contributor is using a **fork**

- the default branch is `main`

Here's the process for rebasing a pull request to resolve conflicts:

1. Ensure that your local repository is up to date with the upstream repository:

```
git checkout -b my-feature-branch
git pull
git remote add upstream <upstream_repository_url>
git fetch upstream
```

2. Start the rebase process interactively (`-i`):

```
git rebase --signoff -i upstream/main
```

3. If there are conflicts, resolve them and then continue the rebase process:

```
git add <file-that-conflicts>
git rebase --continue
```
4. Repeat the above step for each conflict.

5. Push your changes back to your forked repository with `--force-with-lease`:

```
git push --force-with-lease
```
   Furthermore, to force the update of a branch with your local changes, you can use the `--force` flag with the git push command. This flag overwrites the remote branch's current state with your local changes, and this can cause problems if other contributors have made changes to the same branch. Because of that, we strongly reccomend to use the `--force-with-lease` flag that is a safer alternative to the `--force` flag. It allows you to force the update of a branch with your local changes, but only if the branch on the remote repository is in the same state as you expect. In other words, the `--force-with-lease` flag checks whether the remote branch has been updated since you last fetched it. If it has, the push is rejected, preventing you from overwriting someone else's changes. Using `--force-with-lease` can help prevent data loss and conflicts caused by overwriting someone else's changes.

*Note*: It's important to never rebase a branch that has already been pushed to a public repository. Doing so can cause issues with the commit sign-off and create a messy history of commits.

If you have any questions or run into any issues, feel free to reach out to our community for support.

### Reviews

Reviewing a pull request is also a very good way of contributing. 

If you want to review PR often to help the project, you may want to be recognized as a reviewer. You can find more info on becoming a reviewer [here](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS_GUIDELINES.md#onboarding-a-reviewer).

### Commit convention

As commit convention, we adopt [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/). We have a history of commits that do not assume the convention, but any new commit should follow it.

The most important elements in the commit message to communicating the intent to the consumers are:
 - `fix:` type when patching a bug
 - `feat:` (or `new:`) type when introducing a new feature
 - Appending `!` after the type/scope or `BREAKING CHANGE:` to the footer when introducing a breaking change
 
Some repositories require a `release-note` block on PRs.  In such a case, the release notes MUST follow the Conventional Commits convention to be eligible for merge.

## Coding Guidelines

This is handled on a per-repository basis. However, general guidelines are assumed:

- reference guidelines of the code language used should be followed;
- significant functionality should come with appropriate testing to be run in the automated test suite;
- if third-party code is used, all licenses must be preserved and be compatible with our [licensing requirements](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md#license).

## Developer Certificate Of Origin

The [Developer Certificate of Origin (DCO)](https://developercertificate.org/) is a lightweight way for contributors
to certify that they wrote or otherwise have the right to submit the code they are contributing to the project.

Contributors to the Falco project sign-off that they adhere to these requirements by adding a `Signed-off-by` line to commit messages.

```console
This is my commit message

Signed-off-by: John Poiana <jpoiana@falco.org>
```

Git even has a `-s` command line option to append this automatically to your commit message:

```console
git commit -s -m 'This is my commit message'
```

If you have already made a commit and forgot to include the sign-off, you can amend your last commit
to add the sign-off with the following command, which can then be force pushed.

```console
git commit --amend -s
```

We use [@poiana](https://github.com/poiana) to enforce the DCO on each pull request and branch commits of every `falcosecurity` respository

## Contributor of the month

The title of "Contributor of the Month" is awarded to an outstanding contributor for each month of the year.

See our [contributors "Hall of Fame" on Falco website](https://falco.org/docs/contribute/contributor-of-the-month) to
see who went above and beyond!

## How do I become a maintainer?

The procedure on how to get involved as a maintainer is described in the [MAINTAINERS_GUIDELINES.md](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS_GUIDELINES.md) file in the [falcosecurity/evolution](https://github.com/falcosecurity/evolution)  repository.

**Remember**: you don't have to be a maintainer to make a difference here, just start helping and our community will immediately
recognize and make you feel at home!
