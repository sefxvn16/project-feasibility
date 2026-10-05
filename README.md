# project-feasibility

**English** | [Tiếng Việt](README.vi.md)

A Claude skill for building and analyzing project financial feasibility models (cash flow, NPV, IRR, Payback, sensitivity analysis, investment conclusion) for **preliminary internal decisions** on a specific project: a new investment, an M&A deal or a business partnership. Its focus is assumption discipline: every input is labeled, the work moves through three phases with a stop after each, and assumptions cannot be adjusted to make the result look better.

> The skill instructions (`SKILL.md`) are currently written in Vietnamese. Technical terms (NPV, IRR, Fact, Estimate, Assumption, F1–F3…) are kept in English.

## What it does

A feasibility model can look reasonable at the end even when an early assumption is wrong, and there is a pull in the other direction too: quietly tuning inputs until the NPV looks right. The skill works against both with three rules.

**1. Every statement carries exactly one label**

- **Fact**: sourced, observable or published.
- **Estimate**: always given as a range, never a single number.
- **Assumption**: an internal assumption, used only when no reliable Fact or Estimate exists.

**2. A one-way, three-phase pipeline with a stop after each phase**

| Phase | Does | Does not |
|---|---|---|
| **F1 — Data & Assumptions** | Labels inputs, rates their reliability, records gaps and out-of-model risks | Calculate, evaluate, conclude |
| **F2 — Modeling & Calculation** | Follows your file template, or proposes a file structure for approval first; builds a traceable model (inputs / formulas / outputs kept separate), calculates NPV, IRR, Payback | Create or change assumptions, run sensitivity, interpret |
| **F3 — Analysis & Decision** | Sensitivity, break-even, scenario comparison, conclusion | Change inputs or formulas, drop the bad case, promise returns |

After each phase the skill presents the result and waits for the user to confirm before moving on. Changing an assumption means going back to F1, with the reason stated and the impact on later phases recorded.

**Model file rules (F2)**

- If you provide a template, the model follows it. Without one, the skill first proposes the sheets, their content and the main rows and columns, and builds the file only after you agree.
- No hidden formulas: every calculation is a visible formula in the file. No pasted values, no hidden sheets, rows or columns, no IFERROR to mask errors.
- Font colors: **blue** for hand-entered inputs, **black** for formulas, **green** for links to other sheets (your template's convention wins if it has one), with a legend in the file.
- Before handing over the file, the skill recalculates it and checks for formula errors (#NUM!, #DIV/0!, #REF!, #VALUE!, #NAME?, #N/A, #NULL!) and circular references. An error caused by the inputs is reported and sent back to F1, not fixed by changing inputs.

**3. A fixed conclusion format**

The conclusion is always **Go**, **No-go** or **Go-with-conditions**, argued from NPV, IRR, sensitivity and break points, with no automatic numeric cut-off. Go-with-conditions must state the concrete conditions under which Go no longer holds.

The skill also asks before filling a missing input. It only creates an assumption if the user allows it, and it prefers stating "no data" over giving uncertain information. It also stops on a fixed list of request phrases that signal a breach of assumption discipline (for example "just make the IRR look better").

## Boundaries

- For **preliminary internal decisions** only. It does not cover corporate financial statements, audits, bank loan or investment fund applications, or formal valuations. In those cases it says it does not apply instead of adapting.
- It does not search for data on its own unless asked directly.
- It is not professional financial, investment or legal advice.
- It does not depend on any other skill.

## Folder structure

```
project-feasibility/
  SKILL.md
README.md
README.vi.md
LICENSE.md
```

## Installation

### Claude apps (claude.ai, Claude desktop)

1. Download the repo and zip the `project-feasibility` folder on its own into `project-feasibility.zip` (the zip must contain the `project-feasibility` folder at its top level).
2. Open Claude, go to **Customize → Skills**, click **+** → **Create skill** → **Upload a skill**, and choose `project-feasibility.zip`. Menu names and locations may differ between app versions. Skills require code execution to be enabled.
3. Check that `project-feasibility` appears in the list and is turned on.

### Claude Code

Copy the `project-feasibility` folder into `~/.claude/skills/` (available in all projects) or into a project's `.claude/skills/`, then restart Claude Code.

## Usage

The skill triggers when a request concerns the financial feasibility of a project. In Claude Code you can also call it directly with `/project-feasibility`. Examples:

- "Here is the capex, price and volume data for a 50-room hotel. Build a feasibility model."
- "We have the F2 results. Run sensitivity on price and occupancy and tell me whether it is worth investing."

Expect the skill to stop at the end of F1 and F2 and ask for confirmation, even when you ask it to "go straight to the model".

## Limitations

- The workflow has not been empirically validated. The design rationale in SKILL.md is a hypothesis.
- The forbidden phrases in section 9 are listed verbatim in Vietnamese. The skill does not say whether paraphrases or other languages should trigger the same stop.
- The skill does not say how to calculate when the environment cannot run code or spreadsheets.
- Section 3.3 asks for sensitivity analysis in F3, while section 8 forbids "new calculation" in F3. Whether re-running the F2 model with changed inputs counts as new calculation is not spelled out.
- When a key input (such as the discount rate) is missing and the user does not allow an assumption, the skill records the gap but does not say whether F2 should compute the metrics that do not need it.

## Feedback

Please send feedback through the repo's **Issues**. To make it easier to act on, include:

- your request and the type of project (with personal or confidential information removed);
- the phase where the problem happened (F1, F2 or F3);
- the result you expected and the result you got.

Feedback is especially welcome on: the skill triggering when it should not (or not triggering), stops that feel too strict or too loose, cases where the Fact / Estimate / Assumption labels are hard to apply, the limitations listed above, and instructions that are hard to follow.

## License

Released under **CC BY-NC 4.0**: free for non-commercial use with attribution. For commercial use, please contact the author via **Issues**. Provided as-is, without warranty. See [LICENSE.md](LICENSE.md).
