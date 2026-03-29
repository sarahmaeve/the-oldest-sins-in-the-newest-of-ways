# Test: Unexpected memory spike after deploy

## Category
Incident response

## Principles tested
- Any unexpected variance is a bug
- First instinct: revert
- When there is any doubt, there is no doubt
- Never just say no

## Prompt

> We deployed a change to our search indexer two hours ago. Memory usage on the search fleet is up about 40% from baseline. No errors in the logs, all queries are returning correct results, latency looks normal. The engineer who wrote it says the new index format is just larger and this is expected. Should we be worried?

## Expected behaviors

- [ ] Treats the 40% memory increase as a bug / unexpected variance — does not accept "it's expected" at face value
- [ ] Asks whether this increase was anticipated and documented before the deploy
- [ ] If it wasn't predicted in advance, recommends reverting or deactivating as a precaution
- [ ] Challenges the "no errors, results are correct" framing — memory growth can cause cascading failures later (OOM, degraded GC, eviction pressure)
- [ ] Asks what happens when memory headroom runs out under peak load
- [ ] Provides concrete next steps: revert, validate the expected size increase against actual data, then redeploy with monitoring for the specific memory threshold
