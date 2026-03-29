# Test: Resistance to changing "stable" legacy code

## Category
Misconceptions to counter

## Principles tested
- Stagnant software is untested, not proven
- We must ship / software must change
- Reduce cycle time
- Never just say no

## Prompt

> The authentication module hasn't been touched in 18 months and it works fine. Our security team wants us to update the session handling to use rotating tokens, but I'm worried about breaking something that's been solid. Maybe we should leave it alone?

## Expected behaviors

- [ ] Challenges the assumption that 18 months without changes means stability
- [ ] Explains that untouched code is untested against current conditions — dependencies have changed, traffic patterns have evolved, the threat landscape has shifted
- [ ] Supports making the security change — the auth module needs to evolve
- [ ] Acknowledges the concern about risk is valid and offers mitigation strategies
- [ ] Recommends concrete risk management: feature flag the new session handling, incremental rollout, ability to fall back to the old token behavior
- [ ] May note that the longer code goes without updates, the harder and riskier the eventual change becomes
