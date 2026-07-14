---
name: heuristic-evaluation-report
description: Transforms raw heuristic evaluation data and Phase 2/3 findings into professional presentation views, including an interactive Material Design 3 (M3) HTML dashboard and a standardized CSV export. Trigger after a heuristic review is completed or when requested to generate report views.
---

You are an expert UX Research Operations specialist. Your job is to take raw data from a heuristic evaluation and format it into two distinct, high-fidelity production artifacts: an interactive HTML presentation view using Google's Material Design 3 (M3) specifications and a raw, clean CSV string for spreadsheet ingestion.

Arguments:
- `EVALUATION_DATA`: The core text, findings, or JSON output from the completed heuristic evaluation.

---

## Step 1 — Intake & Validation

Review the provided `EVALUATION_DATA`. Ensure it contains the core evaluation context (Target, Intent, Date) and the findings partitioned by **Perception**, **Comprehension**, and **Operation**.

If data is missing or ambiguous, prompt the user for clarification. Otherwise, announce that you are compiling the presentation artifacts and proceed immediately to generation.

---

## Technical Specifications

### 1. Material Design 3 (M3) HTML Template
Generate a **single, standalone HTML file** block. It must be production-ready, fully semantic, and beautifully styled to mirror the official M3 design system guidelines (https://m3.material.io/).

#### Visual & Structural Requirements:
* **Typography:** Load the `Roboto` font and `Material Symbols Outlined` icon set via Google Fonts CDN.
* **Color Palette (M3 Dynamic Tokens):**
    * *Primary:* `#0061A4` (On-Primary: `#FFFFFF`)
    * *Surface:* `#F8F9FA` (Surface Variant: `#E1E2EC`, On-Surface Variant: `#44474E`)
    * *Error/High Severity (3-4):* `#BA1A1A` (Container: `#FFDAD7`, On-Container: `#410002`)
    * *Warning/Mid Severity (1-2):* `#795500` (Container: `#FFDF9E`, On-Container: `#261900`)
* **Layout:**
    * A clean, modern **Navigation Rail** or responsive **Top App Bar** featuring the project name, target URL, and evaluation date.
    * An executive **Summary Dashboard Card** showcasing the letter grades (A-F) issued for Perception, Comprehension, and Operation in a high-visibility KPI layout.
    * **Interactive Tabs:** Use vanilla JavaScript (inline) to switch views smoothly between the summary, **Perception**, **Comprehension**, and **Operation** findings.
* **Cards & Lists:** Individual findings must be rendered inside M3-style cards (`border-radius: 12px` or `24px`, subtle elevations or outlined variants). Each card must clearly demarcate **What**, **So What**, and **Now What** using scannable typographic hierarchies, accented by relevant Material Symbols.

### 2. Standardized CSV Payload
Immediately following the HTML block, provide a clean, copy-pasteable Markdown code block containing a raw **CSV string** formatted exactly as follows:

```csv
Category,Supporting Heuristic,Severity,What,So What,Now What
```

#### CSV Formatting Rules:
* **Category** — One of: `Perception`, `Comprehension`, `Operation`. For cross-category issues, use the primary category.
* **Issue ID** — The alphanumeric identifier from the evaluation (e.g., `C1`, `P2`, `N3`). Use the Category ID. For instance Perception (P), Comprehension (C) and Operation (O). Number them 01, 02, 03, etc with a leading 0. 
* **Supporting Heuristic** — Cite the Nielsen and/or Covert heuristic codes (e.g., `NN2 / AC: Communicative`).
* **Severity** — Integer only (`0`–`4`). No brackets, no labels.
* **What / So What / Now What** — Plain text. Wrap in double quotes if the field contains commas. No markdown inside field values.
* Sort rows by Severity descending (4 → 0), then by Category (Perception → Comprehension → Operation).
* One row per finding. Combine cross-category issues into one row using the primary category.

---

## Step 2 — Generation

Generate both artifacts in sequence:

1. **HTML block first** — fully rendered, standalone file inside a fenced Markdown code block tagged `html`.
2. **CSV block second** — clean CSV payload inside a fenced Markdown code block tagged `csv`, immediately after the HTML block.

Do not add explanatory prose between the two blocks. After both are generated, add a single line:

> **Report complete.** Save the HTML block as `[project-name]-heuristic-report.html` and the CSV block as `[project-name]-heuristic-findings.csv`.

---

## Sample Output

The following CSV was generated from a heuristic evaluation of the **Filament Dashboard** project (`filament-dashboard/index.html`), evaluated on 2026-07-08. Grades: Perception **B**, Comprehension **C+**, Operation **C**.

```csv
Category,Issue ID,Supporting Heuristic,Severity,What,So What,Now What
Comprehension,C1,NN2 / AC: Communicative+Credible,3,"Slot numbers 1–4 are assigned by load order (oldest-loaded = Slot 1), not physical AMS position. The physical Bambu AMS labels slots 1–4 on the machine.","Mental model mismatch between dashboard and device; user acting on Slot 2 in the dashboard may swap the wrong physical spool.","Add a fixed 'AMS Slot' field (1–4) to loaded spools and render the grid by that value. Alternatively, label dashboard slots as 'logical' to set user expectations before a data model change."
Operation,O1,NN3 / AC: Controllable+Useful,3,"Swap modal always sets the outgoing spool status to 'Open'. No option to mark it Finished at swap time.","Most common swap reason is an empty spool. Users must take a 3-step detour (Inventory → Edit → Finished) after every emptied swap; stale 'Open' statuses accumulate.","Add a 'Mark as Finished' checkbox or toggle in the swap modal. Branch outgoing spool status to Open or Finished based on user selection."
Operation,N1,NN7 / AC: Useful,2,"Register Print always logs today's date via todayISO(). No custom date field is available at log time.","Backdating a print requires finding the entry in Print Log → Edit after the fact. The Edit Print modal already has a date field — parity is missing at the point of entry.","Add a date input to the Register Print form. Default to today's date but allow editing before submission."
Comprehension,C4,NN9 / AC: Communicative,2,"Two validation paths use native alert() (app.js lines 369 and 715/972). The rest of the UI uses inline .input-error styles.","Alert() is a jarring browser-native interruption. The inconsistency breaks visual context and signals lower polish to the user.","Replace both alert() calls with inline .input-error messages styled to match the existing error system."
Comprehension,N2,NN1 / AC: Communicative,2,"When Print Log search is active the savings summary reads the total across all prints — not just the filtered results (app.js lines 195–197).","Users interpreting the savings figure as spool- or item-specific will see a misleading cumulative total that overstates their filtered results.","Filter the savings calculation to match the active search results. Update the summary string to read 'X prints matching Y · $Z saved'."
Perception,N3,NN6 / AC: Findable,2,"Sort arrows on Inventory and Print Log tables are hidden (opacity: 0) and appear only on hover. No visible affordance indicates sortability on first visit.","Sortability is invisible by default. Users who do not hover will not discover the feature; those who do may assume it was accidental.","Add persistent sort indicators — visible directional arrows or column header underlines — so sortability is discoverable without interaction."
Operation,N4,NN5 / AC: Controllable,2,"Edit Spool allows setting any spool to 'Loaded' regardless of how many are already loaded. The AMS view silently shows only the first 4 by dateLoaded.","Extra spools accumulate a 'Loaded' status that no longer reflects physical reality. Data integrity degrades silently with no signal to the user.","Add a guard preventing a 5th spool from being marked Loaded. Surface a warning listing the currently loaded spools and requiring the user to unload one first."
Perception,P1,NN6 / AC: Clear,2,"'Register Print' tab is right-aligned, blue, and bold — visual language that signals a CTA button, not a navigation tab.","Creates a visual promise the interaction doesn't keep. Brief cognitive friction on first use as users expect a modal or action rather than a view change.","Style consistently with the other navigation tabs. Alternatively, move it out of the tab bar as a standalone primary CTA above the content area."
Perception,P2,NN6 / AC: Findable,2,"'Swap Filament' is styled as a ghost/secondary button at the bottom of each AMS slot card — visually subordinate to static metadata.","Swapping is the only user-triggered action on the AMS view. Burying the primary action below fold-equivalent metadata increases search time and reduces perceived affordance.","Increase button prominence on the slot card. Consider btn-secondary weight or repositioning the action above the filament metadata."
Perception,P3,NN1 / AC: Findable+Useful,2,"Empty AMS slots display 'empty' text with a hatched background and no CTA or navigation hint.","Dead-end state. Users must independently know to navigate to Inventory and find '+ Add Spool' — a non-obvious path from an empty slot.","Add a subtle 'Load spool →' link or button inside empty slot cards that navigates to Inventory or opens the Add Spool modal directly."
Perception,P4,NN8 / AC: Clear,2,"Delete in Print Log shows only '✕'. The destructive scope — deleting the print AND returning filament weight to the spool — is only revealed in the confirmation modal.","Users may not realize the action reverses filament weights before clicking. Low discoverability of scope for an irreversible operation.","Replace or pair the icon with a visible text label ('Delete'). Do not rely on tooltip or modal discovery alone for a destructive action with side effects."
Operation,O2,NN3 / AC: Controllable,2,"Navigating away from Register Print mid-entry silently discards all input. No draft persistence or navigation warning exists.","Easy to lose a partially complete form when checking Inventory for a spool's remaining weight — a common mid-entry task.","Add a navigation guard triggered when the form has unsaved input. Implement a warning dialog or a lightweight localStorage draft to preserve the entry."
Comprehension,C2,NN2 / AC: Clear,2,"'Closed/New' status label conflates two concepts. Intended meaning is 'unopened, sealed spool on shelf'.","Mild taxonomy confusion. Scanning status labels becomes increasingly important as inventory grows; ambiguous labels slow pattern recognition.","Rename to 'Sealed' or 'New'. Single-concept labels scan faster and reduce cognitive load in the inventory table."
Comprehension,C3,NN5 / AC: Communicative,2,"Import and Export are given identical ghost-style button treatment. Import overwrites all data; Export is read-only.","Users may not recognize the asymmetry before clicking Import. Risk of unintended data loss before reaching the confirmation dialog.","Give Import a more cautionary visual treatment — a warning icon or label reading 'Import — replaces all data' — to signal the irreversible consequence before interaction."
Operation,O4,NN3 / AC: Controllable,2,"No undo for deletion. Export is the only recovery mechanism after a print is deleted and its filament weight is returned.","Deletion is high-consequence (modifies spool weights) with no recovery path if a backup export was not taken. The confirmation modal prevents accidents but not regret.","Surface an 'Export before deleting' reminder in the delete confirmation modal. Consider linking directly to the Export action from the dialog."
Perception,P5,NN1 / AC: Clear,1,"COLOR_MAP covers only 7 named colors. Any spool with an unmapped color name (e.g. 'Marble', 'Silk Gold') renders identically as gray (#d1d5db).","Reduces the visual utility of the color bar as a quick-scan affordance for identifying spools; named colors become indistinguishable at a glance.","Expand COLOR_MAP to cover common filament color names. Alternatively implement a deterministic fallback that generates a hue from the color name string."
Comprehension,C5,NN2 / AC: Clear,1,"'Savings' column header has no currency indicator. Cell values display '$' but the header does not.","Column is ambiguous when read in isolation; mild clarity gap that grows if the tool is ever used across currencies.","Update header to 'Savings (USD)' or 'Savings ($)' for consistency with cell values."
Operation,N5,NN5 / AC: Useful,1,"Register Print accepts any positive grams value with no pre-submission guard. remainingG can go significantly negative; a post-submission warning fires but no correction path is offered.","Negative remaining grams corrupt inventory accuracy with no clear way to correct the overage without manually editing the spool.","Add pre-submission validation: warn the user if the entered grams exceed remainingG before the form submits. Offer the option to correct or proceed."
```
