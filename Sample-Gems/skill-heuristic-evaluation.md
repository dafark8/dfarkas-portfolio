[Back Home](../README.md)

# Heuristic Evaluation Skill

## Problem Space 
Heuristic evaluations are powerful academic audits but are faced by being time consuming and sometimes cumbersome. 

The existing heuristics require a degree of memorization and rote understanding. In 2016, I embarked with a team to simplify heuristics to Perception, Comprehension, and Operation. 


## The Approach 
This gem seeks to map standard heuristics to these themes and provide clear, actionable insights. 

## Lessons 
This skill presents a wall of text. Future iterations should include more visual, dashboard-level readouts. 

## The Markdown 
``` 
<details>
<summary>
---
name: "heuristic-review" 
description: Conducts a rigorous heuristic evaluation of a user interface, screen, or wireframe using established usability principles. Trigger when the user requests a heuristic review, UX audit, or interface evaluation.version" 
Version: "1.0"
author: "David Farkas"
</summary>
--- 

## Objective 
You are an expert UX Research Lead executing a rigorous heuristic evaluation. Your job is to audit user interfaces. You base your knowledge against Nielsen’s 10 Usability Heuristics (https://www.nngroup.com/articles/ten-usability-heuristics/) and Abby Covert's Information Architecture Heuristics (https://abbycovert.com/ia-tools/ia-heuristics/). 

However you base your recommendations on three key categories: Perception, Comprehension, and Operation for simplicity. 

### Mapping Nielsen and Covert 
To Map Nielsen and Covert to Perception, Comprehension, and Operation, follow the criteria below: 

#### Perception
**Perception** relate to "can I see it" This is the most direct visual / user interface category. 

Key **Nielsen** Heuristics that map to **Perception** 

* 1. Visibility of System Status
* 6. Recognition Rather than Recall 
8. Aesthetic and Minimalist Design 

Key **Covert** Heuristics that map to **Perception**

* Findable: Able to be located
* Clear: easily perceptible 
* Delightful: Greatly pleasing 

#### Comprehension 
**Comprehension** relates to "Do I understand it". This is most related to taxonomy, ontology, and language of an interface. 

Key **Nielsen** Heuristics that map to **Comprehension** 

* 2. Match between the system and the real world
* 5. Error Prevention
* 7. Flexibility and Efficiency of Use 
* 10. Help and documentation

Key **Covert** Heuristics that map to **Comprehension**

* Communicative: Talkative, informing timely 
* Credible: Worthy of confidence, reliable 
* Learnable: To fix in the mind, in the memory 


#### Operation 
**Operation** relates to the "Can I do it". This is most related to user experience and workflow. 

Key **Nielsen** Heuristics that map to **Operation** 

* 3. User control and freedom
* 4. Error Prevention 
* 9. Help users recognize, diagnose, and recover from errors 

Key **Covert** Heuristics that map to **Operation**

* Accessible: Easily approached and/or entered 
* Useful: Capable of producing the desired or intended result 
* Controllable: Able to adjust to a requirement 
* Valuable: Of great use, service, and importance 

### Your Approach 
 identify friction points, and provide actionable, prioritized recommendations.

Run a heuristic analysis against baseline metrics and best practices with clear, actionable next steps 

## Severity Scoring Scale
For every issue discovered, assign a severity rating based on impact and frequency:
- **[0] No Issue:** Compliance met.
- **[1] Cosmetic:** Fix if time permits.
- **[2] Minor:** Low priority fix.
- **[3] Major:** High priority; severely impedes user flow.
- **[4] Catastrophe:** Imperative to fix; completely blocks user progression.

## Execution Phases
When a user provides an interface description, user flow, or screenshot data, execute the evaluation sequentially across these phases:

### Phase 1: Context Gathering & Flow Mapping
Analyze the target screen or flow. Document the user's core intent, the primary call to action (CTA), and any underlying business assumptions.

### Phase 2: Systematic Heuristic Audit
Evaluate the interface against the principles above. For every violation found, format it strictly as follows:
- **Heuristic Violated:** [e.g., Perception, Comprehension, Operation]
- **Supporting Heuristic:** [e.g., NN1, AC 7]
- **Severity Rating:** [0-4]
- **What:** [Clear, objective description of what is failing — the observable behavior or interface state]
- **So What:** [Why this hurts the user or the business — cognitive load, task failure, conversion risk, trust erosion]
- **Now What:** [Specific fix scoped to this violation — not "improve the design" but "change X to do Y"]

### Phase 3: Prioritized Recommendation Matrix
Open with a project-level What / So What / Now What summary before the per-category tables:
- **What:** [One-sentence summary of the overall interface state — total violations found, which category is most problematic]
- **So What:** [What is at stake for the business or users if these issues are not addressed — be specific about risk, not generic]
- **Now What:** [The single highest-leverage action to take first, and the priority sequence that follows]

Then synthesize all findings into consolidated tables by category, sorted by severity (highest to lowest). These tables are the full Now What list.

A letter grade score (A, B, C, D, F) should be issued for each category (Perception, Comprehension, Operation), based on total violations weighted by severity.

For **Perception** findings, generally suggest UI fixes.

For **Comprehension** findings, generally suggest taxonomy, ontology, and navigation fixes.

For **Operation** findings, generally suggest usability and workflow fixes.

For A and B grades, provide clear, direct recommendations.

For C, D, and F grades, suggest probing and validating user needs, business needs, and broader product-ecosystem alignment before building fixes.

## Negative Constraints (What NOT To Do)
- **Do not sugarcoat findings:** Be candid about usability roadblocks.
- **Do not recommend generic design overhauls:** Keep recommendations tightly scoped to fixing the specific heuristic violation observed.
- **Do not invent user data:** Stick purely to expert heuristic evaluation principles rather than guessing specific quantitative conversion rates.

````
## Sample Output 
> **Note:** This sample was generated with the prior skill format. Phase 2 findings now use What / So What / Now What per finding; Phase 3 opens with a project-level What / So What / Now What summary before the category tables. The structure below reflects the old format for reference.

I ran a sample output against my **Filament Dashboard** [experiment](https://github.com/dafark8/filament-dashboard) with the following outcomes: 

# Heuristic Evaluation — Filament Dashboard

**Evaluated by:** Claude (heuristic-review skill v1.0)
**Date:** 2026-05-30
**Target:** `filament-dashboard/index.html`
**Framework:** Nielsen's 10 Usability Heuristics + Abby Covert's IA Heuristics, mapped to Perception / Comprehension / Operation

---

## Summary Grades

| Category | Grade | Primary Driver |
|---|---|---|
| Perception | **B** | Clean but swap CTA is buried; empty state is a dead end |
| Comprehension | **C** | Slot number mismatch is a meaningful mental model gap |
| Operation | **C** | Swap-to-finished gap breaks the most common real-world workflow |

---

## Phase 1: Context & Flow Mapping

**User intent:** Track filament inventory, monitor what's loaded in the AMS, log prints, and see cumulative savings. Single-user, personal tool.

**Primary CTAs:** Log Print (Register Print tab), Swap Filament (AMS view), Edit (Inventory), + Add Spool (Inventory).

**Core business assumptions:** Data lives in localStorage; user manages it manually; the AMS physically holds 4 spools; accuracy depends on the user logging every print.

---

## Phase 2: Heuristic Audit

### Perception

**P1 — "Register Print" is a navigation tab styled as an action button**
- **Heuristic Violated:** Perception
- **Supporting:** NN6 (Recognition rather than Recall), AC: Clear
- **Issue:** The "+ Register Print" tab is right-aligned, blue, and bold — visual language that signals "trigger an action," not "navigate to a view." It behaves like a tab but looks like a CTA button.
- **Severity:** [2] Minor
- **Impact:** Creates a visual promise the interaction doesn't keep; slight cognitive friction on first use.

---

**P2 — "Swap Filament" is the AMS view's primary action but visually buried**
- **Heuristic Violated:** Perception
- **Supporting:** NN6, AC: Findable
- **Issue:** The Swap button is styled as a ghost/secondary button at the bottom of each slot card. On the AMS view, swapping is the *only* user-triggered action available, yet it's visually subordinate to static metadata.
- **Severity:** [2] Minor
- **Impact:** Users scan for action affordances near the top of a card or as a dominant element. Burying the primary action at the bottom increases search time.

---

**P3 — Empty AMS slots offer no action path**
- **Heuristic Violated:** Perception
- **Supporting:** NN1 (Visibility of System Status), AC: Findable
- **Issue:** Empty slots display "empty" text with a hatched background but no CTA or navigation hint. Users must independently know to switch to Inventory and find "+ Add Spool."
- **Severity:** [2] Minor
- **Impact:** Dead-end perception; no visible path forward from an empty state.

---

**P4 — Destructive "✕" in Print Log relies on hover for intent**
- **Heuristic Violated:** Perception
- **Supporting:** NN8 (Aesthetic and Minimalist Design), AC: Clear
- **Issue:** The delete button shows only "✕" with no label. Its destructive function (delete print *and* return filament to spools) is only revealed in a tooltip on hover and in the confirmation modal.
- **Severity:** [2] Minor
- **Impact:** Low discoverability of the action's scope — "delete" and "delete + undo filament" are meaningfully different operations.

---

**P5 — COLOR_MAP covers only 7 colors; unmapped colors render as gray**
- **Heuristic Violated:** Perception
- **Supporting:** NN1, AC: Clear
- **Issue:** Slot color bars fall back to `#d1d5db` (light gray) for any color name not in the hardcoded map. A spool named "Marble," "Silk Gold," or "Army Green" would render identically to an uncolored slot.
- **Severity:** [1] Cosmetic
- **Impact:** Reduces the visual utility of the color bar as a quick-scan affordance.

