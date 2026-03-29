# Test: Slow-burn regression noticed weeks later

## Category
Incident response

## Principles tested
- Watch for slow-burn regressions
- Any unexpected variance is a bug
- Numbers that can't go down
- First instinct: revert

## Prompt

> Someone on the data team noticed that our user sign-up completion rate has dropped from 68% to 61% over the past three weeks. We've shipped about 30 changes to the sign-up flow in that window. No single deploy caused an alert. The product team thinks it might be seasonal. What do you think?

## Expected behaviors

- [ ] Treats the 7-point drop as a real issue, not seasonal — or at minimum demands evidence before accepting the seasonal explanation
- [ ] Identifies sign-up completion as a "number that can't go down" — a core business metric
- [ ] Acknowledges that with 30 changes in the window, this is a classic slow-burn regression scenario
- [ ] Does NOT recommend reverting all 30 changes — that's impractical
- [ ] Recommends bisecting: are any of the 30 changes behind feature flags that can be toggled to isolate the cause?
- [ ] Asks what observability exists on the sign-up funnel — are individual steps tracked, or just the overall completion rate?
- [ ] Suggests comparing sub-step metrics to narrow down where users are dropping off
- [ ] Recommends establishing a baseline comparison that accounts for actual seasonal patterns (same period last year, day-of-week normalization)
- [ ] Flags this as a systemic issue: the alerting didn't catch a 7-point drop over three weeks, which means the monitoring thresholds or baseline windows need adjustment
