---
name: research-plan-generator
description: Generate research plans and moderator guides grounded in UX Research best practices. 
---
Generate research plans and moderator guides grounded in UX Research best practices. Ensures all research is based on unambiguous research questions and clearly maps to Discovery, Pre-Market, or Post-Market research and is defined as Generative or Evaluative. 

Arguments: $ARGUMENTS

When you reach a PAUSE block: stop, output the pause text and wait for a reply before continuing. 

--- 

## Context loading

- Read the project folder or files or text provided to understand any basis. 
- Review https://www.nngroup.com/articles/ux-research-cheat-sheet/ for the difference between Discover (Discovery) research, Exploring, Testing, and Listening — and how each maps to research methods.
- Review https://www.nngroup.com/articles/which-ux-research-methods/ to understand when to use different methods and the attitudinal vs. behavioral, qualitative vs. quantitative framework.
- Review https://www.surveyking.com/blog/research-questions/ for good research questions. 
- Review https://findingourway.design/2020/11/17/22-right-problem-right-solution-done-right-the-vanguard-of-user-research-ft-jen-cardello/ for the "right problem, right solution, done right". 

--- 

## Step 1 - Intake 

Announce: 
> I'll help you design a research study grounded in UX Research best practices. 
>
> To build a plan, I need some context: 
> 
> 1. **Product / Features** - What are we testing or exploring? 
> 2. **Current Phase** - Are you in early discovery, testing a prototype, or analyzing a live feature? Would you describe your efforts as generative - understanding the domain and needs, or evaluative - testing a proposed solution or idea? 
> 3. **The Big Unknown** - What is the single biggest question you want to answer? 
> 4. **What Do you know?** - What do you currently know, or believe to be true about the domain or solution? 
> 5. **Goals** - What will stakeholders and the team do with this information? 
> 6. **Existing Research & Artifacts** - Do you have any prior research, analytics data, personas, journey maps, competitive analysis, or other artifacts related to this product or domain? If so, please share or describe them.

Wait for response. If provided via arguments, extract answers from that context and confirm. 

---

## Step 1.5 — Secondary Research & Pre-Research Gate

### Existing Research Review

If the user provided existing research or artifacts in Q6:
- Review and summarize the key findings, known knowns, and assumptions they surface.
- Note how these refine the intake answers — particularly the hypothesis (Q4) and the big unknown (Q3).
- Flag any gaps the existing research does not address. These gaps should anchor the research question in Step 3.

If no existing artifacts were provided: note this and proceed.

### Heuristic Evaluation Gate

Evaluate the following two conditions against the intake answers:

**Condition A:** Does an existing product, site, or workflow exist?
- Signals: user describes a live product, an existing tool, a current workflow, or a feature already in use.

**Condition B:** Does the research goal involve understanding current behaviors, usage patterns, or workflow performance?
- Signals: phrases like "how users currently use," "understand existing behavior," "what's working or not," "current pain points," or a Discover-phase framing around an existing product.

If **both conditions are true**, present the following before proceeding to Step 2:

> **Recommendation: Run a Heuristic Evaluation First**
>
> Before conducting primary user research, a heuristic evaluation of the existing [product / site / workflow] would help ground your research question in observed usability issues and surface known knowns. This reduces the risk of your primary research confirming what an expert review could have identified in a fraction of the time — and it sharpens the questions worth taking to users.
>
> Would you like to run a heuristic evaluation using the `heuristic-review` before continuing with this plan?

- If **yes**: Invoke `heuristic-review` and note that findings should be brought back into this plan to inform Step 2 and Step 3 before continuing.
- If **no**: Acknowledge and proceed to Step 2. Log the decision in the Risks section of the test plan as: *Heuristic evaluation not conducted prior to primary research — known usability issues may be re-surfaced rather than explored.*

If neither condition is met: proceed directly to Step 2.

---

## Step 2 - Framework Mapping 

Using the context loaded from NNg and the intake answers, map the study to a research phase and method.

### Phase Classification

Classify the research phase using the NNg cheat sheet framework:
- **Discover** — Generative research. Little is known. Goal: understand the problem space, users, and needs.
- **Explore** — Still generative, but more focused. Goal: understand how users think about a domain or concept.
- **Test** — Evaluative. A design or prototype exists. Goal: assess usability or effectiveness.
- **Listen** — Ongoing or attitudinal. Goal: track trends, satisfaction, or user-reported behavior.

### Method Selection Logic

Select the primary method based on phase and the nature of the big unknown:

| Phase | Nature of Unknown | Recommended Method |
|---|---|---|
| Discover | Behaviors, environment, workflows in context | Contextual Inquiry |
| Discover / Explore | Mental models, attitudes, needs | User Interviews |
| Explore | Preference or reaction to an early concept | Concept Testing |
| Test | Task performance, usability issues | Usability Testing |
| Listen | Attitudes, satisfaction at scale | Survey |
| Any | Compliance with heuristics or standards | Heuristic Evaluation |

### Behavioral and Quantitative Analytics

Flag when behavioral or quantitative data should be considered:

- **In place of qual** — When the research question is about frequency, scale, or patterns across a large user base (e.g., "How many users drop off at step 3?"), recommend analytics or A/B testing rather than qualitative methods.
- **In conjunction (mixed methods)** — When the research question requires both the *what* (scale and frequency from analytics) and the *why* (meaning and context from qual), recommend a mixed methods approach. Note which methods address each dimension.

### Output of Step 2

Identify and present:
- Proposed primary methodology
- Secondary or mixed methods, if applicable
- Rationale for the recommendation
- Whether behavioral or quantitative data should supplement or replace qualitative work

Ask the user to confirm or redirect before proceeding.

**Note:** This skill references the following related skills for method-specific support:
- `/skill-survey-creation-review` — for survey design
- `/heuristic-review` — for heuristic evaluation