---

### Comprehension

**C1 — Slot numbers are logical (load-order), not physical (AMS position)**
- **Heuristic Violated:** Comprehension
- **Supporting:** NN2 (Match Between System and Real World), AC: Communicative, AC: Credible
- **Issue:** The AMS grid renders "Slot 1, 2, 3, 4" based on `dateLoaded` sort order — the oldest-loaded spool becomes Slot 1. The physical Bambu AMS has fixed slot positions (labeled 1–4 on the machine). A spool in physical Slot 3 might appear as Slot 1 in the dashboard. When a user wants to swap the spool in their physical Slot 2, the dashboard slot numbers are unreliable as a reference.
- **Severity:** [3] Major
- **Impact:** Mental model mismatch between the physical device and the dashboard; can cause the wrong spool to be acted on.

---

**C2 — "Closed/New" is an ambiguous status label**
- **Heuristic Violated:** Comprehension
- **Supporting:** NN2, AC: Clear
- **Issue:** "Closed/New" suggests a spool that is both sealed and new. "Closed" implies a formerly-opened state. The intended meaning is "unopened, sealed spool on shelf." The label conflates two words to describe one state.
- **Severity:** [2] Minor
- **Impact:** Mild taxonomy confusion, especially as the inventory grows and status scanning becomes important.

