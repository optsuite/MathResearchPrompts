# MathResearchPrompts

This repository contains the prompts associated with the paper:
- Zhijian Lai, Dong An, Jiang Hu, and Zaiwen Wen, A Grover-compatible Manifold Optimization Algorithm for Quantum Search, arXiv:2512.08432 (https://arxiv.org/abs/2512.08432)

For details on the human–AI collaboration protocol and verification procedures, refer to our companion paper:
- Chenyi Li, Zhijian Lai, Dong An, Jiang Hu, and Zaiwen Wen, Advancing Mathematical Research via Human–AI Interactive Theorem Proving, arXiv:2512.09443 (https://arxiv.org/abs/2512.09443)

To reproduce the interactions, please copy the relevant text blocks from the source of README.md.

# Figures

The four cartoons below are drawn by nano banana based on our paper.

![Figure 1](fig/1.png)  
(Fig. 1: Nobita is overwhelmed by quantum computing and optimization theory until Doraemon introduces an “AI helper” that turns the Grover and manifold puzzle into a clear research roadmap.)

![Figure 2](fig/2.png)  
(Fig. 2: The "AI-helper" designs a scheme under the constraints (P1) product form, (P2) identity at t = 0, and (P3) correct initial velocity, ultimately producing the five-factor retraction.)

![Figure 3](fig/3.png)  
(Fig. 3: The human–AI loop performs numerical experiment, discarding candidates that fail basic checks and keeping only structures that can support the proof.)

![Figure 4](fig/4.png)  
(Fig. 4: After completing the derivations and verification, the paper concludes, and the human–AI team celebrates achieving global optimality and convergence guarantees.)

# Prompts 

## Conceptualizing Research Topics with AI

### Early-stage Exploration

You are an expert in both quantum algorithms and mathematical optimization.

I want to identify promising points of contact between quantum algorithms and optimization that could lead to clean, analyzable research problems. You can refer to the paper I give you.

Please do the following:
1. Give a concise briefing that figures out:
   - The main quantum algorithmic primitives that are relevant here.
   - The main optimization paradigms that might interact with them.
   - Typical objectives, loss functions, and structural assumptions on each side.
2. Propose 5-8 concrete candidate research directions at this interface. For each direction, provide:
   - A short description of the core idea.
   - The main mathematical objects and assumptions.
   - The nearest classical or existing results and what gap or limitation they leave.
   - A plausible class of analysis techniques.
3. For each direction, add 2-3 sentences of feasibility notes:
   - Why this direction might admit a clean theorem (or why it might fail).
   - Any obvious degenerate or trivial regimes to watch out for.
   - Whether you expect meaningful complexity or convergence guarantees to be within reach.

Format your answer as a numbered list of candidate directions, each with compact bullet points and feasibility notes. Avoid overly speculative ideas that are disconnected from existing theory.


### Sharpened Claims and Validation Plans: Example 1

You are a theoretical mathematician specializing in the intersection of quantum algorithms and Riemannian optimization. Your goal is to map discrete quantum algorithmic structures onto continuous geometric manifolds.

To construct a foundational theoretical framework that maps the discrete steps of Grover's search algorithm onto continuous Riemannian gradient flows, identifying the necessary mathematical objects and structural correspondences.

We are investigating the geometric foundations of quantum search. Specifically, we hypothesize that Grover's algorithm can be rigorously interpreted as a form of Riemannian optimization. We need to identify the correct geometric setting before attempting a proof.

**Task:** Please provide a detailed theoretical framing for this intersection:

1. **Object Identification:** Define the precise mathematical objects on both sides. This must include the manifold of quantum states and the specific Riemannian gradient update rules that serve as the continuous analog.
2. **Properties and Symmetries:** Analyze the essential properties of Grover iterations, such as unitarity and query complexity. How do these map to the oracle complexity in Riemannian optimization?
3. **Alignment Check:** Identify specific regimes or limiting cases where the standard gradient-like updates and the discrete Grover iterations coincide structurally.


### Sharpened Claims and Validation Plans: Example 2
You are a theoretical mathematician specializing in the intersection of quantum algorithms and Riemannian optimization. You are assisting in structuring a formal research paper.

To translate the theoretical framework into rigorous, checkable mathematical statements and to design a validation plan that distinguishes intrinsic geometric properties from coordinate artifacts.

We have established the basic geometric objects for viewing Grover's algorithm as a Riemannian optimization process. We now need to sharpen this intuition into explicit formulas and provable claims to form the core of a research paper.

**Task:**

1. **Gradient Dynamics Formulation:** Explicitly formulate the state evolution as a gradient-style update equation on the chosen manifold. Define the potential function driving this flow.
2. **Artifact Analysis:** Propose specific mathematical checks to ensure the observed structure is intrinsic to the geometry (coordinate-independent) rather than an artifact of a specific parameterization.
3. **Complexity Statements:** Formulate candidate theorems aimed at recovering the classical $O(\sqrt{N})$ complexity of Grover’s algorithm purely through the convergence analysis of this manifold-gradient framework.
4. **Proof Feasibility Strategy:** Assess the difficulty of these claims. Recommend which statements should be targeted for rigorous proof in the initial paper and which should be presented as conjectures supported by numerical evidence.


## AI-assisted Theorem Proving 
### Prompts and Reply of Section 4.1
In this subsection, we document the exact prompt used to generate the AI-assisted proof in Section 4.1. It illustrates how we guide the model toward rigorous, line-by-line reasoning rather than informal sketches. 

**Prompt to the model**

 **Content:**

 You are a careful mathematical assistant collaborating with human experts.
 When you are asked to prove a statement, you must:
 1. restate all assumptions, notation, and domains of all variables;
 2. give a numbered, line-by-line argument in which every non-trivial inference is explicitly justified;
 3. cite standard results by their usual names (e.g. spectral theorem, Cauchy--Schwarz inequality) and never fabricate new references.

 Prove the following statement in a concise but fully rigorous way. In your proof, you should in particular
 - explain carefully why $\mathrm{grad} f(U)=0$ is equivalent to $[H,\psi_U]=0$, and how this implies that $\psi_U$ is built from eigenstates of $H$ and forces $f(U)$ to take an extremal value;
 - prove both directions of the optimality claim: that $\mathrm{grad} f(U)=0$ implies that $U$ is a global optimizer with $f(U)\in\{0,1\}$, and that any global optimizer must satisfy $\mathrm{grad} f(U)=0$.

 **Theorem.**
 Let $f(U) = \mathrm{Tr}(H U \psi_0 U^\dagger)$ on the unitary group $\mathrm{U}(N)$, and write $\psi_U := U \psi_0 U^\dagger$ for the output state of the circuit $U$. The skew-Hermitian part of the Riemannian gradient of $f$ on $\mathrm{U}(N)$ is
 
 $$
   {\mathrm{grad}} f(U) = [H,\psi_U].
 $$

 Moreover, ${\mathrm{grad}} f(U) = 0$ if and only if $U$ is a global optimizer of $f$ over $\mathrm{U}(N)$; in that case $f(U) \in \{0,1\}$, corresponding respectively to the global minimum $0$ and global maximum $1$.

 **Output format.**
 Return only:
 - (1) a LaTeX `proof` environment with a numbered, step-by-step derivation;
 - (2) a short LaTeX `itemize` list of adversarial checks a reader could perform (for example: degenerate spectrum of $H$, special choices of $\psi_0$, boundary cases where $H=0$ or $H=I$, etc.).

Do not output any text outside these two parts.


### Clear target, uncertain truth

**Content.**
You are a careful mathematical assistant participating in a *prove-or-disprove* workflow. Your task is to analyse the structural statement below about commutators of Hermitian matrices and the Lie algebra $\mathfrak{su}(n)$.

When reasoning about this statement, you must:
1. Restate all assumptions, notation, and domains of the variables (including the ambient space $M_n(\mathbb{C})$, Hermitian and skew-Hermitian conditions, and the trace operator).
2. Run *two* explicit branches:
   - **Proof branch:** Try to show that every traceless skew-Hermitian matrix can be written as a commutator $[A,B]$ with $A^\dagger = A$ and $B^\dagger = B$. Use concrete constructions, basis expansions, or dimension arguments.
   - **Disproof branch:** In parallel, look for structural obstructions or counterexamples. Analyse the subspace spanned by such commutators, check invariants (e.g. trace, eigenvalues, rank), and probe whether some elements of $\mathfrak{su}(n)$ might fail to be commutators.
3. Within each branch, give a line-by-line argument in which every non-trivial inference is explicitly justified.
4. Cite standard facts (e.g. basic properties of commutators, spectral theorem, Lie algebra identities) by their usual names and never fabricate references.
5. After exploring both branches, provide a *final verdict*: decide whether the proposition is true or false. If it is true, present a concise but fully rigorous proof; if it is false, present an explicit counterexample and explain why it fails.

**Target statement (to prove or disprove).**

 **Proposition.**
 The set of commutators of Hermitian matrices
 
 $$
     \mathcal{C}=\{[A, B]: \, A^\dagger=A,\; B^\dagger=B\}
 
 $$
 equals
 
 $$
     \{X\in M_n(\mathbb{C}): \, X^\dagger=-X,\; \mathrm{tr}\, X=0\}
     =\mathfrak{su}(n).
 $$

**Required output format.**
Return only the following three parts, in order, all in LaTeX:
1. A **Proof branch** subsection with a numbered, step-by-step derivation attempting to prove the proposition.
2. A **Disproof branch** subsection with a numbered, step-by-step analysis searching for obstructions or counterexamples.
3. A **Final verdict** paragraph stating clearly whether the proposition is true or false, together with either a complete proof or a concrete counterexample, followed by a short `itemize` list of adversarial checks a human reader could perform.
Do not output any commentary outside these three parts.

### Rich proofs and aha-moment

The part of the model outputs that inspired us to obtain Theorem \ref{thm: aha} is as follows.
 **Part of the reply from the model**

 **The Invariant ``Jordan'' Plane (Working Subspace):**
 Because $H$ is a projector and $\psi_0$ is rank-one, the evolution is strictly confined to the Krylov subspace $\mathcal{K} = \text{span}\{ |\psi_0\rangle, H|\psi_0\rangle \}$.
 - *Algebraic reason:* The operators $H$ and $\psi_0$, when restricted to the subspace containing $|\psi_0\rangle$, form a closed $2\times 2$ algebra (a single Jordan block of the pair $\{H, \psi_0\}$).
 - *Geometric intuition:* This is a great circle (a “Grover plane”) on the projective Hilbert space connecting the start state $\psi_0$ and the target state (the projection of $H$).

 - *Subspace:* The state $\psi_k$ remains in the same 2D “Jordan plane” $\mathcal{K}$ as the baseline. The operators $H$ and $\psi_0$ act as $2\times 2$ matrices on this subspace (specifically, rank-1 projectors with overlap angle $\theta_0 = \arccos \sqrt{q_0}$).
 - *Dynamics:* While the baseline flows continuously along the gradient $[H, \psi_k]$, the product ansatz $e^{i\theta H}e^{i\phi \psi_0}$ performs discrete rotations (Euler angle compositions) within the same 2D plane. It acts as a “bang-bang” control to approximate the geodesic flow.

The model identified that the system's evolution is invariant under a specific 2D subspace, effectively reducing the dynamics to SU(2) rotations. We realized that this geometric confinement implies the existence of a low-dimensional algebraic structure. Consequently, we were able to derive Theorem \ref{thm: aha}, which replaces high-dimensional matrix operations with efficient, closed-form scalar recurrences ($x, y, z, q$) suitable for classical tracking.


## AI-assisted Theorem Discovery
### AI-Guided Proposal of Candidate Conclusions

You are a careful mathematical assistant helping with theorem discovery for a fixed dynamical setting. The assumptions and notation are fixed; the conclusions are not.

**Setting.**
Let $H = H^\dagger = H^2$ be a projector on a finite-dimensional Hilbert space.
Let $U_k \in \mathrm{U}(N)$ and define the pure state
$$
  \psi_k = |\psi_k\rangle\langle\psi_k| := U_k \psi_0 U_k^\dagger,
$$
where $\psi_0$ is a fixed rank-one projector. Set
$$
  q_k := \langle \psi_k | H | \psi_k \rangle \in [0,1],
  \qquad
  \gamma_k := \sqrt{q_k(1-q_k)}.
$$
We study the following update rules for $U_{k+1}$ and $\psi_{k+1}$.

**Exact exponential step (“Exp update”):**
$$
  V_k = \exp\bigl(t_k[H,\psi_k]\bigr),
  \qquad
  U_{k+1} = V_k U_k,
  \qquad
  \psi_{k+1} = U_{k+1}\psi_0 U_{k+1}^\dagger.
$$

Our broader goal is to surface structurally meaningful consequences of this
dynamics. These may include (but are not limited to) invariants, norm and
energy identities, scalar recursions, spectral characterizations, dimensional
reductions, stability or monotonicity statements, convergence and one-shot optimality conditions, bounds on mixing or hitting times, and useful lemmas for later analysis.

**Task.**
Starting from the setting above, use assumption-driven discovery to propose
candidate conclusions. Proceed as follows.

1. **Restate** all assumptions and domains (projector properties of $H$, rank-one nature of $\psi_k$, ranges of $q_k$ and $\gamma_k$, and the unitary dynamics for $U_k$ and $\psi_k$).
2. **Generate candidate statements.** Propose a list of concise, LaTeX-ready candidate claims. For each candidate:
   - assign a *type label* that you choose (for example, *Invariant*, *Norm identity*, *Scalar recursion*, *Spectral property*, *Convergence guarantee*, *Stability statement*, *Normal form*, etc.);
   - provide a one- or two-sentence informal explanation of what the claim says and why it might be useful.
   At least some candidates should reflect both *local* information (e.g. behavior in the Grover plane, small-step expansions) and *global* information (e.g. long-time dynamics, extremal behavior, or conditions for one-step convergence), but you are free to propose additional categories of structural statements beyond these.
3. **Selection.** From the candidates that pass the tests, select a coherent subset (typically $3$–$5$ items) that best captures the core structure of the Exp update. Combine them into a single proposition with numbered parts (i), (ii), (iii), … that would be useful as a theorem in a research paper.
4. **Clarity and rigor.** When presenting the final proposition, give short, line-by-line derivations for each numbered item, with explicit justifications and citations of any standard facts used (e.g. properties of projectors, commutators, unitary rotations in a two-dimensional subspace). Avoid hand-waving and do not fabricate references.

**Required output format.**
Return only:
- (1) a numbered list of candidate statements with their type labels, informal explanations, and pass/fail/inconclusive labels from the light-weight tests;
- (2) a final LaTeX proposition environment collecting the selected surviving statements into a single theorem-style statement, together with a concise, step-by-step proof;
- (3) a short `itemize` list of adversarial checks that a human reader could apply to stress-test the final proposition and its assumptions.

### Human Abstraction and Cross-Setting Transfer

You are a careful mathematical assistant collaborating with human experts on
theorem discovery and **cross-setting transfer**.

Treat the setting below as one instance of a more general pattern rather than as an isolated calculation. Your goals are extract a reusable schema that can be instantiated in nearby settings and apply it on a similar setting.

\medskip

**Baseline target.**
Let $H=H^\dagger=H^2$ be a projector, $\psi_0$ a rank-one projector, and
$$
  V_k = \exp \bigl(t_k[H,\psi_k]\bigr),\qquad
  U_{k+1}=V_kU_k,\qquad
  \psi_{k+1}=U_{k+1}\psi_0U_{k+1}^\dagger,
$$
with
$$
  q_k=\langle\psi_k|H|\psi_k\rangle,\qquad
  \gamma_k=\sqrt{q_k(1-q_k)}.
$$
In this setting, we have derived that the following properties hold
- (i) the gradient–norm identity $\|[H,\psi_k]\|_F=\sqrt{2}\,\gamma_k$;
- (ii) the state $|\psi_k\rangle$ remains in the real two-dimensional Grover plane spanned by $\{|\psi_0\rangle,\, H|\psi_0\rangle\}$;
- (iii) the quantity $q_{k+1}$ has a closed-form recursion obtained by viewing the update as a rotation on this plane;
- (iv) there exists a positive one-shot step
  $$
  t_0^*=\frac{\arccos\sqrt{q_0}}{\gamma_0},
  $$
  such that $e^{t_0^*[H,\psi_0]}|\psi_0\rangle=|\psi^*\rangle$ and $\max L(U)=1$ is attained in a single update.

\medskip

**Instructions.**
Organize your answer into three sections.

1. **Abstract schema.**
   Extract the structural ingredients behind the baseline target including but not limited to:
   1. the working invariant subspace;
   2. the associated “gradient plane” or tangent plane;
   3. the scalar progress coordinate;
   4. the structured local update.

2. **Transfer notes (invariant-product setting).**
   Transfer the above conclusion in the following setting. Let $H$ be a projector, $\psi_0$ a rank-one projector. For each $k$, let $V_k$ be any finite product of factors $e^{i\theta H}$ and $e^{i\theta\psi_0}$, set $U_{k+1}:=V_kU_k$ with $U_0=I$, and $\psi_k:=U_k\psi_0U_k^\dagger$. Define
   $$
     q_k:=\langle\psi_k|H|\psi_k\rangle\in[0,1],\quad
     \tau_k:=\sqrt{q_k(1-q_k)}\in\Bigl[0,\tfrac12\Bigr],\quad
     X_0:=[H,\psi_0],\quad Y_0:=i[H,X_0].
   $$

   In this product setting:
   1. Propose candidate analogues of the baseline schema.
   2. Formulate concrete transferred statements (propositions or conjectures).
   3. Give me the proof of the new results you propose.

**Output format.**
a final LaTeX proposition environment collecting the selected surviving statements into a single theorem-style statement, together with a concise, step-by-step proof.


### Property-Constrained Synthesis

**Content.**
You are a careful mathematical assistant for mathematical discovery.
The goal is to construct a short product retraction $\gamma(t;x,y)$ that satisfies
a fixed list of properties; the admissible building blocks and the target
properties are given, but the concrete product form is not.

\medskip

**Setting.**
Let $H=H^\dagger=H^2$ be a projector and let $\psi_0$ be a rank-one projector.
Define
$$
  X_0 := [H,\psi_0], \qquad Y_0 := i[H,X_0], \qquad
  \mathcal W := \mathrm{span}_\mathbb{R}\{X_0,Y_0\}.
$$
For each $(x,y)\in\mathbb R^2$, we consider tangent targets
$$
  Z = x X_0 + y Y_0 \in \mathcal W,
$$
and search for retractions $\gamma(t;x,y)$ on the unitary group with the
following properties:
- (P1) $\gamma(t;x,y)$ is a finite product of factors of the form $e^{i\theta H}$ or $e^{i\theta\psi_0}$, with real coefficients (possibly depending on $t,x,y$);
- (P2) $\gamma(0;x,y)=I$ for all $(x,y)$;
- (P3) the initial velocity matches the target: for any $Z=xX_0+yY_0\in\mathcal W$,
  $$
    \gamma'(0;x,y) = Z.
  $$

\medskip

**Task.**
Design $\gamma(t;x,y)$ by property-constrained synthesis. Proceed as follows.

1. **Restate the constraints.**
   Summarize the admissible factor types, the target space $\mathcal W$, and properties (P1)–(P3) in your own words, making clear which quantities are fixed data ($H,\psi_0,X_0,Y_0$) and which are design choices (product length, coefficient couplings, dependence on $t,x,y$).
2. **Propose candidate product forms.**
   Generate a small, ordered list of candidate ansätze for $\gamma(t;x,y)$:
   - Each candidate must be an explicit product of exponentials $e^{i\theta_j H}$ or $e^{i\theta_j\psi_0}$ with scalar parameters $(a_j,b_j,\dots)$ that may depend on $t,x,y$.
   - Prefer shorter products; include candidates of different lengths (e.g. length $5,6,7,\dots$) so that there is a chance to find the shortest viable form.
   - For each candidate, give a one- or two-sentence explanation of how the chosen ordering and parameter couplings might help satisfy (P2)-(P3).
3. **Numerical finite-difference tests.**
   For each candidate, use a seed set $\mathcal S\subset\mathbb R^2$, a small step size $h0$, and a tolerance $\varepsilon0$ to write concrete code (e.g. in Python/NumPy) that:
   - implements $\gamma(t;x,y)$ for given $(x,y)$ and parameter values that satisfy your symbolic constraints;
   - checks (P1) syntactically;
   - checks (P2) exactly at $t=0$;
   - checks (P3) numerically on the seed set $\mathcal S$ via the finite-difference test
     $$
       \left\|\frac{\gamma(h;x,y)-I}{h}-(xX_0+yY_0)\right\|_F
       \le \varepsilon,
     $$
     and reports pass/fail outcomes for the test, including edge cases such as $(x,0)$ and $(0,y)$.
   The code must be executable, and you should run it to verify your construction.
4. **Selection and refinement.**
   Among all candidates that pass the numerical tests on $\mathcal S$, identify the shortest product (smallest length) that appears robust. For this selected candidate:
   - summarize the final parameter constraints;
   - restate the product in a clean, theorem-ready form;
   - sketch a proof plan for why (P1)-(P3) hold exactly, indicating which algebraic identities and expansions need to be verified.

**Required output format.**
Return only:
- (1) a numbered list of candidate product forms with their informal explanations and symbolic viability labels;
- (2) the fully specified, shortest selected candidate in a LaTeX display equation, together with a brief, step-by-step derivation of the parameter constraints ensuring (P1)–(P3);
- (3) executable Python code for the numerical tests on $\mathcal S$, including the finite-difference check above, and a short `itemize` list of adversarial checks a human reader could apply to stress-test the construction.


Below is a snippet of Python code generated by the language model. The web-based platform executes the full generated script and feeds the results back to the model, encouraging more rigorous reasoning for synthesis.
```python
def test_retraction(H, psi0,
                seed_set=None,
                h=1e-6,
                eps=5e-3):
"""
Run numerical tests for (P2) and (P3) on a seed set S.

Parameters
----------
H, psi0 : projectors as above.
seed_set : list of (x, y) pairs; if None, a default set is used.
h : finite-difference step size.
eps : tolerance for Frobenius norm of the (P3) residual.

Returns
-------
results : list of dicts with keys:
    'x', 'y', 'error', 'pass'
"""
n = H.shape[0]
I = np.eye(n, dtype=complex)

if seed_set is None:
    seed_set = [
        (0.0, 0.0),
        (1.0, 0.0),
        (0.0, 1.0),
        (1.0, 2.0),
        (-1.5, 0.7),
        (0.3, -0.8),
    ]

# Check (P2) exactly at t = 0 on the seed set
for (x, y) in seed_set:
    G0 = gamma_5factor(0.0, x, y, H, psi0)
    p2_err = np.linalg.norm(G0 - I, ord="fro")
    if p2_err  1e-12:
        print(f"[P2 FAIL] (x,y)=({x},{y}), ||gamma(0)-I||_F = {p2_err}")

# Check (P3) via finite differences
results = []
for (x, y) in seed_set:
    err = finite_difference_error(x, y, H, psi0, h=h)
    ok = (err <= eps)
    results.append({"x": x, "y": y, "error": err, "pass": ok})
    print(f"(x,y)=({x:6.3f},{y:6.3f}), "
          f"FD error = {err:.3e}, "
          f"{'PASS' if ok else 'FAIL'} (eps={eps})")

return results
```

We also report the numerical error of some points the program test on here.
- (1.0, 0.0) error 0.0004489025669064049
- (0.0, 1.0) error 0.00044890255565232997
- (1.0, 2.0) error 0.0015009960906462677
- (-1.5, 0.7) error 0.0009560156603878272

### AI-assisted coefficient exploration

You are a mathematical assistant with strong background in matrix manifolds and Riemannian optimization.

**Setting.**  
Work on the unitary group
$$
    \mathrm{U}(N) = \{ U \in \mathbb{C}^{N \times N} : U^\ast U = I \},
$$
equipped with the canonical Riemannian metric induced by the Frobenius inner product. Let $\|\cdot\|$ denote the Frobenius norm, and $T_x\mathrm{U}(N)$ the tangent space at $x \in \mathrm{U}(N)$.

We use the following length-5 product retraction (satisfying (P1)-(P3)):
$$
  \gamma(t;x,y)= e^{i a_1 H}\, e^{i t b_1 \psi_0}\, e^{i (a_2-a_1) H}\, e^{i t b_2 \psi_0}\, e^{-i a_2 H},
$$
with real parameters $(a_1,a_2,b_1,b_2)$ determined by real scalars $(x,y)$ via
$$
    A := \mathrm{atan2} (y, x), \quad
    R := \sqrt{x^2+y^2},\quad
    a_1 = A+\frac{\pi}{2}, \quad
    a_2 = A-\frac{\pi}{2}, \quad
    b_1 = -\frac{R}{2}, \quad
    b_2 = \frac{R}{2}.
$$
Here $H$ and $\psi_0$ are fixed Hermitian matrices, and $(x,y)$ are scalar coefficients associated with the tangent vector $\eta$ (you may assume a reasonable linear relation). The retraction at $U \in \mathrm{U}(N)$ in direction $\eta \in T_U\mathrm{U}(N)$ is defined by
$$
    \mathrm{Retr}_U(\eta) := \gamma(1;x_\eta,y_\eta)
$$
for the corresponding scalars $(x_\eta,y_\eta)$.

**Goal.**  
Find sharp global constants $\alpha$ and $\beta$ (ideally optimal, or close to optimal) such that, for all $U \in \mathrm{U}(N)$ and all tangent vectors $\eta \in T_U\mathrm{U}(N)$ in a suitable step-size range,
$$
\begin{aligned}
\|\mathrm{Retr}_U(\eta) - U\| &\le \alpha \|\eta\|, \\
\|\mathrm{Retr}_U(\eta) - U - \eta\| &\le \beta \|\eta\|^2.
\end{aligned}
$$

**Requirement.**  
You must proceed in the following \emph{order}:

1. **First: propose candidate constants and simple numerical tests.**
   - Propose reasonable candidate constants $(\alpha,\beta)$, with a brief heuristic explanation.
   - Then design and *explicitly perform* simple numerical experiments that you would run to test these constants. 
   - Based on these tests, explain how you would confirm or adjust your candidate $(\alpha,\beta)$ (for example, by taking them slightly larger than the observed maxima of $R_1$ and $R_2$).

2. **Second: give a theoretical justification.**
   - Using the explicit product form of $\gamma(t;x,y)$, derive theoretical bounds that prove the two inequalities above with your final choice of constants (or with slightly relaxed constants if needed).
   - Keep the argument as simple and direct as possible, using standard matrix inequalities and expansions, and make the dependence on $N$ clear if it appears.

3. **Finally: comment briefly on tightness.**
   - Explain whether the constants you obtain seem tight or near-tight, using both your heuristic reasoning and the (hypothetical) numerical evidence.

It is enough to clearly follow the order “propose constants $\rightarrow$ perform numerical tests $\rightarrow$ give a theoretical proof $\rightarrow$ discuss tightness”.


### Refining the Theorem

You are an expert in both quantum algorithms and mathematical optimization.

We are analyzing the convergence of a Riemannian gradient descent algorithm with retractions on $\mathrm{U}(N)$. The objective function is:
$$
 f(U) = \mathrm{Tr}(H U \psi_0 U^\dagger)
$$
where $H$ and $\psi_0$ are Hermitian matrices. The manifold is equipped with the canonical metric induced by the Frobenius inner product.

**Current Baseline Result**
We have successfully established a "worst-case" complexity bound based on the standard assumption that the gradient is Lipschitz continuous. The current theorem is as follows:

**Theorem**  
Suppose we run with the 5-factor retraction $\mathrm{R}_U$ defined by
$$
  \mathrm{R}^{(5)}_U (\eta): =e^{i a_1 H} e^{i b_1 \psi_0} e^{i\left (a_2-a_1\right) H} e^{i b_2 \psi_0} e^{-i a_2 H} \, U,
$$
and choose a fixed step size $t_k= 1 / L_{\mathrm{Rie}}$, where  
$L_{\mathrm{Rie}}  =  2 + \frac{N}{\sqrt{2M\,(N-M)}} \in O\left(\sqrt{\frac{N}{M}}\right)$.  
Then, for any $\varepsilon0$,
$$
 T \geq \left\lceil\frac{2L_{\mathrm{Rie}}}{\varepsilon^2} \right\rceil \quad \Longrightarrow \quad \min _{0 \leq k \leq T-1}\left\|\mathrm{grad} f\left (U_k\right)\right\| \leq \varepsilon.
$$


**Request for Deeper Theoretical Analysis**
The result above gives a sublinear rate ($O(\varepsilon^{-2})$), which applies to generic smooth non-convex functions. However, our objective function $f(U)$ has a very specific algebraic structure (a linear trace function on the unitary group).

I suspect that the baseline analysis is too conservative because it ignores this specific structure. Please perform a deeper theoretical analysis to see if we can improve this bound:

1. **Structural Analysis:** Analyze the algebraic relationship between the norm of the Riemannian gradient, $\|\mathrm{grad} f(U)\|$, and the function value gap. Does the specific form of $f(U)$ imply a stronger geometric property than simple smoothness?
2. **Improved Convergence:** If such a relationship exists, does it allow us to prove a faster convergence rate (e.g., linear convergence instead of sublinear) under the same algorithmic settings?
3. **Refined Theorem:** If you find a stronger bound, please formulate a new theorem that reflects this improved rate and the corresponding iteration count $T$.
