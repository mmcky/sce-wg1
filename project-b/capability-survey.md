# Toolkit capability survey — proposed content

**Status: draft for co-chair review.** This document is the *content* of the survey, written so it
can be reviewed as a whole and then transcribed into a form tool question by question. It is not the
form itself.

Each question below gives its wording, its type, and its answer options. Metadata for the person
building the form is in italics under the question. Dates are left as ⟨TBC⟩.

- **Purpose.** Determine which baseline models each Project B group can realistically adopt. The
  responses compose the capability matrix; the intersection of what a group's toolkits can actually
  solve defines its feasible baselines.
- **Proposed delivery.** Google Form, sent to invited projects with a pre-filled link. Enable
  *collect email* and *allow response editing after submit*. Responses stay private; the derived
  capability matrix is published after each project confirms its own row.
- **Target length.** 15 minutes. Sections 1, 2 and 6 are required; 3, 4 and 5 can be completed by a
  project's technical lead if that is a different person.

**For review:** the three decisions worth settling before this becomes a form are (a) whether it
ships as part of WG1 sign-up or separately to Project B participants only, (b) whether section 5
belongs here at all or in a later round, and (c) how hard to push on question 6.3, which is how
specification architects get recruited.

---

## Form introduction

*Shown above the first question.*

> This survey builds the capability matrix for Project B, the community library of baseline models.
> We use it to work out which baseline model each group can realistically adopt — a baseline is only
> useful if every toolkit in the group can actually solve it.
>
> It should take about 15 minutes. Please answer for what your toolkit does **today**, not what it
> could be made to do. "Not supported" is a useful answer and counts against nobody: the point is to
> find the models that work for everyone, not to rank toolkits. Project B publishes no timings and
> no ranking.
>
> We will publish a capability matrix derived from these answers, and will send you your project's
> row to confirm before anything goes public. You can edit your response at any time using the link
> you receive after submitting.
>
> Questions: ⟨co-chair contact TBC⟩

---

## Section 1 — Project and contact

*Not published. Required.*

### 1.1 Your name
*Short answer · required*

### 1.2 Email
*Short answer · required · or use Forms' automatic email collection*

### 1.3 Project name
*Short answer · required*

### 1.4 Repository URL
*Short answer · required*

### 1.5 Primary implementation language(s)
*Checkboxes · required · Python / Julia / MATLAB / C or C++ / Fortran / R / Rust / Other*

### 1.6 Code licence
*Short answer · required*

### 1.7 Licence for documentation and tutorial text
*Short answer · Help: "Project B publishes text under CC-BY. Tell us if that is a problem for your project."*

### 1.8 Who would author and maintain your project's contributions?
*Paragraph · Help: "Names or roles. This is who we would coordinate with, and who receives authorship credit."*

---

## Section 2 — Model classes

### 2.1 Which of these does your toolkit solve?
*Multiple-choice grid · required · one answer per row*

**Columns:** In production · Partial · Not supported · Planned

**Rows:**

- Incomplete-markets heterogeneous agents, stationary equilibrium (Aiyagari-class)
- Heterogeneous agents with aggregate uncertainty (Krusell–Smith-class)
- HANK, one asset
- HANK, two or more assets
- Representative-agent DSGE, linear
- Representative-agent DSGE, nonlinear or global
- Overlapping generations
- Life-cycle / finite-horizon problems
- Agent-based macro
- Search and matching / labour

*Help: "In production means a user could do this today with documented support. Partial means it can
be done but needs work from the user, or only in a restricted case — explain in 2.2."*

### 2.2 For anything you marked Partial, what is the limitation?
*Paragraph*

### 2.3 What else is your toolkit built for that is not listed above?
*Paragraph · Help: "Particularly anything that would make a good author's-choice showcase."*

---

## Section 3 — Methods and structure

*These determine whether a given specification is implementable in your toolkit at all.*

### 3.1 Time
*Multiple choice · Discrete / Continuous / Both*

### 3.2 Horizon
*Checkboxes · Infinite / Finite / Overlapping generations*

### 3.3 Which solution methods are available?
*Checkboxes · Value function iteration / Policy iteration or Howard improvement / Endogenous grid method / Projection or collocation / Perturbation, first order / Perturbation, second order or higher / Sequence-space Jacobian / Transition path or MIT shock / Simulation-based / Other*

### 3.4 How does the toolkit treat aggregate risk?
*Multiple choice · No aggregate risk, stationary equilibria only / Perfect-foresight transitions (MIT shocks) / Linearized around the steady state / Global solution with aggregate risk / Other*

