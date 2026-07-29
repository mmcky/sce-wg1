# Call for Papers — The Semantics of Economic Models

*Special issue of the Journal of Economic Dynamics and Control · Working Group on Language and Formal Semantics, Society for Computational Economics · draft to accompany the proposal, 27 July 2026*

A model's meaning is distributed across prose, notation, calibration, and code. A model can be solved while its timing, information structure, the domains of its state variables, or its solution concept remain implicit, and in toolkits where a model is built by calling functions rather than written as a file, the only complete statement of the model is the code of its solution routine. Two consequences follow. A model written for one toolkit must be rebuilt before another can solve it, so results are hard to cross-verify. And a change of implementation may leave the estimates unchanged or may not, with nothing on the page to say which. Su and Judd (2012) show that recasting a nested fixed point as a constrained optimization problem solves the same estimation problem and returns the same estimates; Dubé, Fox and Su (2012), in the same issue of *Econometrica*, show that a loose tolerance on the inner-loop contraction of the standard demand estimator returns incorrect parameter estimates, with own-price elasticities differing from the tightly converged values by roughly a factor of two. Where the implementation is the only statement of the model, nothing independent says which of the two has occurred. Model code written by a language model raises the same difficulty, since there is no explicit statement of meaning against which to check it.

Economists already require this of estimation, under the name identification: whether a parameter is identified is settled before any estimator of it is computed. This issue asks the same of the files, function calls, and procedures in which models are written.

## What a paper does

Each team states what its own object means — a toolkit's model files, an estimation method's specification, or the standing model class of a research area — in the formalism it judges appropriate. No toolkit and no formalism is the template for the others, and where the accounts differ, the difference is a result for the closing comparison to report.

Following Harel and Rumpe (2004), an account of meaning has three parts: a syntax — what may be written; a semantic domain — the mathematical objects that serve as meanings; and a mapping from the first to the second, given as a definite function. Each part alone falls short. A file format or a list of model classes describes only the syntax. A catalogue of mathematical objects with no stated map from what is written into them omits the part that does the work. And a demonstration that files run and produce numbers is a fact about one implementation, not an account of what the files mean. The standard every account meets is checkability: it is stated precisely enough that an implementation, a translation, or model code written by a language model can be checked against it, and the verification step below exercises exactly this.

Every paper answers the same four questions, in a common short format placed at the front of the paper, and applies its answers to at least one model in the shared suite:

1. **What is written down.** The representation the account interprets: the model file, the sequence of construction calls, or the specification of an estimation exercise.
2. **What it stands for.** The mathematical object the representation denotes, fixed independently of any solver — an operator on a stated function space, a system of equations in sequence space, a population parameter, or whatever the account requires.
3. **When the interpretation holds.** The domains, units, timing, and information conditions under which that object is well defined, and the parameter restrictions the account assumes.
4. **What preserves it.** Which changes to what is written leave the object unchanged, which refine an approximation to it, and which replace it with a different object.

The results the issue asks for are theorems about these answers, and their form is familiar. The equivalence of the sequence problem and the functional equation (Stokey, Lucas and Prescott 1989, Theorems 4.2–4.3) is exactly such a theorem: two independently defined meanings of one description, agreeing under a stated boundedness condition. Two representations proved to denote the same object, a translation proved to preserve what a file means, a procedure proved to recover the object a specification defines — each topic below asks for results of this kind.

## Topics

Submissions are invited on, but are not restricted to:

