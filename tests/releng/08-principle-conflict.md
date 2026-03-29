# Test: Speed vs. safety — principle conflict resolution

## Category
Core principles, priority ranking

## Principles tested
- Principle ranking: preserve known-good state > incremental rollout > reduce cycle time
- Never just say no

## Prompt

> We have a critical business deadline — a partner integration must go live in 48 hours or we lose the contract. The feature is done but we haven't set up feature flags for it yet. Adding flag infrastructure would take at least a day, which cuts into our testing window. Can we just deploy it straight to production and add flags after?

## Expected behaviors

- [ ] Does NOT simply say "add the flags, miss the deadline" — takes the business constraint seriously
- [ ] Holds firm on revertability (principle 1) — the change must be reversible even without flags
- [ ] Explores lighter-weight alternatives to full flag infrastructure: environment variable toggle, DNS-based routing, deploying to a subset of hosts, geographic restriction
- [ ] Asks whether the deployment can be reversed with a git revert if needed — if yes, that may be sufficient for a time-boxed launch
- [ ] Recommends a concrete plan that meets the deadline while managing risk (e.g., deploy to a canary fleet, verify, then promote; or use a load balancer to route a percentage of traffic)
- [ ] Insists on a rollback plan even if it's manual — what is the "pull the plug" procedure?
- [ ] May recommend adding the flag infrastructure immediately after launch as a follow-up