--- 

## Step 3 - Question Generation & Validation 

Draft a high-level, unambiguous research question scoped to the product context, rooted in the confirmed methodology from Step 2.

The research question should:
- Be written at the study level — not as individual interview questions or survey items
- Be phrased in plain language a stakeholder could understand
- Clearly reflect whether the study is generative or evaluative

Validate against Good Research Criteria: 
- **Specific** - Focused enough to answer 
- **Actionable** - Leads to a clear decision 
- **Practical** - Answerable with common UX Research methods 
- **Non-Research Theater** - Does not address decision avoidance 
- **Needs focused** - Does not anchor on technical feasibility 

If the question fails any gate, discuss with the user opportunities to refine.

Once validated, state the confirmed research question explicitly. This becomes the anchor for the test plan generated in Step 5.

--- 

> **PAUSE - Research question validated**
> Share the validated research question and confirm with the user before continuing. 

--- 

## Step 4 - Discussion / Moderator Guide

Based on the method confirmed in Step 2, route to the appropriate guide:

| Method | Guide |
|---|---|
| User Interviews | Invoke `discussion-guide-template` |
| Concept Testing | Invoke `discussion-guide-template` |
| Usability Testing | Invoke `discussion-guide-template` |
| Contextual Inquiry | Invoke `discussion-guide-template` |
| Survey | Invoke `skill-survey-creation-review` |
| Heuristic Evaluation | Invoke `heuristic-review` |

When invoking `discussion-guide-template`, pre-populate the following fields from the research plan:
- **Study Name** — from product/feature context (Step 1)
- **Researcher** — from Team section (Step 5)
- **Method** — from confirmed method (Step 2)
- **Research Question** — from validated question (Step 3)
- **Participant profile** — from Participants section (Step 5)

When invoking `skill-survey-creation-review`, pass the following:
- **Research Question** — from validated question (Step 3)
- **Study Mode** — Generative or Evaluative (from Step 2)
- **Study Phase** — Discover / Explore / Test / Listen (from Step 2)

Ask:
> Would you like me to generate a discussion guide now, or add it as a placeholder in the test plan?

If generate now: invoke the appropriate skill with the pre-populated context above passed as arguments.

If placeholder: add a section in the test plan output noting the guide is to be developed separately using `discussion-guide-template`.

--- 

## Step 5 - Generate Test Plan 

Generate the structured test plan as a formatted markdown document using the sections below. Where a section requires user input that has not yet been provided, insert a clearly labeled placeholder in brackets.

---

```
# Research Test Plan: [Project / Feature Name]

## Research Question
[Insert validated research question from Step 3]

## Project Phase
[Discover / Explore / Test / Listen] — [Generative / Evaluative]

## Team
| Role | Name |
|---|---|
| Researcher | [Name] |
| Stakeholders | [Names] |
| Designers | [Names] |
| Other | [Names] |

## Method Selection
**Primary Method:** [Method]  
**Rationale:** [1–2 sentences summarizing why this method fits the research question and phase]  
**Mixed Methods / Analytics:** [Describe if applicable, or N/A]

## Timeline
| Milestone | Target Date |
|---|---|
| Study design complete | [Date] |
| Recruitment complete | [Date] |
| Sessions begin | [Date] |
| Sessions complete | [Date] |
| Analysis complete | [Date] |
| Readout | [Date] |

## Hypothesis
What we currently believe to be true about the solution or problem space:

> [Derived from Step 1 intake — "What do you know?" — or user-provided]

## Risks
| Risk | Mitigation |
|---|---|
| [e.g., Recruitment delays] | [e.g., Begin outreach 2 weeks early] |
| [e.g., Scope creep from stakeholders] | [e.g., Align on research question before sessions begin] |

## Tools
| Purpose | Tool |
|---|---|
| Session platform | [e.g., Zoom, UserTesting] |
| Recording | [e.g., Otter.ai, Dovetail] |
| Synthesis | [e.g., Dovetail, Miro] |
| Survey platform | [e.g., Qualtrics — if applicable] |
| Prototype | [e.g., Figma — if applicable] |

## Participants
*This section is to be completed by the research team.*

**Target user group:** [Placeholder]  
**Screener criteria:** [Placeholder]  
**Number of participants:** [Placeholder — reference NNg guidance: ~5 for usability testing, 8–10 for qualitative interviews, 100+ for surveys]  
**Recruitment method:** [Placeholder]  
**Incentive:** [Placeholder]  

## Moderator Guide
*[Placeholder — to be developed as a separate document]*

*(Remove this section if not flagged in Step 4)*
```

---

## Output

Deliver the completed test plan as a formatted markdown document.

Remind the user:
> This plan is formatted in markdown. You can paste it directly into a Google Doc or Word document.  
> - **Google Docs:** Use *File > Import* or paste into a blank doc and use a Markdown import extension such as Docs to Markdown.  
> - **Word:** Paste into a blank document — headers and tables will carry over if your paste settings support rich text.

---

## After Your Sessions

From here, the plan is yours to execute. When sessions are complete and you have raw data to work with, return and run:

- **`thematic-analysis-processor`** — to process transcripts, notes, or open-ended survey responses into a structured thematic synthesis. Pass the Research Question from Step 3 as context — it anchors the synthesis to what you set out to learn.
- **`insights-to-action`** — once synthesis is complete, to translate findings into a stakeholder-ready executive readout and prioritized action plan.

If your method was a **heuristic evaluation**, you can bring those findings back into `thematic-analysis-processor` as a baseline when you run follow-up user sessions — the analysis will track what the heuristic predicted versus what users actually showed.

If your method was a **survey with closed-ended questions only**, route results directly to `insights-to-action` — no thematic analysis step required.
