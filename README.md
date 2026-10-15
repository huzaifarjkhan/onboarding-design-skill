# onboarding-design

A Claude Code skill for designing first-run onboarding that a new user understands at once and believes is for them, without dark patterns.

It turns an agent into an onboarding designer that:

- walks the existing flow as a first-time user and lists every line that leaves the reader guessing;
- replaces abstract questions with concrete ones and makes every answer change a later screen;
- checks every number and claim against the code or a named source;
- studies how good apps open, learns their patterns, and copies nothing;
- uses conversion-questionnaire patterns (goal, pains, personalised plan, permission priming, processing moment, demo) openly, but within hard honesty limits, and shows the owner the pattern-true version of anything it rejects;
- turns the app's mark into a quiet guide, with motion that still works with animations off;
- keeps one primary button in a fixed place and checks every screen on small and tall phones;
- presents clickable prototypes, alternatives with a recommendation, and a build plan, and iterates on the owner's notes round by round.

## Install

Copy the folder into your skills directory:

```sh
# Claude Code
mkdir -p ~/.claude/skills && cp -r onboarding-design-skill ~/.claude/skills/onboarding-design

# or a shared agent skills folder
mkdir -p ~/.agents/skills && cp -r onboarding-design-skill ~/.agents/skills/onboarding-design
```

The skill triggers on requests such as "redesign our onboarding", "make new users feel this app is for them", "critique this first-run flow" or "plan the permission screens". You can also invoke it by name.

## What is inside

- `SKILL.md` - the practice: the first-time-user test, the process, a flow structure that converts honestly, a take/adapt/leave table for conversion patterns with hard limits, copy rules, brand-mark and motion rules, layout rules, an honesty checklist, and an anonymised worked example from eight real review rounds.

## License

MIT, see `LICENSE`.
