---
name: onboarding-design
description: >-
  Design (and plan the build of) a first-run onboarding flow for a mobile or web app from a first-time user's point of view: concrete questions instead of abstract ones, a goal asked first and used on every later screen, honest numbers with sources, a personalised plan as the payoff, permissions asked after value, a brand mark that guides instead of decorating, calm motion with a reduced-motion state, a fixed primary button, and fit checks on small and tall phones. Use when asked to design, redesign, critique, simplify or improve onboarding, a first-run or welcome flow, a signup questionnaire, permission priming, or "make new users feel this app is for them"; also when reviewing someone else's onboarding or turning owner feedback on onboarding into the next round.
---

# Onboarding design

A practice for designing onboarding that a first-time user understands at once and believes is for them, without tricks.
It was distilled from eight review rounds on a real app's onboarding (see "Worked example" at the end) and is app-agnostic.

## Start here (any app)

Before designing anything, learn the app from its own sources. Fill in this sheet and keep it in the review artifact:

| Placeholder | What to find | Where to look |
| --- | --- | --- |
| `{APP}` | Name and one-sentence job ("keeps chosen apps closed for a set time") | README, store listing, the app's own welcome copy |
| `{CORE_ACTION}` | The one thing a user does again and again | Main screen, primary button, analytics event names |
| `{CORE_NOUN}` | The app's own word for that thing (session, challenge, workout, lesson) | UI strings; count each candidate and use the winner consistently |
| `{MARK}` | Brand mark or mascot, and its real asset files | Launcher icon sources, design folder, vector drawables / SVG / asset catalogs |
| `{GOALS}` | 4-7 outcomes users come for | Store reviews, support mail, the product's own marketing, competitor listings |
| `{PAINS}` | What gets in the way, in users' words | Same, plus your own walk of the problem |
| `{PLAN_UNIT}` | What a plan is made of (a schedule window, a weekly target, a reading list) | Data models and the feature that stores it |
| `{FREE_AND_PAID}` | What costs money, what never does | Billing code, pricing pages |
| `{PERMISSIONS}` | Every permission the core action needs, what each actually sees or does | Manifest / Info.plist / entitlements, the code that uses each one, store declarations |
| `{TOKENS}` | Colours, type, spacing, radii, motion durations and curves, haptics | The design system or theme files |
| `{FIRST_RUN}` | Today's onboarding: every screen, string, branch and stored answer | The onboarding package, navigation graph, first-launch flags, storage |

Then list every string of today's onboarding with its file and line, every answer it stores and where (if anywhere) each answer is read again. That list is the start of the copy deck.

## The one test every screen must pass

Read each screen as someone who installed the app thirty seconds ago and knows nothing.
For every line, ask: **"what exactly does this mean, and how would I know?"**

- If a word needs context the user does not have yet ("it", "the game", "armed", "the quiet screen", a product noun never introduced), replace it with the fact behind it.
- If a question has no obvious answer ("How many does it get?", "What do you want back?"), make it concrete: name the thing, give real answers to tap.
- If a picture needs decoding (a metaphor, half of a bar, an icon with no label), replace it or say it in words next to it.
- If a figure appears, the user must be able to see where it came from: their own answer, the app's own measurement, or a named source.

Write down every failure before redesigning anything. A screen-by-screen table "today / what leaves the reader guessing / proposal" is the most useful first artifact.

## Process

