# Reusable Prompt Templates for Human-AI Mathematical Research Workflows

This file organizes the Grover case-study prompt material into reusable template types and adds three auxiliary templates requested by the revision process. The prompts below are intentionally written as domain-neutral templates. Users should instantiate them with their own mathematical objects, assumptions, verification tools, and failure modes.

Important use note: these are not meant to be generic writing prompts. Before running a template, replace bracketed slots such as `[domain]`, `[objects]`, `[known results]`, `[failure modes]`, and `[verification tools]` with substantive expert knowledge from the target area. A good instantiated prompt should name the relevant mathematical structures, standard theorems, admissible operations, boundary cases, and proof obligations. Leaving the slots vague weakens the verification checks and can make the model produce broad but unusable advice.

## 1. Scoping and Topic Conceptualization

Role: You are an expert in [domain A] and [domain B].

Expertise requirement: Use concrete expert knowledge from these domains, including standard objects, canonical examples, known theorems, typical assumptions, and common failure modes. Do not give generic research-methodology advice.

Goal: Identify concrete, analyzable research questions connecting [domain A topic] and [domain B topic].

Context:
- Domain A objects: [insert concrete objects, such as states, operators, graphs, equations, distributions, or variational families].
- Domain B objects: [insert concrete objects, such as manifolds, objectives, dynamics, estimators, algorithms, or proof systems].
- Known anchor results: [insert nearby theorems, algorithms, examples, or limitations].
- Available verification tools: [insert symbolic identities, small numerical checks, formal tools, counterexample search, or expert proof checks].

Tasks:
1. Restate the relevant objects on both sides using the supplied domain notation.
2. Propose 5-8 candidate research directions. For each direction, list the core idea, objects, assumptions, nearest known results, possible gap, and likely proof tools.
3. For each direction, include feasibility notes: degenerate cases, boundary examples, expected theorem or complexity guarantee, and reasons the statement might fail.
4. Rank the directions by mathematical clarity, novelty, and verifiability.

Output: a compact numbered list. Avoid speculative claims disconnected from the supplied domain theory.

## 2. Sharpened Claims and Validation Plan

Role: You are a theoretical mathematician specializing in [domain/interface].

Expertise requirement: Insert domain-specific concepts into the analysis. Use named structures, standard reductions, invariants, admissible operations, and known obstructions from [domain/interface]. Avoid a template-level answer that could apply to any field.

Current idea: [insert rough idea connecting the two settings].

Supplied background:
- Mathematical setting: [insert spaces, objects, maps, updates, objectives, or observables].
- Structural constraints: [insert symmetries, invariants, admissible operations, conservation laws, oracle/query rules, smoothness assumptions, etc.].
- Existing theory: [insert closest known results or expected analogies].
- Verification gates: [insert line-by-line proof checks, boundary cases, numerical stress tests, or formalization targets].

Tasks:
1. Identify the mathematical objects on both sides, including the state space, objective or target property, admissible updates, and progress measures.
2. State structural properties and symmetries that should be preserved.
3. Propose candidate theorem statements and validation checks that distinguish intrinsic structure from coordinate artifacts or implementation artifacts.
4. Classify each candidate as ready for proof, suitable as a conjecture, or likely too broad.

Output: theorem candidates, validation checks, and a proof-feasibility assessment.

## 3. Direct Proof With No Fabricated References

Role: You are a careful mathematical assistant collaborating with human experts in [domain].

Expertise requirement: Use only domain facts that are either supplied in the prompt or standard named results in [domain]. If a required fact is not supplied or standard, flag it as a proof obligation instead of inventing a citation.

Target theorem: [insert theorem statement].

Assumptions and notation:
[insert all assumptions, variable domains, objects, conventions, and admissible operations].

Rules:
1. Restate all assumptions, notation, domains, and objects.
2. Give a numbered, line-by-line proof. Every nontrivial inference must be justified.
3. Cite only standard named results by their usual names. Do not fabricate papers, lemma names, or references.
4. Mark any step that requires an extra assumption or an external theorem not explicitly provided.
5. After the proof, list adversarial checks a human reader should perform, including degenerate cases, boundary cases, notation checks, and citation-status checks.

Return only:
- a LaTeX proof environment;
- a short itemized list of adversarial checks.

## 4. Prove-or-Disprove Branching

Role: You are participating in a prove-or-disprove workflow in [domain].

Expertise requirement: Use concrete constructions, invariants, canonical examples, and obstruction mechanisms from [domain]. The disproof branch should be as domain-informed as the proof branch.

Target statement: [insert uncertain statement].

Assumptions and allowed tools:
[insert domains, admissible objects, standard facts, and any computational checks allowed].

