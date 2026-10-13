<!-- solve-problem:f24b3d2c-5e3a-44e7-b052-de149cc12a95 -->
# Ultimate positivity with repeated characteristic roots

A [Tangle Solve problem](https://solve.tangle.tools/problems/f24b3d2c-5e3a-44e7-b052-de149cc12a95).

## What is the problem?

A linear recurrence sequence (LRS) over ℚ is a sequence ⟨u_n⟩_{n≥0} satisfying u_{n+k} = a_{k-1}u_{n+k-1} + … + a_0 u_n, with a_0 ≠ 0 and initial values u_0,…,u_{k-1} ∈ ℚ. Its characteristic polynomial p(x) = x^k − a_{k-1}x^{k-1} − … − a_0 factors as ∏ (x−λ_i)^{m_i}; the sequence is called **simple** if all m_i = 1 (i.e., the roots are distinct), and general (non-simple) if repeated roots are allowed. The general closed form is u_n = Σ_i P_i(n) λ_i^n where P_i is a polynomial of degree m_i − 1.

- **Positivity**: u_n ≥ 0 for all n ≥ 0.
- **Ultimate positivity**: ∃N ∀n ≥ N: u_n ≥ 0.

**Open problem:** decide ultimate positivity for arbitrary integer/rational LRS *of unbounded order* with no simplicity restriction on the characteristic roots. The exact decision status when repeated roots occur is unresolved in the census formulation; the well-documented state of the art is decidability for simple LRS of arbitrary order (Ouaknine–Worrell 2014), with the general repeated-root case (especially combined with Skolem-hard aspects) not settled by that technique. A reasonable precise target: a decidable procedure or a hardness proof (e.g., ∃ℝ-hardness or undecidability) for ultimate positivity of general LRS. Note: for *fixed order* d, the problem is decidable in polynomial time for all d (via quantifier elimination in real algebraic geometry with exponentials of bounded algebraic degree) — the open regime is unbounded order with repeated roots.

## Why does it matters?

Ultimate positivity is the canonical "eventual safety" question for discrete linear dynamical systems: it asks whether a system's observable eventually stays in a half-space forever. It arises in verification of loop termination/invariants, probabilistic model checking (powers of Markov-chain transition matrices produce repeated characteristic roots — this is exactly why the general case matters), theoretical biology, and as a stepping stone toward the Skolem Problem and Positivity Problem (the latter known to imply deep number-theoretic consequences, e.g., finiteness of relevant τ-conjecture instances). Decidability of positivity for LRS of order 6 would entail major open results in transcendence theory, so the ultimate variant is the tractable fallback everyone wants.

## What's already known?

- **Ouaknine–Worrell (2014)**: ultimate positivity is decidable for simple LRS of arbitrary order over ℚ, in polynomial time for fixed order. The proof: (1) show the dominant (modulus-maximal) roots control the eventual sign; (2) handle equidominant cases via a quantitative "root-separation vs. exponentially small perturbation" argument, reducing to comparing sums of algebraic exponentials on Bohr sets; (3) invoke a deep result of Masser on multiplicative relationships among algebraic numbers.
- **Positivity vs. ultimate positivity**: positivity for simple LRS of order ≤ 5 is decidable; positivity in general is open and hard — Ouaknine–Worrell showed decidability of positivity at order 6 (verify exact order) would entail the Tarski-type/separation conjecture consequences; Positivity is at least as hard as certain open Diophantine questions.
- **Repeated roots break the proof** because the closed form acquires polynomial prefactors P_i(n); oscillatory behavior of terms like n·λ^n with complex λ is controlled by both n and the argument of λ, and the Masser-based Bohr-set machinery was built for pure exponential sums. No published extension handles this in general.
- For fixed order the problem is decidable by results on bounded-order LRS (e.g., via first-order theory of reals with exp restricted to bounded algebraic arguments — the "Tarski with restricted exp" approach of Ouaknine–Worrell for bounded order).

## What would count as solving it?

Any of:
1. **Decidability**: an algorithm that, given an arbitrary-order rational LRS with possibly repeated characteristic roots, decides ultimate positivity, with a termination/complexity analysis.
2. **Hardness/undecidability**: a proof that the problem is undecidable, or hard for a named class (∃ℝ, Skolem-hard, etc.), at some bounded order.
3. **Intermediate progress**: decidability for non-simple LRS with all roots real; or with repeated roots of bounded multiplicity m; or decidability for matrix powers u_n = A^n v (the natural non-simple setting).

A referee would accept (1) as a full solution and (2)/(3) as valuable partial results. Note the census statement is somewhat informal — the exact literature status of the repeated-root case should be re-verified against the Ouaknine–Worrell survey before claiming novelty.

## How to start

1. Read Ouaknine–Worrell 2014 (FoCS/ICALP version) carefully, especially the reduction to dominant roots and the use of Masser's theorem; then their survey "On Positivity and Skolem Problems" for the explicit list of open variants.
2. Write the non-simple closed form u_n = Σ P_i(n)λ_i^n and attempt to redo the equidominant analysis: polynomial prefactors give terms whose sign is governed by (arg λ_i)·n + arg(P_i(n)) — study whether the Bohr-set/multiplicative-dependence argument extends when arguments shift logarithmically in n.
3. Consider the matrix-power formulation: for A ∈ ℚ^{d×d}, is {A^n v : n ≥ N} eventually in a half-space? Repeated roots are unavoidable here, so this sub-case is the natural target and has independent verification interest.
4. Main obstacle: no analogue of Masser's multiplicative-independence bound controls the *polynomial* factors; small-numerator cancellations among terms P_i(n)λ_i^n may encode harder Diophantine information. Check the literature on "linear recurrence sequences with multiple roots" and the τ-conjecture connection before assuming a clean extension exists.

## Key references

- J. Ouaknine and J. Worrell, "Ultimate Positivity Is Decidable for Simple Linear Recurrence Sequences", ICALP 2014. Proves decidability of ultimate positivity for arbitrary-order LRS with simple characteristic roots via dominant-root analysis and Masser's theorem on multiplicative dependencies.
- J. Ouaknine and J. Worrell, "On the Positivity Problem for Simple Linear Recurrence Sequences", ICALP 2014. Shows positivity (all n) is decidable for simple LRS of order ≤ 5 and establishes hardness connections for higher orders.
- J. Ouaknine and J. Worrell, "Positivity Problems for Low-Order Linear Recurrence Sequences", SODA 2014. Decidability results for low orders; source of the τ-conjecture/Positivity connections.
- J. Ouaknine and J. Worrell, "On Linear Recurrence Sequences and Loop Termination", ACM SIGLOG News, 2015. Accessible survey of the Skolem/Positivity/Ultimate Positivity landscape and open problems.

(Links: search ICALP 2014 / SODA 2014 proceedings, or the authors' pages at Oxford/MPI; no arXiv identifiers recorded — verify.)

## Warnings

- The census record's status line is imprecise: for *fixed* order, repeated roots pose no decidability obstruction (quantifier-elimination handles them); the open problem is specifically *unbounded* order. Do not claim to solve the fixed-order case.
- The census source is a single AI-generated record (fleet:gpt6pro, 2026); verify against the primary literature whether some repeated-root case has since been resolved.
- Beware conflating Positivity with Ultimate Positivity — the hardness landscape differs sharply.
- Repeated roots often signal the author means matrix powers / Markov chains; the matrix formulation is equivalent in difficulty and may be the more natural formalization.

---
*`ALGO-000180` · unverified*

## Acceptance guidance

Any of:
1. **Decidability**: an algorithm that, given an arbitrary-order rational LRS with possibly repeated characteristic roots, decides ultimate positivity, with a termination/complexity analysis.
2. **Hardness/undecidability**: a proof that the problem is undecidable, or hard for a named class (∃ℝ, Skolem-hard, etc.), at some bounded order.
3. **Intermediate progress**: decidability for non-simple LRS with all roots real; or with repeated roots of bounded multiplicity m; or decidability for matrix powers u_n = A^n v (the natural non-simple setting).

A referee would accept (1) as a full solution and (2)/(3) as valuable partial results. Note the census statement is somewhat informal — the exact literature status of the repeated-root case should be re-verified against the Ouaknine–Worrell survey before claiming novelty.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/f24b3d2c-5e3a-44e7-b052-de149cc12a95?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000180.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000180)
