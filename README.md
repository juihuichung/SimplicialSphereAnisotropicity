# Formalization of characteristic-two anisotropicity of simplicial spheres

Every positive-dimensional simplicial sphere is generically anisotropic over
every field of characteristic two.

Based on [*The characteristic 2 anisotropicity of simplicial
spheres*](https://arxiv.org/abs/2012.09815) by Stavros Argyrios Papadakis and
Vasiliki Petrotou, and [*On the anisotropy theorem of Papadakis and
Petrotou*](https://doi.org/10.5802/alco.298) by Kalle Karu and Elizabeth Xiao.

## Semantic alignment

[`Challenge.lean`](Challenge.lean) spells out Definitions 2.2 and 3.2 and
Theorem 3.3 of Papadakis--Petrotou.  The principal correspondences are:

| Paper | Lean |
| --- | --- |
| the vertex set `{1, ..., m}` | `Fin m` (zero-based); Mathlib's [`AbstractSimplicialComplex`](https://github.com/leanprover-community/mathlib4/blob/6f1ef4e5dd604a435bddba4747b13970cd65d2a1/Mathlib/AlgebraicTopology/SimplicialComplex/Basic.lean#L145-L153) requires every singleton to be a face |
| a geometric realization of `D` homeomorphic to `Sⁿ` | `IsSimplicialSphere D n`, using the canonical barycentric realization |
| `k = Frac(k₁[aᵢⱼ])` | `GenericField k₁ n m` |
| `A = k[x₁, ..., xₘ]/(I_D + (f₁, ..., fₙ₊₁))` | `GenericArtinianReduction k₁ D` |
| the graded component `Aⱼ` | classes with a homogeneous degree-`j` representative |
| every nonzero `u ∈ Aⱼ`, `1 ≤ 2j ≤ n+1`, has `u² ≠ 0` | `GenericallyAnisotropic k₁ D n` |

Mathlib stores only nonempty faces of an abstract simplicial complex, so the
Stanley--Reisner generators explicitly require a nonempty nonface.  The
solution machine-checks the remaining representation bridges in
[`mem_quotientDegree_iff`](Solution.lean#L607),
[`genericReductionIdeal_isHomogeneous`](Solution.lean#L655), and
[`preGeom_toPre_eq_geometricRealization`](Solution.lean#L8138).  It also proves
[`crosspolytope_isSimplicialSphere`](Solution.lean#L33540), giving an explicit
standard family that satisfies the sphere predicate.

The repository includes a Comparator setup.

```sh
lake update
lake exe cache get
lake build lean4export
lake exe comparator comparator/config.json
```

[Type-check it online!](https://live.lean-lang.org/#project=mathlib-stable&url=https%3A%2F%2Fraw.githubusercontent.com%2Fjuihuichung%2FSimplicialSphereAnisotropicity%2Frefs%2Fheads%2Fmain%2FSolution.lean)
