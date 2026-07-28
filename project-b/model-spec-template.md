# Baseline model specification — template

**Status: draft for review.** One specification per model group, authored by that group's model
specification architect. Implementations and tutorials are submitted against a frozen version of
this document.

The governing rule: **pin the economics, leave the method free.** If a statement here would force
every toolkit to solve the problem the same way, it belongs in section 5 (what is deliberately left
free), not in sections 2–4.

---

## 0. Identity

| Field | Value |
| --- | --- |
| Model name | |
| Group | |
| Specification version | v0.1 (draft) |
| Architect | |
| Status | draft / comment / frozen |
| Source paper(s) | |
| Comment window closes | |

## 1. Scope

Two or three sentences: what this model is, why it was chosen for this group, and what a reader
should be able to compare across implementations once it exists.

## 2. Environment

State the model as the source paper states it, resolving anything the paper leaves implicit.

- Agents and their problem
- **Timing convention** — say explicitly when the state is measured and when shocks are realized;
  this is the single most common source of results that fail to line up
- Functional forms, written out
- Budget and borrowing constraints
- Market clearing conditions
- Definition of equilibrium
- Normalizations (units of assets, price level, population)

## 3. Calibration

Every parameter, with its source. Prefer "as in the source paper, Table N" over a fresh choice.

| Parameter | Symbol | Value | Source | Notes |
| --- | --- | --- | --- | --- |
| | | | | |

Frequency: (quarterly / annual, and how any converted parameters were converted.)

## 4. Exogenous processes

Give the **targets**, not the discretization: the continuous process and the moments an
implementation must reproduce. How a toolkit discretizes it is its own business, and the differences
that produces are part of what the library exists to show.

| Process | Specification | Target moments | Tolerance |
| --- | --- | --- | --- |
| | | | |

## 5. Deliberately left free

State this positively, so nobody implements defensively:

- Solution method and algorithm
- Grid construction, bounds, and density
- Discretization scheme for exogenous processes
- Convergence criteria beyond the reported tolerances
- Language, code structure, and API

## 6. Reported objects

The comparison contract. Keep it small — every entry is something four teams must produce and agree
on. Give the shape, the units, and the convention for each.

| Object | Shape / type | Units and convention | Tolerance | Notes |
| --- | --- | --- | --- | --- |
| Steady-state interest rate | scalar | annualized, net | | |
| Capital-output ratio | scalar | annual | | |
| Wealth Gini | scalar | | | |
| Policy function | array on the stated common grid | | | |
| IRF | array, H periods, stated shock and size | % deviation from steady state | | |

Common evaluation grid (if any), stated exactly:

Output file layout: one file per implementation, at `results/<toolkit>/<object>.csv`, plus a
metadata file recording the specification version it targets.

## 7. Documented deviations

A project that cannot match one element exactly implements the rest and records the deviation here,
rather than dropping out. Deviations are published alongside the results.

| Toolkit | Element | Deviation | Reason | Expected effect on reported objects |
| --- | --- | --- | --- | --- |
| | | | | |

## 8. Divergence findings

Where two implementations differ beyond tolerance, record it here and attribute it to method. These
are results of the exercise, not defects. **No timings and no ranking of toolkits in Phase 1.**

| Object | Implementations | Size of divergence | Attributed to | Resolved? |
| --- | --- | --- | --- | --- |
| | | | | |

## 9. Open questions

One row per unresolved question, linked to its issue. The specification cannot freeze while any
question marked *blocking* is open.

| # | Question | Blocking? | Issue | Resolution |
| --- | --- | --- | --- | --- |
| | | | | |

## 10. Changelog

A frozen specification changes by version, so existing implementations are never silently
invalidated. Implementations record which version they target.

| Version | Date | Change | Affects existing implementations? |
| --- | --- | --- | --- |
| v0.1 | | Initial draft | — |
