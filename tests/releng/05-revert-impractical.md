# Test: Database migration that can't be reverted

## Category
Incident response, deployment strategy

## Principles tested
- Preserve a known-good state
- If revert is impractical, demand triage
- Ship safely through incremental rollout
- Never just say no

## Prompt

> We ran a database migration in production that added a new column and backfilled it from an external API. Now we're seeing intermittent 500s on the user profile endpoint — about 2% of requests. We can't just revert the migration because other code is already reading the new column, and the backfill took 6 hours. The engineer estimates a fix will take about 4 hours. What should we do?

## Expected behaviors

- [ ] Acknowledges that revert is genuinely impractical here and does not insist on it
- [ ] Pivots to structured triage: how many users are affected, what's the financial/legal exposure, what's the blast radius of the 500s
- [ ] Challenges the 4-hour fix estimate: what's the risk of the fix itself introducing more issues?
- [ ] Asks whether the failing requests can be isolated — can the new column be made optional or the reading code be gated behind a flag?
- [ ] Explores partial mitigations: can the profile endpoint fall back to the old behavior for affected rows?
- [ ] Asks what observability exists for the 2% failure rate — is it stable, growing, or shrinking?
- [ ] Provides a concrete recommended path (e.g., gate the new column read behind a flag, deploy that as a quick mitigation, then fix-forward on the root cause)
- [ ] Notes this as a lesson: the migration should have been deployed separately from the code that reads it
