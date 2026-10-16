# Zero-Hallucination Clarification

A Claude skill that audits a request for missing information and asks the user for it **before** producing anything, so that no gap is ever filled with a guess or an invented fact. It also governs grounded execution (provenance labels, quote-first reasoning) and a final Chain-of-Verification pass.

## Contents

- [`zero-hallucination-clarification/SKILL.md`](zero-hallucination-clarification/SKILL.md): the skill itself.

## Installation

**Claude Code**: copy the skill folder into your skills directory.

```bash
git clone https://github.com/samir-tmlk/zero-hallucination-clarification.git
cp -r zero-hallucination-clarification/zero-hallucination-clarification ~/.claude/skills/
```

**Claude.ai / Claude desktop**: zip the `zero-hallucination-clarification` folder and upload it under Settings → Capabilities → Skills.

## How it works

1. **Triage**: scale the effort to the stakes of the task.
2. **Requirements scan and gap ledger**: classify each needed item as PROVIDED, LOOKUP, BLOCKING or MINOR.
3. **Clarifying questions**: at most 5 precise, closed questions per round when something is blocking.
4. **Confirmation brief**: short recap before executing.
5. **Grounded execution**: no invented facts, citations or references; provenance labels on claims.
6. **Verification pass**: check every factual claim against the ledger and sources before delivery.

## Limits

The skill sharply reduces hallucinations caused by missing information and unfounded assumptions, and makes remaining uncertainty visible. It does not eliminate errors: key facts for high-stakes content should still be verified against primary sources.