Proceed in two explicit branches.
1. Proof branch: try to prove the statement using concrete constructions, basis expansions, invariants, variational principles, standard theorems, or other supplied domain tools.
2. Disproof branch: search for obstructions, counterexamples, boundary cases, hidden assumptions, and incompatible known results.

Within each branch, give line-by-line reasoning and identify any step whose validity depends on an extra assumption. End with a final verdict: proved, disproved, or unresolved under the stated assumptions.

Return only the two branches, the verdict, and adversarial checks.

## 5. Candidate-Conclusion Discovery

Role: You are helping with theorem discovery for a fixed setting in [domain]. The assumptions are fixed; the useful conclusions are not yet known.

Expertise requirement: Generate candidates that reflect the supplied mathematical structure. At least some candidates should use domain-specific invariants, normal forms, comparison principles, algebraic identities, geometric reductions, or complexity/progress measures.

Setting:
[insert fixed assumptions, update rule or model, variables, ranges, objective, and admissible operations].

Known expert hints:
[insert structures that may matter, such as invariant subspaces, conserved quantities, commutator identities, monotonicity formulas, sharp examples, or known limiting regimes].

Tasks:
1. Restate all assumptions, domains, and variable ranges.
2. Propose concise candidate statements. Tag each as invariant, norm identity, scalar recursion, spectral property, convergence guarantee, stability statement, normal form, obstruction, counterexample family, or another useful type.
3. For each candidate, explain why it might be useful and what quick check could falsify it.
4. Select a coherent subset of surviving statements and package them into a theorem-style proposition with numbered parts.
5. Give short derivations for the selected statements and list adversarial checks.

Return: candidate list with pass/fail/inconclusive labels, final proposition, proof sketch, and adversarial checks.

## 6. Transfer Schema Extraction

Role: You are collaborating with human experts on theorem discovery and cross-setting transfer.

Expertise requirement: Extract the actual structural mechanism of the baseline result, not just its surface wording. Use domain-specific objects from both settings and state which pieces of expert knowledge must be supplied before transfer is credible.

Baseline result: [insert proven result from the original setting].
Original setting: [insert objects, assumptions, proof mechanism, and verification checks].
New setting: [insert modified or related objects, assumptions, and available checks].

Tasks:
1. Extract the reusable structural schema from the baseline result, such as invariant subspaces, conserved quantities, tangent or feasible directions, scalar progress coordinates, admissible updates, comparison inequalities, and proof mechanism.
2. State which assumptions appear essential and which may be relaxed.
3. Transfer the schema to the new setting by proposing analogous statements.
4. For each proposed transferred statement, list required checks and likely failure modes.
5. Provide a theorem-ready statement only for claims that survive the stated checks.

Output: schema, transfer notes, candidate statements, and proof obligations.

## 7. Property-Constrained Object Synthesis

Role: You are helping synthesize [target object] in [domain].

Expertise requirement: Use the concrete admissible building blocks, algebraic/geometric constraints, and edge cases supplied below. Do not merely say that a search should be performed; propose domain-specific candidates and tests.

Setting:
[insert fixed data, ambient space, admissible generators or building blocks, parameter ranges, and notation].

Required properties:
(P1) [insert structural property, such as product form, equivariance, feasibility, conservation, or admissibility].
(P2) [insert normalization or boundary property].
(P3) [insert first-order, second-order, approximation, complexity, or correctness property].
(P4 optional) [insert any additional property].

Tasks:
1. Restate all constraints and fixed data.
2. Propose candidate constructions of different sizes or complexities, including short candidates that may fail.
3. For each candidate, write executable Python, MATLAB, or symbolic-check code for finite tests on random and structured seed cases.
4. Include edge cases supplied by the domain expert: [insert edge cases].
5. Report pass/fail outcomes and explain failures.
6. Select the simplest candidate that passes the tests and provide a symbolic proof plan for (P1)-(P3).

Numerical tests are screening evidence only. A symbolic proof or a clearly stated proof obligation is required before acceptance.

Example-instantiation note: if the target object comes from a specific application, replace the placeholders above with that application's admissible building blocks, edge cases, and symbolic proof obligations before running the prompt.

## 8. Constant Discovery and Numerical Stress Testing

Role: You are a mathematical assistant with background in [domain] and [analysis/geometry/probability/optimization area].

Expertise requirement: Use domain-specific norms, inequalities, extremal examples, scaling laws, and structured test cases. Generic random testing is not enough.

Setting:
[insert construction, convention, norm or metric, parameter range, and known inequalities].

Goal:
Find constants [alpha], [beta], ... such that
[insert target inequalities].

