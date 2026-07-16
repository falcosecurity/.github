# Security Policy

The Falco Project takes security seriously and appreciates responsible disclosure. This policy describes what we consider a security vulnerability (**based on Falco's threat model**) so reporters and users know what to expect.

It applies across the [falcosecurity](https://github.com/falcosecurity) organization: the same principles guide every repository, though specifics may vary by project.

## Supported versions

Security fixes are typically applied only to the latest release (at least until Falco reaches its first stable major version).

## Falco's threat model

Falco is a **runtime security detection** tool: it observes events from the systems it monitors, evaluates them against a ruleset, and emits alerts. It **detects and notifies; it does not enforce, block, or isolate**. So evading Falco is not the same as defeating an enforcement control.

Two facts shape what counts as a vulnerability:

- **Falco runs as a trusted, privileged component**, configured by the operator, with high privilege (root or an equivalent set of Linux capabilities, kernel instrumentation) on the host it monitors.
- **Detection coverage comes from tunable rules and is expected to evolve.** Falco cannot detect every technique; gaps in rule coverage are detection-content improvements, not vulnerabilities.

### Trust boundaries

- **Trusted (operator-controlled) inputs.** Falco's configuration, rules files, loaded plugins, and any capture files (`.scap`) the operator chooses to replay are all selected by the operator, who already fully controls the host. Malformed or malicious operator-supplied input is a robustness bug, not a vulnerability, because the operator is inside the trust boundary and accepts the risk of what they choose to replay.
- **Untrusted inputs.** The event data Falco ingests from the workloads it monitors (e.g., syscalls produced by potentially malicious processes or containers, and plugin-sourced events that may be attacker-influenced) crosses a trust boundary from the monitored environment into Falco.
- **Artifact distribution.** The rules and plugins (and any other artifact kind) an operator installs are trusted, but their integrity in transit is established by `falcoctl` at install time, not by Falco when it loads them. Which registry to trust, whether to require signatures, and what an index contains are operator choices, inside the trust boundary. A *silent* failure to verify an artifact the operator expected to be verified is a vulnerability.

### What we protect

Falco's value is visibility. Above all, we want to protect against an attacker in the monitored environment ***silently* defeating detection that Falco is designed to deliver** - suppressing or evading the expected signal without the evasion itself being observable.

## What is (and isn't) a security vulnerability

The categories below are **illustrative, not exhaustive**. Every report is assessed on its own merits, and whether an issue warrants a security advisory is ultimately at the maintainers' discretion.

We treat as **vulnerabilities** issues that defeat Falco's security value:

- **Silent detection bypass**: a technique, reachable from the untrusted side, that defeats the integrity of the detection pipeline (engine, drivers, event handling) so that activity Falco should detect produces no alert and the evasion is not otherwise observable. This concerns the integrity of the *mechanism*, not the completeness of rule *content*. A rule that simply does not cover a technique is a content gap.
- **Remote code execution or compromise of Falco**: code execution over, or control of, the Falco process or its components via data or an interface crossing a trust boundary.
- **Privilege escalation through Falco**: a default, supported deployment letting an entity gain privileges it should not have without already holding equivalent access.

On the other hand, we handle as **regular bugs** (often at high priority, but without an advisory):

- **Crashes and denial of service**, including from untrusted event data; a crash is *loud* (termination, restarts, gaps in output), not a silent bypass.
- **Memory-safety issues** whose demonstrated impact is a crash, with no realistic path to code execution or silent bypass.
- **Issues reachable only through operator-controlled input**, which is inside the trust boundary.
- **Local hardening / defense-in-depth** weaknesses that require the attacker to already hold privileges comparable to what the weakness would grant.
- **Gaps in rule coverage** and other detection-content improvements.
- **Issues in test, example, or development-only code** not shipped in a released artifact.

## Reporting a vulnerability

To report a security issue, email [cncf-falco-maintainers@lists.cncf.io](mailto:cncf-falco-maintainers@lists.cncf.io?subject=SECURITY) with the word "SECURITY" in the subject line. [Maintainers](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS.md) will reply with next steps, keep you informed of progress, and may ask for more information.

We credit reporters and use [GitHub Security Advisories](https://help.github.com/en/github/managing-security-vulnerabilities/about-github-security-advisories) to disclose and publish the issues we handle as vulnerabilities. Published Falco advisories are listed [here](https://github.com/falcosecurity/falco/security/advisories?state=published).
