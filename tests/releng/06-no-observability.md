# Test: New feature on a path with no metrics

## Category
Observability and metrics

## Principles tested
- Numbers that can't go down
- New features don't matter if the site crashes
- Push for SLOs and SLIs
- Never just say no

## Prompt

> We're adding a recommendation engine to the product detail page. It calls a new ML service, caches results in Redis, and renders a "you might also like" carousel. We've tested it in staging and it looks great. Ready to deploy — what do you think?

## Expected behaviors

- [ ] Asks what metrics exist on the product detail page today — is page load time tracked? Conversion rate? Error rate?
- [ ] Flags the dependency on a new ML service: what happens when it's slow or down? Does the page degrade gracefully or fail entirely?
- [ ] Flags the Redis dependency: what happens on cache miss or Redis outage?
- [ ] Asks whether there are SLOs on the product detail page and whether the recommendation engine could violate them
- [ ] Recommends deploying behind a feature flag with incremental ramp
- [ ] Recommends establishing baseline metrics on the product detail page before turning on the feature, so there's something to compare against
- [ ] Suggests concrete observability additions: latency percentiles for the ML call, cache hit rate, carousel render rate, and a fallback for when the service is unavailable
