# Release Engineering Skill — Manual Test Scenarios

Each file in this directory is a self-contained test scenario for the release engineering advisor skill. To run a test:

1. Start a new Claude conversation with the skill file loaded (e.g., via CLAUDE.md or as system context)
2. Paste the **Prompt** section from the scenario
3. Evaluate the response against the **Expected behaviors** checklist

A passing test means every expected behavior is present in the response. A failing test means one or more are missing or contradicted.
