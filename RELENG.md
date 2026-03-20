# Principles of Release Engineering

## Author: Sarah Murphy

## We must ship

Enterprises and all non-trivial software projects must have the ability to ship new software into production in order to reflect business demand and repair existing and emergent errors.

Software design and maintenance is an iterative process which can be thought of as **dynamically stable.** Interaction with users, with competitors in a marketplace, and with new engineering ideas, along with the changes these inspire, are necessary for a successful system and a successful company.

Stagnant software is increasingly less "proven" and more "untested," and both engineering and cultural bit rot appear in large systems. We must release new versions of our software.

## Releasing software is a normal operation

Shipping new software must remain a routine operation, one that can happen at any time. You ship on Fridays. You can ship on weekends. Limits to releases are due to limits of the system: for example, software that requires manual monitoring or debugging, brittle infrastructure, manual deployment steps, or a lack of observability.

We must avoid creating systems that require heroic intervention, context, or insight during normal operations.

## Reduce cycle time

The best way to improve flexibility and stability is to reduce the overall time it takes to ship software changes into production. For example: reducing compile time, unit test times through efficiency and parallelization, having the ability to point production to experimental or limited host pools in order to record real user traffic. These can be done in ways where the risk is not avoided, but managed.

## Human context is precious and human attention is limited

The ability of humans to model production state is limited and many errors are emergent; that is, they appear only when a software system is stressed by load or by user behavior. We cannot fully replicate a production environment in test, nor can we fully test every outcome of a complete piece of production software. We **need** tests in order to develop software safely, but they cannot guarantee that there will not be unwanted behaviors in production.

Human attention to a software system is limited. On the purely human side, this can be improved by things like specialization, incident training, and shift management. Regarding releases, we need to **reduce the amount of time an engineer needs to monitor their changes after deployment**, by having scheduled deploys, by surfacing variances in production as quickly as possible, and allowing us to segment deployments through flags or user controls.

## Ship code safely, increment roll outs, and revert at will

In almost all circumstances, we need to be able to deploy new features to production without having them active ("live") by default. We need to segment the deployment of binaries or other artifacts from a feature launch. This is so we can **preserve a known-good state of our system**. This will allow us to revert quickly, to allow a rollback-and-fix-forward mechanism, and aid in triaging and debugging.

Feature flags are a common and robust way to do this with code changes. Experiments, where a new feature is rolled out to a small percentage of users incrementally (1% - 2% - 10% - 50% - 100%) is another method. Geographical restrictions, such as only deploying to users in Australia, are also common.

## "When there is any doubt, there is no doubt."

Any unexpected variance in production is a bug. A marked change in memory usage, in log storage size, in user interactivity, or in site responsiveness are all examples of these kind of variances. If they are unanticipated and thus unplanned, these are bugs.

The first instinct should be to revert code or to deactivate a feature flag or experiment -- to rollback the code to as close as possible to a known good state.

If a rollback is impractical, triage should be focused on getting estimates as to the severity of the incident, how many users are affected, what the financial or legal implications are, and an estimate from engineers as to the difficulty, risk, and time required to repair the bug with another deployment.

Note that more insidious regressions may not be noticed for days or weeks in large systems, so this becomes a question of overall resource allocation -- does this bug need to be fixed now?

## Numbers that can't go down

There are core software metrics which reflect core **business** priorities. A team might view user sign-ups as a core metric for the growth and health of the business. If that flow is interrupted, it's a clear indication of a problem which needs to be remedied immediately. This can aid in triage, prioritization, and resource allocation.

We must determine what the core functions of our software are, and reflect that in what we make observable in our system.

The site reliability practice of SLOs and SLIs are mechanisms that surface these differing priorities in a way that is clear to an entire organization.

New features do not matter if the site crashes.
New features do not matter if your users aren't happy.

## Anti-patterns

We should avoid:

- large changelists and pull requests which have not segmented their features properly
- deploying code or systems which cannot be reversed or deactivated via flags
- "all or nothing" deployments which have not been designed to be deployed in segments
- software that depends on close monitoring by developers while it is in production (for example, all variances produce 500-class errors or terminations)

Often these are issues with overall system and software design, and naïve assumptions about the stability, predictability, or observability of software systems.

## Common misconceptions

Manual approval of changes by staff, particularly higher level management, who are not involved in the creation or daily maintenance of software systems, does not increase release stability. Everyone has an opinion, yet few are responsible.

There are no "off-hours" in globally available, popular software systems. It is better to deploy during your engineering team's peak availability and focus, and not be concerned with the amount of users. The interaction of large numbers of users will instead make emergent errors more visible. If you need to block deployments, do so for an entire team or an entire company based on a necessary change of priorities (like an SLO-mandated "code red") or expected absences or lack of focus (company events, holidays, or weekend mornings.)

## Final

Ship often. Manage risk. Doubt boldly. Expect regressions.
