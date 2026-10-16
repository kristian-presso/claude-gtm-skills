# GTM skills for Claude

**B2B go-to-market with Claude: a motion you can run every week, a sourced, dated reason to contact every prospect, account plays across the whole buying group, and sequences that land in the inbox, not spam.**

```bash
/plugin marketplace add kristian-presso/claude-gtm-skills
/plugin install gtm@claude-gtm-skills
```

One department of [claude-skills](https://github.com/kristian-presso/claude-skills), where all departments live in one place. Free, MIT licensed, no sign-up.

Four skills that cover the path from "who should I go after, and in what order?" to "the first messages are drafted and landing in inboxes". Written for people doing the selling themselves: founders, account executives with a named territory, account managers growing a book, consultants. Each works with no integrations; where a tool such as web search helps, the skill uses it if present and falls back to working from what you give it. Run them in order, or use any one on its own.

## Skills

| Skill | Use it when |
| --- | --- |
| [gtm-motion](skills/gtm-motion/SKILL.md) | You want a repeatable motion: which accounts, which signals, which personas, and a weekly routine. Start here. |
| [signal-prospecting](skills/signal-prospecting/SKILL.md) | Finding prospects from public signals (funding, hiring, launches) with a sourced, dated reason to contact each one. |
| [account-play](skills/account-play/SKILL.md) | One account deserves real effort: map who decides, propose two or three use cases, plan a multi-person play and draft the first touches. |
| [outbound-sequences](skills/outbound-sequences/SKILL.md) | Designing an outbound sequence, with a deliverability pre-flight before a single email goes out. |

## Tested, not just written

Every skill is evaluated with Claude Code's built-in `claude plugin eval`: five cases per skill (three it should handle, two near-misses it must leave alone), each run three times with the skill and three times without, graded by a separate model. A skill ships only if Claude does better with it than without it. Results from 16/10/2026:

| Skill | Score with | Without | Gain |
| --- | --- | --- | --- |
| gtm-motion | 0.98 | 0.82 | +0.15 |
| signal-prospecting | 0.92 | 0.65 | +0.27 |
| account-play | 0.95 | 0.68 | +0.27 |
| outbound-sequences | 1.00 | 0.77 | +0.23 |

Small gains mean plain Claude already does well there; those skills earn their place on the cases it gets wrong.

## Install

### Claude Code

On its own, from this repository:

```bash
/plugin marketplace add kristian-presso/claude-gtm-skills
/plugin install gtm@claude-gtm-skills
```

Or with every other department, from the hub:

```bash
/plugin marketplace add kristian-presso/claude-skills
/plugin install gtm@claude-skills
```

Use one or the other, not both, or the skills load twice.

### Claude app

On claude.ai or the Claude desktop app, download this repository as a zip (Code, then Download ZIP), take the folder of the skill you want from `skills/` (the one containing `SKILL.md`), zip that folder on its own and upload it in your skills settings. Each skill works on its own.

## Notes

- Benchmarks and thresholds in these skills (reply rates, sending limits, legal
  penalties) are dated and say where to verify them. Vendor-reported numbers are labelled
  as such.
- The legal summary in `outbound-sequences` is reference, not legal advice.
- `gtm-motion` asks employed sellers whether their employer allows customer data in
  outside AI tools, and runs on public information when it does not.
- `signal-prospecting` and `account-play` use public business information only, cite a
  source and date for every claim, and respect opt-outs. Nothing is sent: every draft is
  held for the seller to approve.

## Re-run the evals and tests

The eval cases live in `evals/`, one folder per skill. From the repository root:

```bash
claude plugin eval . --trust-plugin --scaffold --ablation with-without --runs 3 --no-publish
```

Every push runs the same checks as CI: each skill through the validator, the manifests through `claude plugin validate`:

```bash
for d in skills/*/; do python3 tools/validate_skill.py "$d"; done
claude plugin validate .
```

## Feedback

Two minutes on [this form](https://tally.so/r/7XlJbL?source=gtm) tells me what worked, what broke and what to build next. Every answer gets read. Bugs with steps to reproduce are best as a GitHub issue: if a skill fired when it should not have, did not fire when it should, or produced the wrong thing, tell me what you typed and what happened.

## More departments

This is one of six. [claude-skills](https://github.com/kristian-presso/claude-skills) has all departments in one place: operator discipline, the operator starter, building with Claude, go-to-market, marketing and UK business, installable together or one at a time.

## All of it in one install

These skills also run inside [Corey](https://getcorey.ai), alongside the rest of the library I use to run my business: one install that already knows your business, remembers it between chats and keeps itself up to date. It is free for individuals.

## Licence

[MIT](LICENSE). Take them, fork them, strip the parts you disagree with.

How these were built, and why, is written up at [kristianpapadakis.com/guides](https://kristianpapadakis.com/guides).