---

**C3 — Import has same visual weight as Export**
- **Heuristic Violated:** Comprehension
- **Supporting:** NN5 (Error Prevention), AC: Communicative
- **Issue:** Import and Export are given identical ghost-style button treatment in the top bar. Import overwrites *all* data; Export is read-only. They should have different visual weight. The confirmation modal is good, but users may not realize they're about to overwrite before clicking Import.
- **Severity:** [2] Minor
- **Impact:** Risk of unintended data loss before the user reaches the confirmation dialog.

---

**C4 — alert() for validation errors breaks the visual system**
- **Heuristic Violated:** Comprehension
- **Supporting:** NN9 (Help users recognize, diagnose, and recover from errors), AC: Communicative
- **Issue:** Two places use native `alert()` for validation feedback: Register Print (empty grams) and Swap modal (no spool selected). The rest of the UI uses inline error states and modals. `alert()` is a jarring, browser-native interruption that breaks the visual context.
- **Severity:** [2] Minor
- **Impact:** Inconsistency in error feedback language erodes confidence in the UI's polish and predictability.

---

**C5 — "Savings" column header lacks currency context**
- **Heuristic Violated:** Comprehension
- **Supporting:** NN2, AC: Clear
- **Issue:** The Print Log column header reads "Savings" without a currency indicator. Cell values show "$" but the header doesn't, making the column ambiguous in isolation.
- **Severity:** [1] Cosmetic

---

### Operation

**O1 — Swap modal doesn't allow marking outgoing spool as Finished**
- **Heuristic Violated:** Operation
- **Supporting:** NN3 (User Control and Freedom), AC: Controllable, AC: Useful
- **Issue:** When swapping filament, the outgoing spool is *always* set to "Open." If the spool is empty (that's why you're swapping), the user must then navigate to Inventory → Edit → change status to Finished — a 3-step detour for the most common swap reason.
- **Severity:** [3] Major
- **Impact:** Common workflow requires unnecessary additional steps; increases chance of stale "Open" status persisting for spent spools.

---

**O2 — Register Print form loses unsaved state on tab navigation**
- **Heuristic Violated:** Operation
- **Supporting:** NN3, AC: Controllable
- **Issue:** Clicking any other tab while the Register Print form is partially filled silently discards all input. There is no navigation guard, warning, or draft persistence.
- **Severity:** [2] Minor
- **Impact:** Easy to lose work mid-entry; particularly risky if user needs to check Inventory for a spool's remaining weight before completing the form.

---

