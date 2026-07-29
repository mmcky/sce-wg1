---
title: Special Issue Proposal — The Semantics of Economic Models
authors:
  - name: Working Group on Language and Formal Semantics
    affiliations:
      - Society for Computational Economics
abstract: |
  We propose a special issue of the Journal of Economic Dynamics and Control
  on the semantics of economic models — stated accounts of what model files,
  toolkits, and estimation procedures mean, fixed independently
  of any solver.   Each paper supplies a semantic ontology: a map from what is written to a
  mathematical object, together with what that map takes as given, applied
  to a shared suite of models.   Each account is verified by cross-team use before refereeing, and a joint
  comparison paper closes the issue.
exports:
  - format: pdf
    template: ./templates/plain_latex_wide
    output: exports/JEDC-special-issue-proposal.pdf
  - format: tex
    template: ./templates/plain_latex_wide
    output: exports/JEDC-special-issue-proposal.tex
---

# Special Issue Proposal — The Semantics of Economic Models

*Journal of Economic Dynamics and Control · Working Group on Language and Formal Semantics, Society for Computational Economics · 28 July 2026*

## AI and the Need for a Semantic Ontology

When economists compute an applied model for research or policy, the precise *meaning* of the model is distributed — much of it implicitly — across prose, notation, calibration, and code. A paper says "we solve the following model", but the equations on the page underdetermine what the code computes; the remainder — the relations between economic objects, the timing and information structure, the domains of state variables, the equilibrium assumptions, and the computational choices of discretization and solution concept — is settled silently, inside the implementation.[^implementation]

The meaning at stake is more than variable definitions: it includes the relational structure of the theoretical model — which objects the model is built from and how they determine one another. In a heterogeneous-agent framework, for example, decision rules respond to prices, decisions induce a cross-sectional distribution, and the distribution feeds back into prices. A framework may state much of this structure explicitly, recording which objects determine which; yet what each piece means mathematically, and when the assembled model stands for an equilibrium system, still lives only in code. The only complete statement of the model is therefore often the code of its solution routine, and a model written for one toolkit must be rebuilt before another can solve it, so results are hard to cross-verify.[^mmb]

AI makes the missing statement costly, and the cost is permanent. Language models already write, modify, and translate modelling code; to interpret and verify their output, one must know which economic objects the machine is computing and which relations among them it is enforcing — and neither the code nor the incomplete equations on the page make that statement. Nor will better models remove the need: a language model's output is probabilistic by construction, so there must always be an independent statement of meaning to check it against, and once language models call solvers in a loop, an unchecked error compounds across iterations instead of sitting in one file awaiting review. Industry met the same problem first: an enterprise's data presupposes a conceptual model of the business — customers hold accounts, orders ship to addresses — that was never written down, so these relations are now deduced back out of the data and held as conjectures pending verification.[^aws] Economics is in the opposite and better position: the relations among a model's objects are not patterns waiting to be discovered but the theory itself, stated in the paper yet never attached to the files and function calls that compute it. Supplying that meaning in a form shared by economists and readable by machines lets every reading be checked rather than guessed.

The objective of this special issue is to supply the missing statement: a concrete meaning map for the declarative languages and frameworks in current use in computational economics. The exercise is practical rather than foundational — the accounts state the relations as they stand in working computation, not a general model theory for economics. Economists already settle one question of meaning before computation: what a parameter means in terms of the data, and whether it is identified, is fixed before any estimator of it is computed (Koopmans and Reiersøl 1950). No comparable requirement applies to the operations, files, function calls, and procedures in which models are written. We call the missing statement a **semantic ontology**: an account of what a model representation means, settled before, and independently of, how it is solved.

[^implementation]: A change of implementation may preserve the estimates or change them, and both cases are on record in one issue of *Econometrica*: Su and Judd (2012) show that two implementations of one estimator return the same estimates, while Dubé, Fox and Su (2012) show that a loose tolerance on the inner-loop contraction of the standard demand estimator returns incorrect parameter estimates, with own-price elasticities differing from the tightly converged values by roughly a factor of two. Where the implementation is the only statement of the model, nothing independent says which of the two has occurred.

[^mmb]: The field's closest remedy, the Macroeconomic Model Data Base (Wieland et al. 2012), imposes a common policy rule and common shocks on models that keep their own equations — comparability achieved without stating what any model means.

[^aws]: "Build a semantic ontology to power AI assistants on AWS — Part 1", AWS Database Blog, 14 July 2026: "raw schemas lack the semantic relationships and business context that models need to reason effectively, and no amount of technical metadata compensates for missing meaning."

## Semantic Ontology for Economists

An account of meaning — a semantics — has three parts (Harel and Rumpe 2004): the written form of a model; the mathematical objects that serve as meanings, specified independently of any notation; and a map carrying each written form to the object it stands for, stated as an explicit function rather than left to convention. An account also lists what a representation takes as given: the economic objects — agents, states, shocks, the timing, the equilibrium concept — and the relations among them, meaning which objects determine which, and in what order. Such an inventory of objects and relations is an ontology (Gruber 1993); the map and the inventory together are the semantic ontology of the opening section.