Required order:
1. Propose candidate constants and explain the heuristic using the supplied domain structure.
2. Design and perform numerical or symbolic stress tests over random and structured cases.
3. Adjust the constants if the tests reveal violations.
4. Give a theoretical proof using the explicit construction and standard inequalities.
5. Discuss tightness and list worst-case or near-worst-case examples.

Return: candidate constants, test design, test summary, proof outline, and tightness notes.

## 9. Structure-Specific Rate Refinement

Role: You are helping refine a baseline convergence or complexity theorem in [domain].

Expertise requirement: Use the special structure of the target problem, not only a generic smoothness template. Insert the relevant geometry, error-bound condition, sharpness/PL/KL-type inequality, invariant region, or problem-specific comparison principle.

Baseline theorem: [insert baseline statement and rate].
Target quantity: [insert objective, residual, gap, distance, success probability, or error measure].
Algorithm or dynamics: [insert update rule and admissible step-size/parameter regime].

Tasks:
1. Identify the assumptions needed for the baseline theorem.
2. Search for a structure-specific inequality relating the progress measure to the target gap or residual.
3. State the exact region where the refined inequality is expected to hold.
4. Use the baseline descent/ascent/smoothness inequality and the refined inequality to derive the improved iteration or complexity bound.
5. List boundary cases and stress tests that could falsify the proposed constants.

Return a theorem-ready statement and a proof skeleton. Do not hide local assumptions behind vague phrases such as "good initialization".

Example-instantiation note: the refined inequality may be a PL, KL, error-bound, sharpness, invariant-region, or comparison inequality, depending on the target problem. State the exact local or global region before asking the model to derive the rate.

## 10. Prompt Variation and Failure-Mode Check

Role: You are testing how sensitive the workflow is to prompt quality.

Mathematical task:
[insert one concrete task from the target domain].

Domain-specific full prompt ingredients:
- objects and notation: [insert];
- assumptions and variable domains: [insert];
- admissible tools and operations: [insert];
- expert hints or known results: [insert];
- boundary cases and failure modes: [insert];
- required output format: [insert].

Use the same mathematical task under three prompt variants:
A. Full prompt: assumptions, domains, expert knowledge, proof/disproof branch, evidence requirements, and output format are all specified.
B. Missing-assumption prompt: omit variable domains, admissible building blocks, or key expert hints.
C. Numerical-only or evidence-only prompt: request computational or heuristic evidence but no symbolic proof.

For each variant, record:
1. notation drift;
2. hidden assumption changes;
3. unsupported claims;
4. fabricated or vague references;
5. boundary cases omitted;
6. whether numerical evidence is overstated as proof;
7. whether the absence of domain-specific expert knowledge makes the output too generic to verify.


## 11. Computational Environment Log Template

For each prompt run, record:
- task name;
- original GitHub prompt family and template version;
- full prompt text;
- domain-specific information inserted into the template;
- model name and snapshot/date;
- API or local deployment;
- temperature and decoding settings;
- hardware used for any numerical tests;
- Python/MATLAB/symbolic-tool version and package versions;
- accepted output summary;
- rejected output or failure-mode notes;
- human verification steps completed;
- unresolved proof obligations or author-supplied information still needed.

## 12. Optional Second Case Study Scoping Template

Role: You are helping decide whether the human-AI mathematical workflow can be tested on a second, smaller case study.

Expertise requirement: The proposed second case must include enough domain-specific structure for expert verification. Do not recommend a case study that only shows generic prompting behavior.

Goal:
Find a compact case study that is close enough to [original setting] to reuse the propose-check-distill workflow, but different enough to provide evidence beyond the original example.

Candidate settings to consider:
1. [candidate setting 1].
2. [candidate setting 2].
3. [candidate setting 3].
4. [candidate setting 4].

For each candidate, require author-supplied expert information:
- mathematical objects and notation;
- nearest known results;
- admissible operations or update rules;
- expected theorem-level deliverable;
- verification tools and boundary cases;
- likely failure modes.

Tasks:
1. For each candidate setting, identify the mathematical object, assumptions, target statement, and expected verification tools.
2. State what would count as a minimal theorem-level deliverable: invariant, structural identity, synthesis property, convergence statement, complexity bound, or counterexample.
3. List the prompt templates from this file that would transfer directly and the templates that would need modification.
4. Give failure modes, including missing invariant structure, uncheckable assumptions, dependence on unavailable numerics, or lack of expert-verifiable proof obligations.
5. Rank the candidates by feasibility for a short revision addendum.

Return:
- a comparison table;
- one recommended second case study;
- a minimal prompt sequence for that case;
- a list of author-supplied information required before the case can be reported.

Important:
Do not claim that the second case has been validated. Treat this as a scoping protocol unless the authors run the prompts, verify the outputs, and add the resulting theorem or negative evidence to the manuscript.
