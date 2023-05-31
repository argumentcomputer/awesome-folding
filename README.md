# Awesome-Folding

A curated list of awesome resources related to zero-knowledge folding schemes. Folding schemes are a revolutionary approach to incrementally verifiable computation (IVC), fundamental to efficient and correct execution of computational steps in Zero-Knowledge Proofs. 

## Table of Contents
- [Writings (papers, blog posts, etc)](#writings-papers-blog-posts-etc)
  - [Prequels](#prequels)
    - [Arithmetization](#arithmetization)
    - [Spartan](#spartan)
    - [IVC](#ivc)
    - [Halo2](#halo2)
  - [Classic Nova](#classic-nova)
  - [Nova Extensions (without high-degree gates)](#nova-extensions-without-high-degree-gates)
  - [HyperNova / ProtoStar : The next generation (with high-degree gates)](#hypernova-/-protostar-:-the-next-generation-(with-high-degree-gates))
- [Code (software repositories)](#code-(software-repositories))
  - [Reference implementations](#reference-implementations)
  - [Teaching / experimental implementations](#teaching-/-experimental-implementations)
  - [Code Explorations](#code-explorations)
- [Other resources (podcasts, etc)](#other-resources-(podcasts,-etc))
- [Applications](#applications)


# Writings (papers, blog posts, etc)

## Prequels

### Arithmetization

A gentle introduction to Plonk-like arithmetization, lookup arguments and the birth of lookup arguments in the Plonk world. 

- [From AIRs to RAPs](https://hackmd.io/@aztec-network/plonk-arithmetiization-air)
- [A Brief history of lookup arguments](https://github.com/ingonyama-zk/papers/blob/main/lookups.pdf)
- [Multiset checks in PLONK and Plookup](https://hackmd.io/@arielg/ByFgSDA7D)

### Spartan

The final SNARK used in Nova (only using MSMs)

- [Spartan: Efficient and general-purpose zkSNARKs without trusted setup](https://eprint.iacr.org/2019/550)

### IVC

- [Incrementally Verifiable Computation or Proofs of Knowledge Imply Time/Space Efficiency](https://www.cs.purdue.edu/homes/pvaliant/uniqueCS.pdf)

### Halo2

The prototype of the delayed proving approach which Nova puts on steroids.

- [Recursive Proof Composition without a Trusted Setup](https://eprint.iacr.org/2019/1021)

## Classic Nova

Classic works on the Nova proof system, including seminal papers and accompanying presentations.

- [Nova: Recursive Zero-Knowledge Arguments from Folding Schemes](https://eprint.iacr.org/2021/370)
    - [Presentation](https://www.youtube.com/watch?v=Jj19k2AXH2k)
- [SuperNova: Proving universal machine executions without universal circuits](https://eprint.iacr.org/2022/1758)
    - [Presentation](https://www.youtube.com/watch?v=BiKMCNKwaec)
- [Sangria: a Folding Scheme for PLONK](https://github.com/geometryresearch/technical_notes/blob/main/sangria_folding_plonk.pdf)
    - [Presentation](https://www.youtube.com/watch?v=D7rQbHpxl7Q)

## Nova Extensions (without high-degree gates)

Extensions to the Nova proof system that explore PCS in terms of linear codes, folding, and other concepts.

- [Linear algebra and zero-knowledge](https://www.youtube.com/watch?v=dSsUfKgZlkk)
- [Origami – A Folding Scheme for Halo2 Lookups](https://hackmd.io/@aardvark/rkHqa3NZ2)
- [Folding for Arbitrary Polynomial Custom Gates and Lookups](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)
- [Folding endgame](https://zkresear.ch/t/folding-endgame/106)

## HyperNova / ProtoStar : The next generation (with high-degree gates)

- [Customizable constraint systems for succinct arguments](https://eprint.iacr.org/2023/552)
- [HyperNova: Recursive arguments for customizable constraint systems](https://eprint.iacr.org/2023/573)
- [ProtoStar: Generic Efficient Accumulation/Folding for Special Sound Protocols](https://eprint.iacr.org/2023/620)

# Code (software repositories)

## Reference implementations

- https://github.com/microsoft/Nova

## Teaching / experimental implementations

- https://github.com/arnaucube/nova-study/
- https://github.com/jules/supernova

## Code Explorations

Code implementations and explorations related to the Nova proof system, including benchmarks, specifications, and experimental versions.

- [Nova benchmarks](https://hackmd.io/@oskarth/rJmSaOtZ2)
- [Nova wishlist and next steps](https://hackmd.io/@oskarth/SJRm4zYbn)
- [Nova-based ZKVM spec](https://hackmd.io/@CPerezz/ByTmhi6yn)
- [Origami-benchmarks](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)

# Other resources (podcasts, etc)

- *Podcast*: [ZK-Podcast Episode 277: Nova and beyond with Srinath Setty](https://www.youtube.com/watch?v=hRza_k8i16s)
- *Talk*: [ZK Study Club: SuperNova with Srinath Setty](https://www.youtube.com/watch?v=ilrvqajkrYY)
- *Forum*: [Privacy Scaling Explorations](https://appliedzkp.org/#top) [Discord Server](https://discord.gg/sF5CT5rzrR)
- *Forum*: [Lurk Lab](https://lurk-lab.com/) [Zulip Server](https://zulip.lurk-lab.com/)

# Applications

- [Nova-Scotia](https://github.com/nalinbhardwaj/Nova-Scotia)
    - This repository provides necessary middleware to take generated output of the Circom compiler (R1CS constraints and generated witnesses) and use them with Nova as a prover.
- [Lurk](https://github.com/lurk-lang/lurk-rs)
    - Lurk is a Turing-complete programming language for recursive zk-SNARKs. It is a statically scoped dialect of Lisp, influenced by Scheme and Common Lisp.