> **Example (shock timing).** A paper writes "a policy shock raises entrants at date $t$." The sentence does not pin down the model: under one convention the shock reaches the cross-sectional distribution at $t$ and time-$t$ prices respond; under another it reaches the distribution at $t+1$, through a mid-period transition, and prices respond a period later. Each convention lives in hand-written code and comments, and the impulse response differs before any grid or solver is chosen.

Each part alone falls short. A file format or a list of model classes describes only the syntax. A catalogue of mathematical objects with no stated map from what is written into them omits the part that does the work. And a demonstration that files run and produce numbers is a fact about one implementation, not an account of what the files mean. The standard every account meets is checkability: it is stated precisely enough that an implementation, a translation, or model code written by a language model can be checked against it.

Econometrics has maintained the object side of this apparatus since Koopmans and Reiersøl (1950): a structure generates a distribution of observables, two structures are observationally equivalent when they generate the same distribution, and identification is the condition that the correspondence be one-to-one. On the computational side progress is also partial: the sequence-space Jacobian toolkit already states a model's relational structure as a graph of blocks (Auclert et al. 2021). What no toolkit states is the map from its files and function calls into such objects; a semantic ontology supplies precisely this map. The papers' results are accordingly theorems about a stated map: the conditions under which it is defined, proofs that two representations or two implementations denote the same object, and statements of what a solver preserves of it. The form is familiar: the equivalence of the sequence problem and the functional equation (Stokey, Lucas and Prescott 1989, Theorems 4.2–4.3) is exactly such a theorem — two independently defined meanings of one description, agreeing under a stated boundedness condition.

## The Papers

Each team states what its own object means — a toolkit's model files, an estimation method's specification, or the standing model class of a research area — in the formalism it judges appropriate. No toolkit and no formalism is the template for the others, and where the accounts differ, the difference is a result for the closing comparison to report. The subject is the meaning of representations and procedures, not of the mathematics they describe: what a Bellman equation means is settled; what a given Dynare file or HARK model means is not.

Every paper answers the same four questions, in a common short format placed at the front of the paper, and applies its answers to at least one model from a shared suite. Together these answers constitute the paper's semantic ontology:

1. **What is written down.** The representation the account interprets: the model file, the sequence of construction calls, or the specification of an estimation exercise.
2. **What it stands for.** The mathematical object the representation denotes, fixed independently of any solver — an operator on a stated function space, a system of equations in sequence space, a population parameter, or whatever the account requires.
3. **When the interpretation holds.** The domains, units, timing, and information conditions under which that object is well defined, and the parameter restrictions the account assumes.
4. **What preserves it.** Which changes to what is written leave the object unchanged, which refine an approximation to it, and which replace it with a different object.

The results the issue asks for are theorems about these answers. The papers fall into four areas — model-language syntax, toolkits, estimation methods, and the model classes of economics' sub-disciplines — with cross-cutting work on solvers, translation, and machine checking. Submissions are invited on, but are not restricted to:

- **Model languages.** What a file in a language with a fixed grammar denotes, stated once alongside the grammar, so that every model's meaning is an instance of one map. Dynare's model language, Dolo, and HARK's model files are the obvious cases.
- **Toolkits.** For toolkits with construction operations rather than a grammar — the sequence-space Jacobian toolkit (Auclert et al. 2021), the VFI Toolkit, HARK's agent classes — what each construction stands for, how the meaning of a combination follows from the meanings of its parts, and what the toolkit requires of any function the user supplies. In the sequence-space Jacobian toolkit much of the structure is already stated — a model is a directed graph of household, firm, and market-clearing blocks with declared unknowns, targets, and exogenous paths, in substance an ontology of the model — and what remains unstated is the map: what each block's interior denotes, and the conditions under which the assembled graph stands for an equilibrium system. A toolkit may appear under both kinds: whether HARK's model files and its agent classes agree on one model is itself a question for a paper.
- **Estimation methods.** For a method with no model file — the simulated method of moments — the specification format does not exist in advance; constructing it, then stating which population parameter a specification defines and the theorem under which the procedure recovers it, is the paper's contribution. What belongs to the model and what to its implementation is settled by a theorem, not a convention: the weighting matrix affects only efficiency under correct specification, but under misspecification, with the parameter vector overidentified, it determines the probability limit (Hall and Inoue 2003, p. 363). The closest precedent treats Bayesian inference this way (Ścibior et al. 2018), leaving convergence to ordinary probability theory, so the existing asymptotic theory is reinterpreted rather than replaced.
- **Model classes and research areas.** Which objects a class of models is built from, how they relate, which combinations count as a model, and when two descriptions are the same model — an ontology of the class in Gruber's sense, stated in one formalism and translatable into each toolkit's representation. Heterogeneous-agent macroeconomics is one case: sequence-space and state-space accounts agree numerically where both apply, but the sequence-space account excludes models whose value function depends on the distribution of agents — money search, and overlapping generations with mid-life bequests (Auclert et al. 2021) — so what each account can represent is a question about the objects it commits to, not about numerics. The payoff of stated relations is measured, not conjectural: the JEL codes last had a major revision in 1990, while computer science maintains an automatically generated ontology of its research areas whose typed relations matched human experts in classification tasks where the same vocabulary used as flat keywords fell significantly short of them (Salatino et al. 2020). A mathematical generalization — an abstract dynamic program, for example — proves theorems over many models at once without stating what any representation means; on its own it does not meet the call.
- **Solvers, translations, and machine checks.** For at least one suite model, which numerical choices leave the denoted object unchanged, which refine an approximation to it, and which change the solution concept; meaning-preserving translation between toolkits, including the cases where none exists and why; and reports of using a stated account to check implementations, translations, or machine-written model code, with the failures reported.