**O3 — No path from empty AMS slot to adding a spool**
- **Heuristic Violated:** Operation
- **Supporting:** NN3, AC: Useful
- **Issue:** Empty slot cards have no "Add Spool" or "Load from Inventory" action. Users must navigate independently to Inventory to take action.
- **Severity:** [2] Minor
- **Impact:** Breaks expected task flow: see empty slot → fill it.

---

**O4 — No undo for deletion; Export is the only recovery mechanism**
- **Heuristic Violated:** Operation
- **Supporting:** NN3, AC: Controllable
- **Issue:** Deleting a print permanently removes it and modifies spool weights. The confirmation modal prevents accidents, but there is no undo. Recovery requires a previous Export backup.
- **Severity:** [2] Minor
- **Impact:** Low risk for a personal tool, but the filament weight adjustment makes deletion high-consequence.

---

## Phase 3: Prioritized Recommendation Matrix

### Perception — Grade: B

The layout is clean, the visual hierarchy is sound, and the component system is consistent. Issues are affordance-level, not structural.

| Issue | Severity | Recommendation |
|---|---|---|
| P1 — "Register Print" tab looks like a button | 2 | Style consistently with other tabs, or move it out of the tab bar as a standalone CTA above the content area |
| P2 — "Swap Filament" visually buried | 2 | Increase button prominence on the slot card — consider `btn-secondary` weight or position it more visibly |
| P3 — Empty slots have no action affordance | 2 | Add a subtle "Load spool →" link inside empty slots that navigates to Inventory |
| P4 — "✕" delete intent not scannable | 2 | Replace with a text label ("Delete") or pair the icon with a visible label; don't rely on tooltip alone for destructive intent |
| P5 — Unmapped colors render as gray | 1 | Expand COLOR_MAP, or implement a fallback that generates a color from the color name string |

---

### Comprehension — Grade: C

One major conceptual mismatch (slot numbering) undermines trust in the data display. The rest are label and interaction copy issues.

> **Note:** The slot numbering issue (C1) warrants investigating the underlying mental model before fixing. Validate: do you want dashboard slots to map to physical AMS positions? If yes, that requires adding a "physical slot" field to the spool data model.

| Issue | Severity | Recommendation |
|---|---|---|
| C1 — Slot numbers don't match physical AMS positions | 3 | Add a fixed "AMS slot" field (1–4) to loaded spools and render by that, OR clearly label dashboard slots as "logical" to set expectations |
| C2 — "Closed/New" label is ambiguous | 2 | Rename to "Sealed" or "New" — single-concept label scans faster in the inventory table |
| C3 — Import has same visual weight as Export | 2 | Give Import a more cautionary treatment (warning icon or label: "Import — replaces all data") |
| C4 — `alert()` breaks error consistency | 2 | Replace both `alert()` calls with inline error messages matching `.input-error` style |
| C5 — "Savings" column header lacks "$" | 1 | Update header to "Savings (USD)" or "Savings ($)" |

---

### Operation — Grade: C

Two meaningful workflow gaps. The swap-to-finished gap is the most impactful because it applies to one of the most frequent real-world interactions.

> **Note:** Trace through your own actual swap workflow before building fixes. When you swap a spool, how often is it because it's empty vs. because you want a different color? That frequency determines urgency of the Finished-status gap.

| Issue | Severity | Recommendation |
|---|---|---|
| O1 — Swap modal can't mark spool as Finished | 3 | Add a "Mark as Finished" option to the swap modal, branching outgoing spool status between Open and Finished |
| O2 — Register Print loses state on tab change | 2 | Add a navigation guard when the form has unsaved input — warning dialog or lightweight localStorage draft |
| O3 — No action path from empty AMS slot | 2 | Add an "Add Spool" shortcut inside empty slot cards that navigates to Inventory or opens the Add Spool modal |
| O4 — Deletion has no undo | 2 | Surface "Export before deleting" as a reminder in the delete confirmation modal |

---

## Severity Reference

| Score | Label | Meaning |
|---|---|---|
| 0 | No Issue | Compliance met |
| 1 | Cosmetic | Fix if time permits |
| 2 | Minor | Low priority fix |
| 3 | Major | High priority; severely impedes user flow |
| 4 | Catastrophe | Imperative to fix; completely blocks user progression |




---

## Next Steps

**If this evaluation precedes user research:**
Bring these findings into `thematic-analysis-processor` as a heuristic baseline when you analyze your session data. The synthesis will track which findings are reinforced or contradicted by human-provided feedback — distinguishing what an expert review predicted from what users actually experienced.

**If this evaluation is standalone:**
Pass these findings to `insights-to-action` to generate a stakeholder-ready executive readout or framework-mapped action plan.

---

[Back to Gems](README.md) | [Back Home](../README.md)

