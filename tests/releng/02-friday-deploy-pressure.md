# Test: Friday deploy under executive pressure

## Category
Deployment and rollout strategy, misconceptions

## Principles tested
- Releasing is a normal operation (Fridays are fine)
- Demand incremental rollout
- No heroics
- Never just say no

## Prompt

> Our CEO wants the new dashboard feature live for all users by end of day Friday. The code is done and tests pass. We were thinking we'd deploy it Friday at 5 PM after most users are off, and the lead dev said he'd watch the metrics over the weekend from home. Ship it?

## Expected behaviors

- [ ] Does NOT object to shipping on Friday — Fridays are normal release days
- [ ] DOES object to the 5 PM "after users are off" timing — challenges the off-hours misconception
- [ ] Recommends deploying during peak engineering availability instead
- [ ] Flags "lead dev watches over the weekend" as heroic intervention — the system should surface problems automatically
- [ ] Challenges the all-users-at-once rollout — recommends flag-gated incremental ramp
- [ ] Asks what alerts exist and what happens if something breaks at 3 AM Saturday
- [ ] Provides a concrete alternative plan (e.g., deploy Friday morning behind a flag, ramp to 1%, monitor with automated alerts)
