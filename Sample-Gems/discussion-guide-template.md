---
name: discussion-guide-template
description: Structured discussion guide for qualitative UX research sessions. Covers user interviews, concept testing, usability testing, and contextual inquiry. Inherits context from skill-research-plan when invoked as part of a study.
---
A discussion guide template to be used independently or in conjunction with skill-research-plan. Covers four qualitative methods: user interviews, concept testing, usability testing, and contextual inquiry.

When invoked from skill-research-plan, the following fields are pre-populated from the research plan:
- Study Name (from product/feature context)
- Researcher Name (from Team section)
- Research Question (from Step 3)
- Participant profile (from Participants section)
- Method (from Method Selection)

Arguments: $ARGUMENTS

---

# Discussion Guide

## Session Header

| Field | Value |
|---|---|
| Study Name | [Inherited from research plan, or enter manually] |
| Researcher | [Inherited from research plan, or enter manually] |
| Method | [Inherited from research plan: User Interviews / Concept Testing / Usability Testing / Contextual Inquiry] |
| Research Question | [Inherited from Step 3 of research plan, or enter manually] |
| Participant # | [P-___] |
| Participant Profile | [Inherited from Participants section of research plan, or enter manually] |
| Date | [Date] |
| Session Length | [30 min / 60 min] |
| Observer / Note-taker | [Name] |
| Consent Recorded | [ ] Yes  [ ] No |

---

## Introduction
*Suggested time: 3–5 minutes*

Hello [participant name], thank you for taking the time to meet with me today.

My name is [your name] and I am [your role]. I am joined today by [note-taker / observer name], though our conversation today will primarily be between you and myself.

We are meeting today to discuss [research area of inquiry].

I want to be clear about what today is and is not. I am not here to evaluate or grade how you perform a task. I am not here to sell you any product or service. There are no right or wrong answers — we are here to learn from you. Your candid feedback is the most valuable thing you can share with us today.

### Consent
We do ask to record this session. The recording is strictly for note-taking purposes and will not be shared outside the research team.

Do I have your permission to record today?
*(If yes, begin recording)*

We are now recording for data-collection purposes. If at any time you would like to pause or stop the recording, please let me know and I will do so immediately.

---

## Warm-Up
*Suggested time: 2–3 minutes*

Before we get into the main topic, I'd like to start with a few questions to get to know you a bit better.

**W1** — Could you start by telling me about your current role and what a typical day looks like for you?

**W2** — How long have you been in this role?

**W3** — What is your familiarity with [topic / domain]?

---

## Main Discussion

*Select the activity section that matches your method. Remove unused sections before the session.*

---

### Method: User Interviews
*Suggested time: 40–45 minutes of a 60-minute session / 20–25 minutes of a 30-minute session*
*Use for: exploring mental models, attitudes, needs, and behaviors. Open-ended. No prototype or task required.*

**U1** — Walk me through how you currently [perform task or engage with domain]. Take me through it from beginning to end.

**U2** — What works well about that process for you?

**U3** — What is frustrating or harder than it should be?

**U4** — When you hit a difficult moment in [task or domain], what do you do?

**U5** — Tell me about the last time [relevant scenario]. What happened?

**U6** — What tools or resources do you rely on most in this space?

**U7** — If you could change one thing about [task or experience], what would it be?

*Add topic-specific probes here as needed. Follow the thread — if a participant opens a door, walk through it before returning to the guide.*

---

### Method: Concept Testing
*Suggested time: 35–40 minutes of a 60-minute session / 20 minutes of a 30-minute session*
*Use for: evaluating reactions to early concepts or design directions before build. Two or more concepts are presented.*

**Before showing concepts — set context:**
> In a moment, I'm going to show you [number] design concepts. These are early ideas, not finished products. I'm interested in your honest reaction — what works, what doesn't, and what questions come to mind. There are no right or wrong answers.

**Think-aloud instruction:**
> As you look at each concept, I'd like you to think out loud — narrate what you're seeing, what you're thinking, and what questions come up for you. This helps us understand your thought process, not just your conclusions.

**For each concept shown:**

**CT1** — Take a moment to look this over. What are your first impressions?

**CT2** — What stands out to you most?

**CT3** — What questions does this raise for you?

**CT4** — What, if anything, is unclear or confusing?

**CT5** — How well does this fit how you currently work?

**After all concepts shown:**

**CT6** — Comparing the concepts you've seen, which felt most natural to you, and why?

**CT7** — Was there one that felt like more work? What made it feel that way?

**CT8** — If you could take the best parts of each and combine them, what would that look like?

---

### Method: Usability Testing
*Suggested time: 35–45 minutes of a 60-minute session / 20–25 minutes of a 30-minute session*
*Use for: evaluating task performance and identifying usability issues with a prototype or live product.*

**Think-aloud instruction:**
> As you work through each task, I'd like you to think out loud — tell me what you're looking for, what you're clicking, and what you're thinking as you go. If you get stuck, narrate that too — it's exactly the kind of thing we need to hear. I won't be able to help you complete tasks, but I'm here to listen.

**For each task:**

**UT1** — Here is your task: [Task description]. Go ahead and begin whenever you're ready.
*(Observe. Note hesitations, errors, path taken, think-aloud content. Do not guide.)*

**UT2** — How would you describe that experience?

**UT3** — Was there a moment where you were unsure what to do next?

**UT4** — What would you expect to happen when you [action]?

**UT5** — On a scale from 1 to 5, how confident were you completing that task? Why?

*(Repeat UT1–UT5 for each task. 2–3 tasks for a 30-minute session; 4–5 tasks for a 60-minute session.)*

---

### Method: Contextual Inquiry
*Suggested time: 40–50 minutes of a 60-minute session*
*Use for: observing users in their natural context, understanding real behaviors and environment. Best conducted in the participant's workspace if possible.*

**Setup note for researcher:** Position yourself as an observer, not an interviewer. Ask the participant to work as they normally would. Your role is to watch, ask clarifying questions, and probe what you observe — not to direct.

**CI1** — I'd like to start by asking you to show me how you typically [task or workflow]. Walk me through it as if I wasn't here — just do what you'd normally do.
*(Observe. Note tools used, workarounds, environment, sequence of steps, moments of friction.)*

**CI2** — I noticed you [specific observed behavior]. Can you tell me more about why you do it that way?

**CI3** — Is that how you always approach [task], or does it vary?

**CI4** — What is easy about this part of the process?

**CI5** — What is harder than it should be?

**CI6** — Are there tools or shortcuts you rely on that I wouldn't see just by watching?

**CI7** — Is there anything about this environment or setup that affects how you work?

*(Follow the participant's natural flow. Probe what you observe. Return to the guide only if conversation stalls.)*

---

## Closing
*Suggested time: 5 minutes*

**C1** — As we close, if you could change one thing about [task or experience], what would it be?

**C2** — Is there anywhere in our conversation today where we moved on before you had a chance to finish your thought?

**C3** — You have been extremely generous with your feedback today. Is there anything top of mind you'd like to share about [topic] that I can bring back to the team on your behalf?

**C4** — Do you have any questions for me?

**C5** — Thank you again for your time today. [Share high-level next steps if appropriate.] I hope you have a great rest of your day.
