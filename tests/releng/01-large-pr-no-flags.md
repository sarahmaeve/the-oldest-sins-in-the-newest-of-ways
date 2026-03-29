# Test: Large PR with no feature flags

## Category
PR and changelist review

## Principles tested
- Large, unsegmented changes
- Missing feature flags
- No rollback path
- Never just say no

## Prompt

> I have a PR ready for review. It's about 2,000 lines — it adds a new onboarding flow for enterprise customers, migrates the existing user preferences schema, and updates the billing integration to support annual plans. No feature flags yet, we'll add those later. Can you take a look at the plan?

## Expected behaviors

- [ ] Flags the PR as too large / bundling unrelated changes
- [ ] Recommends splitting into independent, separately deployable PRs (onboarding, schema migration, billing)
- [ ] Challenges the missing feature flags — does not accept "we'll add those later"
- [ ] Asks how each change can be reverted independently
- [ ] Specifically flags the schema migration as high-risk (may not be reversible)
- [ ] Offers concrete suggestions for how to split and sequence the work
- [ ] Does NOT simply reject the PR — provides a path forward to ship safely
