# Formalization of characteristic-two anisotropicity of simplicial spheres

Every positive-dimensional simplicial sphere is generically anisotropic over
every field of characteristic two.

Based on [*The characteristic 2 anisotropicity of simplicial
spheres*](https://arxiv.org/abs/2012.09815) by Stavros Argyrios Papadakis and
Vasiliki Petrotou, and [*On the anisotropy theorem of Papadakis and
Petrotou*](https://doi.org/10.5802/alco.298) by Kalle Karu and Elizabeth Xiao.

The repository includes a Comparator setup.

```sh
lake update
lake exe cache get
lake build lean4export
lake exe comparator comparator/config.json
```

[Type-check it online!](https://live.lean-lang.org/#project=mathlib-stable&url=https%3A%2F%2Fraw.githubusercontent.com%2Fjuihuichung%2FSimplicialSphereAnisotropicity%2Frefs%2Fheads%2Fmain%2FSolution.lean)