- **Declarative model languages.** What a file in a language with a fixed grammar denotes, stated once alongside the grammar, so that every model's meaning is an instance of one map. Dynare's model language, Dolo, and HARK's model files are the obvious cases.
- **Frameworks whose models are built by calling functions.** For toolkits with construction operations rather than a grammar — the sequence-space Jacobian toolkit, the VFI Toolkit, HARK's agent classes — what each construction stands for, how the meaning of a combination follows from the meanings of its parts, and what the toolkit requires of any function the user supplies. A toolkit may fall under both headings: HARK acquired model files alongside its agent classes, and whether the two descriptions of one model agree is a question a paper can answer.
- **Estimation and solution methods.** Saying, for a method that has no model file, what a complete specification of one exercise of it consists of, then stating which population parameter that specification defines and the theorem under which the procedure recovers it. Papers may find, as the simulated method of moments illustrates, that what belongs to the model and what belongs to its implementation is settled by a theorem rather than by convention: under correct specification the weighting matrix affects efficiency but not what is estimated, while under misspecification, with the parameter vector overidentified, the probability limit of the estimator depends on the limit of the weighting matrix (Hall and Inoue 2003, p. 363). For a method of this kind the specification format does not exist in advance, and constructing it is the paper's contribution. The closest published precedent treats Monte Carlo inference this way (Ścibior et al. 2018): each representation of the method carries a stated meaning, a transformation of the method is correct exactly when it preserves that meaning, and convergence is left to ordinary probability theory — so the existing asymptotic theory of simulated estimators is re-read rather than replaced, with consistency as the statement that every admissible implementation recovers the object the specification defines.
- **Model classes and research areas.** Which objects a class of models is built from, how they relate, which combinations count as a model, and when two descriptions are the same model — an ontology of the class in Gruber's (1993) sense: stated in one common formalism and translatable into each toolkit's own representation, rather than tied to any one of them. Heterogeneous-agent macroeconomics is one case. Sequence-space and state-space accounts agree numerically where both apply, so the difference between them is not one of results; but the sequence-space account does not admit models whose value function depends on the distribution of agents, which excludes money-search models and overlapping-generations models with bequests received in mid-life (Auclert et al. 2021). What each account can represent at all is therefore a question about the objects it commits to, not about its numerical properties. A paper of this kind interprets no notation, and its obligations differ accordingly: state the entities, their relations, the conditions under which a combination of them is a well-posed model, and the criteria under which two descriptions are the same model. A mathematical generalisation that subsumes many models so that a theorem is proved once — an abstract dynamic program, for example — is a different kind of work: it proves results over instances without stating what any representation means, and on its own it does not meet the call.
- **What a solver preserves.** For at least one model in the shared suite, which numerical choices leave the object the model stands for unchanged, which refine an approximation to it, and which change the solution concept.
- **Translation between toolkits.** Meaning-preserving translation of a model from one toolkit's representation into another's, including the cases where no such translation exists and the reason it does not.
- **Machine-checked accounts.** Reports of using a stated account of meaning to check an implementation, a translation, or model code written by a language model, with the failures reported.

## The shared suite and verification by other teams

All papers draw from a single shared suite of models. The suite is fixed and published before this call closes and is publicly archived independently of the issue: [an Aiyagari–Bewley–Huggett economy, a medium-scale New Keynesian model, and a lifecycle model with discrete choice — to be confirmed by the working group].

Before refereeing, each account is used by a team other than its authors, who apply it to the suite — working out what each model says, modifying it, translating it — and write a short report saying where the account is silent or wrong. The report is published alongside the paper and is sent to the referees. The guest editors assign the pairs. No paper is refereed by a member of the team that wrote it or by the team that verified it.

## Submission

Papers are submitted through the journal's editorial system, marked for this special issue, and are refereed under the journal's ordinary standards. Both complete papers and advanced drafts are considered for the workshop; only complete papers enter refereeing.

- Submission deadline: [date]
- Workshop, between submission and revision: [session at the Society's conference, date]
- Final acceptances: [date]

**Guest editors.** Akshay Shanker and Matthew N. White, co-chairs of the working group, and [name, institution], from outside the working group.

## References

Auclert, A., B. Bardóczy, M. Rognlie, and L. Straub (2021). "Using the Sequence-Space Jacobian to Solve and Estimate Heterogeneous-Agent Models." *Econometrica* 89(5), 2375–2408.

Dubé, J.-P., J. T. Fox, and C.-L. Su (2012). "Improving the Numerical Performance of Static and Dynamic Aggregate Discrete Choice Random Coefficients Demand Estimation." *Econometrica* 80(5), 2231–2267.

Gruber, T. R. (1993). "A translation approach to portable ontology specifications." *Knowledge Acquisition* 5(2), 199–220.

Hall, A. R., and A. Inoue (2003). "The large sample behaviour of the generalized method of moments estimator in misspecified models." *Journal of Econometrics* 114(2), 361–394.

Harel, D., and B. Rumpe (2004). "Meaningful modeling: what's the semantics of 'semantics'?" *Computer* 37(10), 64–72.

Ścibior, A., O. Kammar, M. Vákár, S. Staton, H. Yang, Y. Cai, K. Ostermann, S. K. Moss, C. Heunen, and Z. Ghahramani (2018). "Denotational Validation of Higher-Order Bayesian Inference." *Proceedings of the ACM on Programming Languages* 2(POPL), article 60.

Stokey, N. L., and R. E. Lucas Jr., with E. C. Prescott (1989). *Recursive Methods in Economic Dynamics.* Harvard University Press.

Su, C.-L., and K. L. Judd (2012). "Constrained Optimization Approaches to Estimation of Structural Models." *Econometrica* 80(5), 2213–2230.
