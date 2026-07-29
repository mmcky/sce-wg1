# Project A — The Semantics of Economic Models

*Research brief for the SCE Working Group on Language and Formal Semantics · revised draft · 21 July 2026*

**What this is.** A research project of the working group, aimed at a journal special issue. The question is open: **what are the semantic ontologies that can enable the use of AI for economic modelling?** Here *enable* is meant broadly: AI that interacts with models and with interoperable solvers robustly, transparently, and accurately — finding and reading models, modifying and translating them, driving solvers across toolkits. The foundation for all of it is checkability: AI already produces modelling code, and what is missing is the explicit statement of meaning against which its readings, its edits, and its solver runs can be verified. Each participating team develops an answer for its own toolkit or tradition and publishes it as a paper; the special issue collects the answers. A single semantic meaning layer may not emerge. The semantics natural to Dynare's model language may differ in kind from the semantics natural to a heterogeneous-agent or dynamic-programming toolkit, and where the accounts differ, the differences are findings that will inform what interoperability can actually mean.

Two constraints bound the pluralism. Each account must be **formal**: stated precisely enough that an implementation, or an AI proposal, can be checked against it, because an informal semantics cannot adjudicate when two implementations disagree. And each must state its **ontology**: what the model's expressions refer to and what entities they commit us to. Formality alone is not enough; the same formal system admits many interpretations, and only stated commitments say which is intended (Guizzardi and Guarino 2024). An account that meets both constraints is what we call a **semantic ontology**, and the research question is which semantic ontologies the field's toolkits turn out to need.

## Motivation

A model's meaning is currently distributed across prose, notation, calibration, code, and toolkit conventions. A model can run while its timing, information structure, domains, solution concept, or numerical assumptions stay implicit. In many toolkits, much of the meaning lives inside the solution routine; how much of it can be inspected, varied, or checked from outside is itself a question each team is best placed to answer for its own tool. The working group's founding problem follows: models do not travel between toolkits, and results are hard to cross-verify. AI raises the stakes. Larger context windows and vector search improve retrieval, but retrieval does not supply a statement of what a model is.

The argument that AI needs semantics was made elsewhere first. In knowledge representation it is decades old: shared vocabularies with stated commitments let independently built systems interoperate (Gruber 1993; Guarino, Oberle and Staab 2009). Systems biology learned it in practice, adopting common model-description standards (SBML; MIRIAM) because models could not otherwise move between tools. The recent AI literature arrives from the other side: explaining a symbolic description, including one an AI system produced, means revealing the commitments that make its statements true — what Guizzardi and Guarino (2024) call *ontological unpacking*. Grounding language models in explicit knowledge structures also measurably improves their accuracy (Sequeda, Allemang and Jacob 2023), though accuracy is not yet checkability, which is the harder target here. Economic modelling faces the same raw ingredients: many tools, overlapping mathematics, meaning embedded in code. The semantic layer is the missing piece.

## A working definition

As orientation, offered to be revised, we read "the semantics of an economic model" as an explicit account of: (1) what its expressions and components denote; (2) the domains, units, assumptions, timing, and information under which they are interpreted; (3) how they compose to determine behaviour, equilibrium, solution, and observables; and (4) which translations and transformations preserve, refine, or change those meanings. A label, an embedding, or a prose summary is not by itself a semantics; it becomes one when it is tied to a defined referent, rule, or validity condition with a testable interpretation.

Concretely, take a model fragment:

```
V(a) = max_{0 ≤ c ≤ a}  u(c) + β·V(R·(a − c)),        u(c) = c^(1−γ)/(1−γ)
```

