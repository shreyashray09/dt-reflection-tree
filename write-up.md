# Write-Up: Design Rationale for the Daily Reflection Tree

## Why These Questions

The hardest part of this assignment wasn't building the tree — it was writing questions that a tired person at 7pm would answer honestly instead of clicking through to finish. I tested each question by imagining someone who had a genuinely bad day: a missed deadline, a tense meeting, a colleague who let them down. Would they stop and think, or would they pick the easiest answer and move on?

**Axis 1 — Locus (Victim ↔ Victor)**

The opening question uses a weather metaphor deliberately. "How was your day?" invites performance. "If today were a weather report?" invites description. Framing forces a different cognitive mode — the employee has to translate before answering, which slows them down just enough to be honest. The options (Sunny / Cloudy / Stormy / Foggy) are non-judgmental on their face, but they carry real signal: "Foggy" captures the dissociation that often accompanies external locus — not frustration, but *disconnection from agency*.

The follow-up questions branch based on the opening: people who reported a "good" day are asked what made it happen (do they take credit?), while people who reported a "bad" day are asked what their first instinct was (do they reach for control or withdraw?). This matters because Rotter's original scale (1954) found that locus of control is not about outcomes — it's about *attribution*. A person with an internal locus can have a terrible day and still see their choices. The questions try to surface attribution, not just outcome.

The second-layer questions ("Think of one moment where you made a deliberate choice...") are designed to operationalize agency in concrete behavioral terms — not "are you an internal or external?" but "what specific kind of choice did you make?" This prevents the tree from feeling like a personality quiz.

**Axis 2 — Orientation (Entitlement ↔ Contribution)**

Organ's (1988) concept of Organizational Citizenship Behavior — discretionary effort beyond formal job requirements — is notoriously hard to self-report, because people don't typically frame their behavior in those terms. The question "Think about your interactions today — which of these best describes a moment that stood out?" forces a memory-retrieval frame rather than a self-assessment frame. This is intentional: memory is harder to game than self-report.

The trap I tried to avoid: asking people whether they're entitled is useless, because psychologically entitled people (Campbell et al., 2004) genuinely don't experience themselves as entitled — they experience their expectations as *fair*. So the questions approach entitlement through what the employee was *tracking* (recognition, fairness, others' effort) rather than labeling it. The follow-up question — "What would change if you let that go, even temporarily?" — isn't asking them to give it up. It's asking them to notice it.

**Axis 3 — Radius (Self-Centric ↔ Altrocentric)**

Maslow's late work on self-transcendence (1969) is the least-known part of his hierarchy, and the most relevant here. His insight was that the peak of human psychological health isn't self-actualization — it's *care for something beyond the self*. The "radius of concern" metaphor came from this: how wide is the circle of who you're thinking about?

The opening question ("Who comes to mind first?") deliberately offers four options that map to concentric circles: self → team → specific colleague → customer/end user. The progression is visible to the reader of the tree, but not labeled for the employee. This lets the question do its work without signaling the "right" answer.

The follow-up questions don't moralize about self-focus. The question to a self-focused employee ("Was there anyone else affected by how your day went, even indirectly?") is genuinely curious — it might be true that their day was entirely self-contained. But the question makes them check.

---

## How I Designed the Branching

**The core branching logic is two-stage per axis:**

1. *Opening question* routes the employee into a "high" or "low" branch for that axis based on their initial response.
2. *Follow-up question* within each branch probes the signal further.
3. *State accumulates* across both questions, and a final decision node reads the dominant signal to route to the appropriate reflection.

**Trade-offs I made:**

- **Fewer branches, more nuance within them.** I could have branched after every question, creating an exponential tree. Instead I chose to keep the main paths to two per axis (positive/negative pole), but make the questions within each path genuinely different. A person on the "high agency" path gets asked about the *type* of choice they made; a person on the "low agency" path gets asked whether they can retroactively see a choice they missed. Same axis — different conversation.

- **The bridge nodes carry interpretive weight.** The bridges between axes aren't just transitions — they contextualize what's coming. "You've looked at how you navigated today. Now let's look at what you gave" tells the employee that we're shifting frames, but also *implicitly reframes* the first axis: navigation is agency, and agency leads to questions about what you do with it. This is the axis progression in action.

- **The summary is combinatorial.** There are 8 possible axis-combination states (2³). Rather than writing 8 unique summaries, I built a template system: each axis contributes its own sentence, and the closing question is selected from a lookup table based on the full combination. This is auditable and extensible — adding a fourth axis would require only new template entries, not restructuring.

**What I'd improve with more time:**

1. **More granular second-layer branching on Axis 2.** The contribution/entitlement axis currently has one follow-up per branch. With more time, I'd add a third question that targets the edge cases — people who are contribution-oriented but secretly tracking whether they're noticed, or people who feel entitled but are also legitimately high-contributors. This is the most psychologically rich territory in the assignment.

2. **Time-of-week context.** A Friday reflection should feel different from a Monday one. The tree could accept a day-of-week input and adjust its opening and closing tone — "It's the end of the week. What does that week add up to?" — without changing the underlying branching logic.

3. **A session log that shows the path taken.** The employee should be able to see the full path they walked — not just the summary, but every question and every answer, in sequence. This makes the tool useful as a journal, not just a mirror.

4. **Longitudinal tracking.** The biggest limitation of a single-session tool is that there's no before/after. Tracking axis signals across weeks would reveal whether someone's locus is actually shifting — which is the actual measure of whether the tool is working.

---

## Psychological Sources

- Rotter, J. B. (1954/1966). *Generalized expectancies for internal versus external control of reinforcement*. Psychological Monographs.
- Dweck, C. (2006). *Mindset: The New Psychology of Success*. Random House.
- Campbell, W. K., Bonacci, A. M., Shelton, J., Exline, J. J., & Bushman, B. J. (2004). Psychological entitlement: Interpersonal consequences and validation of a self-report measure. *Journal of Personality Assessment*.
- Organ, D. W. (1988). *Organizational Citizenship Behavior: The Good Soldier Syndrome*. Lexington Books.
- Maslow, A. H. (1969). Theory Z. *Journal of Transpersonal Psychology*.
- Batson, C. D. (2011). *Altruism in Humans*. Oxford University Press.