1. **Walk today's flow as a new user.** Read the real strings from the code, not from memory or mock-ups. Note every guess the reader must make, every fact the copy gets wrong (check each against the code), and every answer that is collected but never used.
2. **Check the facts.** For each claim in the copy (lengths, prices, what a permission sees, what still works), find the line of code or the document that proves it. Copy that cannot be backed is cut or reworded. Record the evidence next to each line.
3. **Study how good apps open**, from their store listings and first screens, and from any agent or teammate who walked them. Learn patterns, never copy text, art or branding. For each pattern write down what you take and what you leave, and why.
4. **Get an outside view** (a principled reviewer, a design lead, a known writer's public opinions). Record where you followed it and where you departed.
5. **Design, then show it as a clickable prototype** at a small phone (360 x 640 dp) and a tall phone (412 x 915 dp), in the app's real fonts, colours and tokens. Static mock-ups hide flow problems; text descriptions hide layout problems.
6. **Offer real alternatives when the direction is open** (two or three genuinely different directions, each complete and polished), recommend one, and say honestly what each costs. When the owner picks or merges, rebuild as one flow.
7. **Iterate on owner notes literally.** Quote each note verbatim, apply it, show a "note → what changed" table, and keep earlier rounds as linked records instead of overwriting them.
8. **Plan the build** in the same artifact: steps and their ids, state and storage, motion tokens, haptics, files, tests (unit, UI, screen-size matrix, end-to-end), device checks, and which decisions gate which commit.

## Structure of a flow that converts honestly

Order matters. A proven shape (adapt, do not copy blindly):

1. **Welcome** - an outcome headline that says what the app does in plain words, and one line that introduces the brand or the idea. One primary button.
2. **Goal** - "What do you want more time for?" style: one concrete question, 4-7 tappable answers with simple line icons, the button off until something is picked. This makes everything after it about the user.
3. **When / how much** - concrete scheduling or quantity questions ("Which parts of the day?", a slider for "hours a day"). Mark a suggestion that fits their goal, but never pre-select it: an untouched default is not an answer.
4. **Their number** - arithmetic on their own answer, in a unit everyone already holds (whole days on a calendar beats "half a month" on a bar chart). Handle small results gracefully.
5. **Pains** - "What pulls you away from [their goal]?" Up to three, in everyday words, never as faults ("Picking it up out of habit", not "Lack of willpower").
6. **What the app does about each** - one row per pick: a checkable fact about how the problem works, then what the app does. No results it cannot measure.
7. **A short, honest "building your plan" moment** - tick off their real answers as they are combined. Never a fake spinner that waits "even if nothing is loading". Tappable to skip; shorter with animations off.
8. **Their plan** - built from their answers, labelled "suggested from your answers", every part changeable in place, costs and what is free stated plainly. One primary action to turn it on, a secondary "Not now" that saves nothing.
9. **Permissions** - only now, after value. Each row says what it does for *their* plan ("So your plan starts at 10:30 PM, on time"). "Set up later" is never punished. Keep any platform-required disclosure intact and before the system page.
10. **Done** - what happens next, how to do it any time, and one calm closing line.

Seven or eight short steps plus setup is plenty. Cut any screen that only says "ready?".

## Patterns from conversion playbooks: take, adapt, or leave

Questionnaire-style funnels (goal → pain → proof → solution → preferences → permissions → processing → demo → value → account → paywall) contain good ideas and dark ones. Be genuinely open to each, try it, and keep what helps the user believe the app is for them. Hard limits never move:

| Pattern | Use it when | Hard limit |
| --- | --- | --- |
| Goal question, pain points | Always | Answers must visibly change later screens |
| Agree-or-not "sounds like you?" cards | Flow feels like a survey | Everyday situations, first person, never faults |
| Personalised solution, with/without comparison | You can state what the app *does* | No invented percentages or results |
| Preference configuration | It changes something real (the plan) | Only ask what you use |
| Processing moment | It shows the real inputs being combined | No staged waits |
| In-app demo of the core action | It feels native and professional | Label any preview as a preview; drop it if it reads as a toy |
| Social proof, user counts, testimonials | You have real, attributable, consented ones | Never placeholder or written reviews |
| Account gate, paywall | The product really requires them | Never promise an account does something it does not |
| Answers sent to analytics | Declared in privacy policy and store forms | Default to keeping answers on the device |

When you disagree with a pattern the owner may want, still build the pattern-true screen next to your version, mark any hard-limit breach with a warning and use clearly marked placeholders, so the owner can judge.

## Copy rules

- Plain international English, second person, short sentences, no idioms, no metaphors where a fact fits.
- Never shame or blame the user; describe how products work, not what is wrong with people.
- No health or addiction claims. Research may appear as one small sourced line, worded as a finding, never as a diagnosis.
- Facts about other products must be checkable ("each swipe brings a new video") and correct (check the detail: a feed that loops is not one that autoplays the next item).
- Use the product's own vocabulary consistently; if the owner renames a core noun, flag every other place it appears.
- Buttons say what happens next ("Build my plan", "See my plan", "Turn on my plan"), not "Continue" everywhere.
- State costs before they bite, and state what is free ("Let the timer finish and you pay nothing").

## Brand mark and motion

- If the app has a mascot or mark, draw it from the real icon assets so it can never drift from the launcher icon. Split it into parts (wings, body, antennae) to animate.
- Give it **one rule the user can see without being told**, and a job: a guide that moves to where attention belongs (the question, the answer just tapped, the result, the plan). It never speaks, never nags, never covers text.
- One calm story beats nine metaphors. If you use a metaphor, say it once in plain words ("Like a moth drawn to a light, we are drawn to our phones").
- Motion: entrances rise a few dp and settle; nothing bounces; nothing loops forever; sequences use delays inside the animation spec, not sleeps, so a "remove animations" setting collapses them to end states. Every animated picture must still carry its meaning when still.
- Haptics only where they confirm something real (a value changed, a permission granted).

## Layout rules

- **The primary forward button sits in the same place on every step.** Secondary actions ("Not sure", "No idea", "Set up later") go above it, not below or beside.
- Test every screen and state at 360 x 640 and 412 x 915 at 1.0x font, and at large font scales. Script it: for each state, measure `scrollHeight - clientHeight` of the scroll area and fail on overflow. Where a scroll is unavoidable, show a visible "more below" cue.
- On tall phones, balance the space: centre the content block, grow the mark, never leave a dead band between the words and the button.
- Touch targets at least 44-48 dp; contrast that holds on a dark theme; content descriptions for every control; decorative pictures hidden from screen readers, with the headline carrying the meaning.

## Platform notes

The practice is the same everywhere; the mechanics differ.

- **Android (Jetpack Compose):** build steps as stateless composables driven by one UI state; keep answers in a saveable state holder; animate with `tween`/`spring` from shared tokens and read the system "remove animations" setting (animator duration scale) to show end states; draw the mark from the launcher's vector path data (`ImageVector`/`Path`); run a screen-size matrix (for example 320-840 dp at 1.0-2.0x font) with screenshot tests; permission rows read the real grant state on resume, never trust a tap.
- **iOS (SwiftUI):** steps as views over an `@Observable` model; respect `accessibilityReduceMotion`; draw the mark from the app icon's vector source as a `Shape`; preview at small (iPhone SE) and tall (Pro Max) sizes with Dynamic Type up to accessibility sizes; prime notifications and other permissions with your own screen before the one-shot system prompt.
- **Flutter:** one `ChangeNotifier`/`Bloc` for the flow; `MediaQuery.disableAnimations` for reduced motion; `CustomPainter` for the mark; golden tests across sizes and text scales.
- **React Native:** a reducer for flow state; `AccessibilityInfo.isReduceMotionEnabled`; `react-native-svg` for the mark; test on the smallest and largest supported devices with font scaling on.
- **Web:** `prefers-reduced-motion`; SVG for the mark; test at 360 px wide and on a tall phone viewport; keep the primary button reachable without scrolling.

On every platform: one fixed primary button position, decorative art hidden from screen readers, headlines that carry the meaning, and permission state that only "on" when the system says so.

## Short checklist for the next app

1. Fill in the "Start here" sheet from the codebase and listings.
2. Walk today's onboarding as a new user; list every guess, wrong fact and unused answer.
3. Check every claim against code or a named source.
4. Study three to five good apps' first screens; record take / leave for each pattern.
5. Draft the flow: welcome, goal, when/how much, their number, pains, what the app does, a short honest build moment, their plan, value-framed permissions, done.
6. Make the mark a guide with one visible rule; set motion and reduced-motion end states.
7. Build a clickable prototype at a small and a tall phone; script the overflow check for every state.
8. Offer two or three directions if open; recommend one with costs.
9. Iterate on owner notes verbatim; keep every round as a record.
10. Write the build plan: steps, state, storage, tokens, tests, device checks, and which decision gates which change.

## Honesty checklist (run before every round)

- [ ] Every figure comes from the user's answer, the app's measurement, or a named source.
- [ ] Every claim about the app is checked against code or docs, with a file:line or link recorded.
- [ ] No answer is collected that is not used; stored answers are the minimum, kept on the device.
- [ ] Suggestions are labelled as suggestions and never pre-selected.
- [ ] Previews are labelled; nothing implies protection, payment or sign-in that is not real.
- [ ] Permission and disclosure text matches what the code actually does, word for word where a store reviews it.

## Presenting the work

- One review page per flow, revised in place each round, with: a short "what changed and why" at the top; the clickable phones; a copy deck (old / new / why); a facts-checked list; the outside view; choices with one recommendation each and their cost; and the build plan.
- Ask the owner only for real decisions (direction, product rules, store-facing text). Decide routine design picks yourself and say so.
- Keep earlier rounds as linked records. Never delete what the owner already reviewed.

## Worked example (anonymised)

A focus app that keeps chosen apps closed for a set time went through eight rounds:

- Round 1 found that the welcome did not say what the app does, nine screens used metaphors, a question's answer was never used, and an average screen-time figure had no source. Thirteen screens became eight.
- Rounds 2-3 added a concrete "what keeps you on your phone?" question and a factual screen on how feeds keep people scrolling (each line checked; one draft line was wrong about autoplay and was fixed).
- Round 4 tried an in-app "try it" demo of the lock screen. The owner found app previews unprofessional, so it was dropped in round 6.
- Round 5 rebuilt around the goal, studied a conversion-questionnaire skill openly, adopted most patterns and showed every rejected one, built pattern-true with warnings.
- Round 6 offered three polished directions led by the app icon (calm and atmospheric, bold editorial, a guiding mascot). The owner merged them: the calm look with the guide's animations.
- Round 7 replaced a "half a month" bar with whole days on a calendar, introduced the mark on the welcome screen ("drawn to a light, as we are to our phones") and stated that finishing costs nothing.
- Round 8 added a "when do you want essentials only?" step that builds the plan's time windows, made the mark follow each answer, and closed with a calm, sourced line about the mark (moths have existed for over 200 million years).

The owner's verdict on round 7: the onboarding finally felt like it was made for first-time users.