A semantic ontology for the file this lives in states, at minimum: what `V`, `a`, and `c` refer to (a value function on a stated domain; a state; a control with its feasible set); the restrictions under which the equation is well-posed (β ∈ (0,1), so the induced operator is a contraction; R > 0; γ > 0 with γ ≠ 1 for this utility form, log at the limit); what the equation denotes (an operator on a stated function space, whose fixed point is the model's solution); and which edits preserve that meaning (changing γ recalibrates the same model; adding a borrowing limit changes the feasible set, and with it the denoted operator). Two implementations agree when they compute the same denoted object, and an AI-proposed edit is checkable because the edited file denotes a definite new object.

Each sub-group may sharpen, restrict, or argue against this reading for its own setting; the papers are where positions are staked. The one discipline asked of every account: state your source representation, your semantic domain, your interpretation rules, and your criteria for preservation, equivalence, or acceptable approximation.

## Approaches and instruments

No single kind of account is privileged. Conceptual and ontological accounts (what basic things a model assumes exist, and how they relate), denotational and mathematical accounts (compositional maps from notation to mathematical objects), operational and axiomatic accounts (evaluation rules, invariants, correctness conditions), and mapping and provenance accounts (relating papers, equations, data, and code) are all in scope.

The formal instruments differ too. An account may be written in first- or higher-order logic, in type theory including its categorical forms, or mechanised in a proof assistant such as Lean, which makes a stated semantics checkable by machine as well as by referees. The instrument belongs to the team; the two constraints above are instrument-neutral.

Dynare's, the VFI Toolkit's, HARK's, and the Econ-ARK Bellman project's model representations — the last two from the organisers' own group — each embody semantic choices worth stating on their own terms, and each account is a contribution, not a template for the others.

## The research programme

1. **Shared questions** (jointly, in the first meetings). Fix the questions each paper answers — the four-part reading above, or a team's argued alternative — and a small shared glossary, with working distinctions between the economic model and its numerical treatment offered as hypotheses to test.
2. **Per-toolkit papers** (sub-groups). Each team states what its own toolkit's model representations mean, in the formalism of its choice, unpacking the commitments the representation already carries. Each also documents, for at least one worked example from the shared corpus, what its solver preserves of that meaning — a first characterization, not an equivalence proof.
3. **Verification within the group.** Each stated semantics is exercised by someone other than its authors: another team, or an AI run that another team supervises, uses the account to read, modify, or translate the shared examples. The account is revised where it fails, and failures are findings; where revision cannot be completed in time, the synthesis records where verification stands. The papers then face ordinary journal refereeing.
4. **Comparative synthesis** (jointly, closing the issue). What is common across the accounts, what is genuinely different, what travels between toolkits and what cannot. So that the synthesis has a fixed basis of comparison, every account, whatever its instrument, also answers the four-part reading in a short common format.

> **Relation to Project B.** Project B, the community library of baseline models, supplies the standardized examples this project tests against: every semantics paper treats the same baseline models, the verification experiments of item 3 run on them, and the synthesis compares accounts on shared ground. The projects are run by separate teams, and the dependency runs one way — Project A's verification needs Project B's corpus on a compatible timeline. The corpus is the interface.

The horizon is short to medium term: items 1 and 2 begin immediately; the special issue collects the papers.

## Success criteria

Every paper in the issue states a semantics precise enough that an implementation, or an AI proposal, can be checked against it; states the ontological commitments that fix which interpretation is intended; and has survived another team's attempt to use it. The closing comparison then answers the opening question: whether the semantic ontologies of economic modelling turn out to be one, several, or a family.

## Appendix: key terms

The vocabulary of this brief comes from several fields — programming-language theory, mathematical logic, knowledge engineering. Each entry says what the term means, where it comes from, and what work it can do for economic modelling.

- **Syntax.** The written form of a model: the rules fixing what may be written, carrying no meaning by itself. Every toolkit already has one — its model-file format or model classes.
- **Abstract syntax.** What survives of the syntax when notation is stripped: which constructs a model is built from and how they nest (from compilers). Hierarchical structure gives a tree; when repeated parts are represented once — one period template reused across a lifecycle — a graph, an *abstract syntax graph*. For us: the structured object a model file parses into, before any meaning is assigned.
- **Denotational semantics.** Semantics is the assignment of meaning to syntax; in the denotational style (the Scott–Strachey tradition), each expression *denotes* a mathematical object, and the meaning of a compound is built from the meanings of its parts. For us: a model file denotes the problem it poses — spaces, operators, solution concept — independently of any solver.
- **Operational semantics.** The other common style: meaning given by execution rules, the steps a term induces. For us: the natural style for describing what a solver does, and by the same token closer to one implementation than to toolkit-independent meaning.
- **Compositionality.** The property that the meaning of the whole is determined by the meanings of its parts and the way they are combined. This is what lets a semantics scale from a two-line fragment to a lifecycle model without re-deriving everything.
- **Ontology.** An explicit specification of a *conceptualization*: the concepts and relations chosen to represent a domain (Gruber 1993, as refined by Guarino, Oberle and Staab 2009). For us: the economic commitments of a file — agents, states, shocks, timing, the equilibrium concept.
- **Semantic ontology.** This project's term, defined above: an account that is both formal and states its ontological commitments. (Distinct from "ontological semantics" in computational linguistics, Nirenburg and Raskin 2004.)
- **Knowledge graph.** Entities and relations stored as a labelled graph, built for linking and querying at scale. Strong for provenance — connecting papers, equations, datasets, and code. Industry property graphs carry no semantics of their own; the semantic-web lineage (RDF/OWL) does carry a formal one, though not one tied to any particular economic model.
- **Semantic graph.** A graph representation of one model in which every node and edge has a stated denotation. A knowledge graph indexes many models for retrieval; a semantic graph states the exact meaning of one.
- **Types.** Machine-checkable classifications of expressions that constrain how they may combine, from simple types through dependent and categorical type theory (from logic and programming languages). For us: domains, units, timing, and information constraints can be expressed as types, so that ill-formed models are rejected before anything is solved.
- **First- and higher-order logic.** First-order logic quantifies over individuals; higher-order logic also over functions and sets. Value functions and operators are higher-order objects, so statements about them sit naturally in higher-order or type-theoretic settings, at the price that machine automation is harder there.
- **Proof assistant (e.g. Lean).** Software in which definitions, statements, and proofs are written formally and checked by machine (Lean, Rocq — formerly Coq — and Isabelle). Lean's mathematical library covers much of the general analysis these models rest on — complete metric spaces, the contraction mapping theorem — but the dynamic-programming-specific content is not yet formalized and would be new work for any team choosing this instrument. The relevance is direct even so: a semantics whose claims are mechanised is verified by a checker rather than a referee, and an AI-drafted derivation that is wrong is rejected automatically — provided the formal statement itself captures the intended claim, a correspondence that remains a human judgment.

## Selected foundations

Formal semantics of languages: Scott & Strachey (1971); Stoy (1977); Winskel (1993); Hutton (2023). Semantics of modelling notations: Harel & Rumpe (2004). Ontologies and knowledge sharing: Gruber (1993); Guarino, Oberle & Staab (2009). Semantics, ontology, and explanation: Guizzardi & Guarino (2024). Semantics and AI: Sequeda, Allemang & Jacob (2023). Model-description standards: SBML (Hucka et al. 2003); MIRIAM (Le Novère et al. 2005). Data-stewardship principles: FAIR (Wilkinson et al. 2016). Programme documents: SCE, "AI as Babel Fish for Structural Economics" (2026); WG1 agenda.
