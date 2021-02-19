# How to contribute

We are really glad you are reading this, because we need volunteer developers to help this project come to fruition.

- [How to contribute](#how-to-contribute)
  - [Code of Conduct](#code-of-conduct)
  - [Community](#community)
  - [Contributing](#contributing)
    - [Contributor of the month](#contributor-of-the-month)
    - [Issues](#issues)
    - [Triaging](#triaging)
      - [More about labels](#more-about-labels)
    - [Pull Requests](#pull-requests)
    - [Reviews](#reviews)
    - [Commit convention](#commit-convention)
      - [Rule type](#rule-type)
  - [Coding Guidelines](#coding-guidelines)
  - [Developer Certificate Of Origin](#developer-certificate-of-origin)
  - [How do I become a maintainer?](#how-do-i-become-a-maintainer)

## Code of Conduct

Falco projects have a
[Code of Conduct](CODE_OF_CONDUCT.md)
to which all contributors must adhere, please read it before interacting with the repository or the community in any way.

## Community

Discussion and **support requests** should go through the `#falco` channel in the [Kubernetes slack](https://slack.k8s.io).

[Join the **mailing list**](https://lists.cncf.io/g/cncf-falco-dev/) for news, announcements, and a Google calendar invite for our Falco open source meetings.

We also run weekly **community calls** which are open calls to discuss Falco projects from an user perspective. In case you want to discuss a topic during those calls you can simply add it to
this week's [agenda](https://hackmd.io/3qYPnZPUQLGKCzR14va_qg).

[Wednesdays at 4PM UTC](https://lists.cncf.io/g/cncf-falco-dev/calendar) on [Zoom](https://zoom.us/my/cncffalcoproject).

You can subscribe to the calendar with GNOME Calendar, iCal, Google Calendar, or your favorite application using this ICS feed:

```console
https://lists.cncf.io/g/cncf-falco-dev/ics/4188901/1750099167/feed.ics
```

## Contributing

All the `falcosecurity` projects use the help of the @poiana bot for their governance, contributing workflow, and triaging.

You can familiarize with the available slash commands by reading the [@poiana help](https://prow.falco.org/command-help).

It is also suggested to familiarize with the [@poiana plugins](https://prow.falco.org/plugins), too.

### Contributor of the month

The title of “Contributor of the Month” is awarded to an outstanding contributor for the month of the year.

See our [contributors "Hall of Fame" on the Falco website](https://falco.org/docs/contribute/contributor-of-the-month) to
see who went above and beyond!

### Issues

Issues are the heartbeat ❤️ of the Falco projects, there are mainly three kinds of issues you can open:

- Bug report: you believe you found a problem in a project and you want to discuss and get it fixed,
creating an issue with the **bug report template** is the best way to do so.
- Enhancement: any kind of new feature need to be discussed in this kind of issue, do you want a new rule or a new feature? This is the kind of issue you want to open. Be very good at explaining your intent, it's always important that others can understand what you mean in order to discuss, be open and collaborative in letting others help you getting this done!
- Failing tests: you noticed a flaky test or a problem with a build? This is the kind of issue to triage that!

The best way to get **involved** in the project is through issues, you can help in many ways:

- Issues triaging: participating in the discussion and adding details to open issues is always a good thing,
sometimes issues need to be verified, you could be the one writing a test case to fix a bug!
- Helping to resolve the issue: you can help in getting it fixed in many ways, more often by opening a pull request.

### Triaging

We need help in categorizing issues. Thus any help is welcome!

When you triage an issue, you:

- assess whether it has merit or not

- quickly close it by correctly answering a question

- point the reporter to a resource or documentation answering the issue

- tag it via labels, projects, or milestones

- take ownership submitting a PR for it, in case you want 😇

#### More about labels

These guidelines are not set in stone and are subject to change.

Anyway a `kind/*` label for any issue is mandatory.

This is the current [label set](https://github.com/falcosecurity/falco/labels) we have.

You can use commands - eg., `/label <some-label>` to add (or remove) labels or manually do it.

The commands available are the following ones:

```console
/[remove-](area|kind|priority|triage|label)
```

Some examples:

- `/area rules`
- `/remove-area rules`
- `/kind kernel-module`
- `/label good-first-issue`
- `/triage duplicate`
- `/triage unresolved`
- `/triage not-reproducible`
- `/triage support`
- ...

### Pull Requests

Thanks for taking time to make a [pull request](https://help.github.com/articles/about-pull-requests) (hereafter PR).

In the PR body, feel free to add an area label if appropriate by typing `/area <AREA>`, PRs will also
need a kind, make sure to specify the appropriate one by typing `/kind <KIND>`.

The PR template is there to guide you through the process of opening it.

Also feel free to suggest a reviewer with `/cc @theirname`, or to assign an assignee using `/assign @nickname`.

Once your reviewer is happy, they will say `/lgtm` which will apply the
`lgtm` label, and will apply the `approved` label if they are an
[owner](/OWNERS) for the project.

Your PR will be automatically merged once it has the `lgtm` and `approved`
labels, does not have any `do-not-merge/*` labels, and all status checks (eg., rebase, tests, DCO) are positive.

### Reviews

Reviewing a pull request is also a very good way of contributing
### Commit convention

As commit convention, we adopt [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/), we have an history
of commits that do not adopt the convention but any new commit should follow it.

Pull requests towards projects using the `release-note` plugin MUST have release note following such convention to be eligible for merge.

#### Rule type

Besides the classic types, we adopt a type for rules, `rule(<scope>):`.

Example:

```console
rule(Write below monitored dir): make sure monitored dirs are monitored.
```

Each rule change must be on its own commit, if a change to a macro is done while changing a rule they can go together but only one rule per commit must happen.

If you are changing only a macro, the commit will look like this:

```console
rule(macro user_known_write_monitored_dir_conditions): make sure conditions are great
```

Notice this section applies to `falcosecurity/falco` only.

## Coding Guidelines

This is handled on a per-repository basis.

## Developer Certificate Of Origin

The [Developer Certificate of Origin (DCO)](https://developercertificate.org/) is a lightweight way for contributors to certify that they wrote or otherwise have the right to submit the code they are contributing to the project.

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

We use a [poiana](https://github.com/poiana) to enforce the DCO on each pull
request and branch commits of every `falcosecurity` project.

## How do I become a maintainer?

The procedure on how to get involved as a maintainer is described in the [GOVERNANCE.md](GOVERNANCE.md) file in this repository.

Becoming a maintainer is a time investment, you will need to commit to have time to be available for the project.

**Remember**: you don't have to be a maintainer to make a difference here, just start helping and our community will immediately recognize and make you feel at home!
