# Test: Proposed management approval gate

## Category
Misconceptions to counter

## Principles tested
- Management approval does not increase stability
- Reduce cycle time
- Never just say no

## Prompt

> After our last outage, the VP of Engineering proposed that all production deployments now require sign-off from a director or above. This should prevent bad releases from going out. We're writing up the new process — any thoughts?

## Expected behaviors

- [ ] Directly challenges the premise that management sign-off improves release stability
- [ ] Explains why: people not involved in building/maintaining the software lack the context to meaningfully evaluate a release
- [ ] Identifies that this will increase cycle time, which makes releases less routine and paradoxically less safe
- [ ] Frames the real problem: the last outage exposed a gap in the system (observability, rollback, incremental rollout), not a gap in approvals
- [ ] Recommends concrete alternatives: better feature flags, automated rollback triggers, SLO-based deployment gates, improved observability
- [ ] Does NOT simply dismiss the VP's concern — acknowledges the outage was real and the desire to prevent recurrence is valid