## Organisation of the Issue

### Format and Verification

We follow the format this journal has used twice (den Haan, Judd and Juillard 2010, 2011): a suite of models fixed and published before the papers are written, independent papers by teams working in different traditions, and a comparison paper. Ours would be written jointly by the participating teams — as in the second of those issues — and would close the issue.

The suite is fixed and published before the call closes and is publicly archived independently of the issue: [an Aiyagari–Bewley–Huggett economy, a medium-scale New Keynesian model, and a lifecycle model with discrete choice — to be confirmed by the working group].

Before refereeing, each account is used by a team other than its authors, who apply it to the suite — working out what each model says, modifying it, translating it — and write a short report saying where the account is silent or wrong. The report is published alongside the paper and is sent to the referees. The guest editors assign the pairs. No paper is refereed by a member of the team that wrote it or by the team that verified it. We propose six to eight papers and one comparison, with a session at the Society's conference between submission and revision.

### Teams and Editors

The working group's twelve members include developers of Dynare, HARK, and the VFI Toolkit. Committed teams: [to be listed — only teams that have agreed in writing]. Guest editors: Akshay Shanker and Matthew N. White, co-chairs of the working group, and [name, institution], from outside it. Papers are submitted through the journal's editorial system, marked for this special issue, and are refereed under the journal's ordinary standards; no paper is handled by an editor from its own team.

### Timeline

- Call for papers on acceptance
- Suite published at three months
- Submissions at nine months
- Verification by other teams at twelve months
- Referee reports at fifteen months
- Revisions and the comparison paper by twenty-four months

## References

Auclert, A., B. Bardóczy, M. Rognlie, and L. Straub (2021). "Using the Sequence-Space Jacobian to Solve and Estimate Heterogeneous-Agent Models." *Econometrica* 89(5), 2375–2408.

den Haan, W. J., K. L. Judd, and M. Juillard (2010). "Computational suite of models with heterogeneous agents: Incomplete markets and aggregate uncertainty." *Journal of Economic Dynamics and Control* 34(1), 1–3.

den Haan, W. J., K. L. Judd, and M. Juillard (2011). "Computational suite of models with heterogeneous agents II: Multi-country real business cycle models." *Journal of Economic Dynamics and Control* 35(2), 175–177.

Dubé, J.-P., J. T. Fox, and C.-L. Su (2012). "Improving the Numerical Performance of Static and Dynamic Aggregate Discrete Choice Random Coefficients Demand Estimation." *Econometrica* 80(5), 2231–2267.

Gruber, T. R. (1993). "A translation approach to portable ontology specifications." *Knowledge Acquisition* 5(2), 199–220.

Hall, A. R., and A. Inoue (2003). "The large sample behaviour of the generalized method of moments estimator in misspecified models." *Journal of Econometrics* 114(2), 361–394.

Harel, D., and B. Rumpe (2004). "Meaningful modeling: what's the semantics of 'semantics'?" *Computer* 37(10), 64–72.

Koopmans, T. C., and O. Reiersøl (1950). "The Identification of Structural Characteristics." *Annals of Mathematical Statistics* 21(2), 165–181.

Salatino, A. A., T. Thanapalasingam, A. Mannocci, A. Birukou, F. Osborne, and E. Motta (2020). "The Computer Science Ontology: A Comprehensive Automatically-Generated Taxonomy of Research Areas." *Data Intelligence* 2, 379–416.

Ścibior, A., O. Kammar, M. Vákár, S. Staton, H. Yang, Y. Cai, K. Ostermann, S. K. Moss, C. Heunen, and Z. Ghahramani (2018). "Denotational Validation of Higher-Order Bayesian Inference." *Proceedings of the ACM on Programming Languages* 2(POPL), article 60.

Stokey, N. L., and R. E. Lucas Jr., with E. C. Prescott (1989). *Recursive Methods in Economic Dynamics.* Harvard University Press.

Su, C.-L., and K. L. Judd (2012). "Constrained Optimization Approaches to Estimation of Structural Models." *Econometrica* 80(5), 2213–2230.

Wieland, V., T. Cwik, G. J. Müller, S. Schmidt, and M. Wolters (2012). "A new comparative approach to macroeconomic modeling and policy analysis." *Journal of Economic Behavior & Organization* 83(3), 523–541.
