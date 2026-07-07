---
name: survey-creation-review
description: Generate, review, and optimize surveys for generative or evaluative research. 
---
Generate a well-structured, bias-free survey grounded in UX Research. 

Arguments: $ARGUMENTS

When you reach a PAUSE block: stop, output the pause text to the user and wait for instructions 

---

## Context Loading 
If the user is pasting a survey draft directly, use that. If not, ask the user to specify the file — it may be a .md, .txt, or other format. 

--- 

## Mode Detection - Build v Review 

Before running step 1, determine which mode applies: 

**Review Mode** - Triggered when the user provides an existing survey draft in '$ARGUMENTS' or their opening messaging includes 3+ recognizable survey questions, a list of questions, or explicit language like 'here is my survey, review this'

**Build Mode** - triggered when no draft is present and the user describes a goal, feature or topic 

### Review Mode 
Confirm receipt of the draft but do not begin question review.

> I can see you have a draft. Before I review the questions, I want to make sure a survey is the appropriate method for your goal. 
> 
> 1. **What do you want to learn?** - What is the single biggest unknown this survey should answer? 
> 2. **How will you use the results?** - What decision or action will this data inform? 

> **PAUSE** — Waiting for your answers above before continuing.

Wait for a response then run step 3 (escalation and method fit check) against those answers. Only proceed to Step 5 if a survey is appropriate. Otherwise provide language that another method may be a better fit. 

## Step 1 - Intake *Build mode only* 
Announce: 
> I'll help you build a clear, bias-free survey. I'll ask a few questions to ground the survey. 
> 
> To get started: 
> 
> 1. **What do you want to learn?** - What is the single biggest unknown this survey should answer? 
> 2. **How will you use the results?** - What decision or action will this data inform? 
> 3. **Study mode** - Is this generative (exploring attitudes, behaviors, needs) or evaluative (measuring usability, satisfaction, or concept response?)
> 4. **Survey tools** - Which platform will you use to field this (e.g., Qualtrics, Google Forms, dScout, other, I don't know)

If the user provided context via '$ARGUMENTS' or this skill was called from another skill or project folder, extract answers from that rather than re-asking 

> **PAUSE** — Waiting for your responses above before continuing.

---

## Step 2 - User Track Detection

Based on the user's intake responses silently assign a track: 

- **Researcher track** - User identifies as a researcher, references standard UX research language and methods, or demonstrates fluency in UX research skills. Provide full control: question type choice, scale configuration, branching and logic options. 
- **Non-Researcher Track** - User identifies as a designer or PM, uses non-UX research language. Provide guardrails to surface plain-language prompts, flag risky patterns, and keep scope tight. 

Do not announce the track, simply adjust your tone and depth of guidance accordingly. Default to a non-researcher track unless you have 75% or higher confidence of the user's fluency with survey methodologies. 

--- 

## Step 3 - Complexity and Escalation Check 

Before drafting, evaluate scope against the complexity thresholds and escalate immediately if: 

- More than 10 questions are needed 
- Complex branching is required beyond simple skip logic 
- The goal will not be answerable by survey data alone (need for analytics, interviews, etc)

If one or more thresholds are exceeded: clearly name each one that was triggered and explain why it applies. Then ask:

> **PAUSE** — One or more complexity thresholds were exceeded (see above). Would you like to proceed with a narrower scope, or pause to refine your goals first?

If no thresholds are exceeded, continue to Step 4 without pausing. 

--- 

## Step 4 - Survey Structure and Question Drafting 

Draft the survey following best practices https://www.nngroup.com/articles/survey-best-practices/ 

**Length** Target 3-5 questions for a micro survey. Maximum 7 for a standard survey. Call out scope creep. Do not silently expand 

**Metric Standardization** Use UMUX Lite (2 questions) (https://measuringu.com/umux-lite/) for perceived usability measurements. Do not use NPS unless explicitly requested 

**Question mix** Closed questions first (rating, scale, single select, multi-select) open-ended questions last. Each open-ended question should ask exactly one thing. 

**Bias eradication** — Check every question against:
- Leading Bias - Does the phrasing assume a preference or outcome?
- Double-barreled - Does the question ask two things at once? 
- Acquiescence bias - Does the question make agreement feel like the natural answer? 
- Social desirability bias - Does one answer feel safer or more professional than another? 

When a question has a flaw, name the bias and give a direct rewrite. Do not hedge. 

> **PAUSE** — Draft complete. Review the questions above and let me know if you'd like any adjustments before final validation.

--- 

## Step 5 - Review and Validation 
Present the full draft survey with a structured review 

**Goal Alignment** Pass / Fail - will these questions answer the stated learning goal? 

**Length** Pass / Fail - Question count and estimated completion time 

**Question by Question**

*If Claude-generated (Build Mode):*
- Question Type
- Question
- Rationale: what this question will achieve and how it maps to the learning goal

*If user-provided (Review Mode):*
- Original Question
- Issue (if any): Bias or structural 
- Rewrite (if needed): concrete replacement 

**Branching / Logic Notes** Flag if concerning 

> **PAUSE** — Review complete. Let me know how you'd like to proceed.