### 3.5 Discretization of idiosyncratic processes
*Checkboxes · Tauchen / Rouwenhorst / Adda–Cooper / Simulation / The user supplies the discretized process / Other*

*Help: "Project B specifications state the target moments of an exogenous process, not how to
discretize it — how your toolkit does this is one of the differences the library exists to show."*

### 3.6 Which of these does the toolkit handle?
*Multiple-choice grid · one answer per row*

**Columns:** Yes · Partial · No

**Rows:**

- Occasionally-binding constraints
- Portfolio choice / multiple assets
- Adjustment costs
- Discrete choice
- Non-convexities

### 3.7 How many continuous individual state variables can it handle comfortably?
*Dropdown · 1 / 2 / 3 / 4 or more*

### 3.8 How is the distribution represented?
*Checkboxes · Histogram or discretized density / Simulated panel of agents / Continuous density or spline / Other*

### 3.9 Is calibration or estimation built in?
*Checkboxes · None / Moment matching or SMM / Maximum likelihood / Bayesian / Other*

---

## Section 4 — Objects the toolkit reports

### 4.1 Which of these can a user obtain?
*Multiple-choice grid · required · one answer per row*

**Columns:** Natively · With modest user code · Not really

**Rows:**

- Steady-state aggregates (r, K/Y, C/Y, …)
- Policy functions evaluated on a grid the user specifies
- The stationary distribution
- Distributional statistics (Gini, percentile shares)
- Impulse responses
- Sequence-space Jacobians
- Welfare measures
- Simulated panels
- Transition paths between steady states

*Help: "These become the reported objects in a specification — the small set of outputs every
implementation in a group produces so results can be compared. The honest answer is more useful than
the generous one."*

### 4.2 What formats can results be written to?
*Checkboxes · CSV / JSON / HDF5 / NetCDF / .mat / In-memory objects only / Other*

---

## Section 5 — Running it in the library

*Phase 1 promises CI that runs every implementation and flags breakage. These answers tell us what
that infrastructure has to support.*

### 5.1 Can it run headless on Linux in CI?
*Multiple choice · Yes / No / Unsure*

### 5.2 Does it require a commercial licence?
*Multiple choice · No / MATLAB core only / MATLAB plus toolboxes / A commercial solver / Other*

### 5.3 If yes, is there a free path?
*Paragraph · Help: "Octave compatibility, a free solver, a container, an academic licence — anything that lets a reader run the model without a paid licence."*

### 5.4 Roughly how long does a stationary Aiyagari-class solve take?
*Multiple choice · Under 10 seconds / 10–60 seconds / 1–5 minutes / 5–30 minutes / Over 30 minutes / Not applicable*

*Help: "A rough order of magnitude, for CI planning only. Project B publishes no timings."*

### 5.5 Are dependency versions pinned, and do you run CI today?
*Paragraph · Help: "A link to your CI configuration is the easiest answer."*

### 5.6 Notebook support
*Checkboxes · Jupyter / Pluto / MATLAB Live Script / Quarto / None / Other*

---

## Section 6 — Taking part

### 6.1 Which model group(s) do you expect to join?
*Checkboxes · required · Incomplete-markets heterogeneous agents / HANK / DSGE / Agent-based macro / Undecided*

### 6.2 Could you commit a baseline implementation by ⟨date TBC⟩?
*Multiple choice · required · Yes / Yes, with support / Not on that timeline / Undecided*

### 6.3 Would you be willing to author the specification for your group?
*Multiple choice · Yes / Maybe, tell me more / No*

*Help: "Each group has one model specification architect who writes the baseline specification the
group implements against. It is the most influential role in Project B and the most work."*

### 6.4 Provisional topic for your author's-choice showcase
*Paragraph · Help: "The tutorial where you show what your toolkit is actually built for. A rough idea is fine — nothing is binding."*

### 6.5 Anything else the group should know?
*Paragraph*

### 6.6 Publication
*Checkboxes, single item · required*

> I understand that a capability matrix derived from these answers will be published, and that my
> project's row will be sent to me to confirm first.

---

## Appendix — Form settings

| Setting | Value | Why |
| --- | --- | --- |
| Collect email addresses | On | Needed to send the matrix row back for confirmation |
| Allow response editing after submit | On | Capabilities change; projects should correct their own entry rather than us re-surveying |
| Limit to one response per person | Off | One response is per *project*, and the delegate may differ from the invitee |
| Sign-in required | Off | Do not make a Google account a condition of taking part |
| Response destination | Linked sheet | The sheet is the working capability matrix before it is published |
| Progress bar | On | Six sections; people should see the end |
| Section logic | None | Simpler to keep all sections visible than to branch on 2.1 |
