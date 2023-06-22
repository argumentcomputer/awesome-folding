# Awesome-Folding

A curated list of awesome resources related to zero-knowledge folding schemes. Folding schemes are a revolutionary approach to incrementally verifiable computation (IVC), fundamental to efficient and correct execution of computational steps in Zero-Knowledge Proofs.

<!-- toc -->

- [Writings (papers, blog posts, etc)](#writings-papers-blog-posts-etc)
  * [Prequels](#prequels)
    + [Arithmetization](#arithmetization)
    + [Spartan](#spartan)
    + [IVC and PCD](#ivc-and-pcd)
    + [Halo](#halo)
    + [Aggregation schemes](#aggregation-schemes)
  * [Accumulation schemes](#accumulation-schemes)
  * [Classic Nova](#classic-nova)
  * [Nova Extensions (without high-degree gates)](#nova-extensions-without-high-degree-gates)
  * [HyperNova / ProtoStar : The next generation (with high-degree gates)](#hypernova--protostar--the-next-generation-with-high-degree-gates)
- [Code (software repositories)](#code-software-repositories)
  * [Reference implementations](#reference-implementations)
  * [Teaching / experimental implementations](#teaching--experimental-implementations)
  * [Code Explorations](#code-explorations)
- [Other resources (podcasts, etc)](#other-resources-podcasts-etc)
  * [Podcast episodes](#podcast-episodes)
  * [Talks & Lectures](#talks--lectures)
  * [Forums](#forums)
- [Applications](#applications)

<!-- tocstop -->

## Writings (papers, blog posts, etc)

### Prequels

#### Arithmetization

A gentle introduction to Plonk-like arithmetization, lookup arguments and the birth of lookup arguments in the Plonk world.

- [From AIRs to RAPs](https://hackmd.io/@aztec-network/plonk-arithmetiization-air)
- [A Brief history of lookup arguments](https://github.com/ingonyama-zk/papers/blob/main/lookups.pdf)
- [Multiset checks in PLONK and Plookup](https://hackmd.io/@arielg/ByFgSDA7D)

#### Spartan

The final SNARK used in Nova (only using MSMs)

- [Spartan: Efficient and general-purpose zkSNARKs without trusted setup](https://eprint.iacr.org/2019/550)

#### IVC and PCD

- [Incrementally Verifiable Computation or Proofs of Knowledge Imply Time/Space Efficiency](https://www.cs.purdue.edu/homes/pvaliant/uniqueCS.pdf)
    - The paper that introduced incrementally-verifiable computation and the notion of recursive composition of proofs.
- [Proof-Carrying Data and Hearsay Arguments from Signature Cards](https://www.cs.tau.ac.il/~tromer/papers/pcd.pdf)
    - The paper that introduced proof-carrying data, a generalization of incrementally-verifiable computation to arbitrary graphs (IVC considers only a chain of computation)
- [Recursive composition and bootstrapping for SNARKS and proof-carrying data](http://eprint.iacr.org/2012/095)
    - This paper provides firm theoretical foundations for PCD and IVC.
- [Scalable Zero Knowledge via Cycles of Elliptic Curves](http://eprint.iacr.org/2014/595)
    - This paper introduces the notion of pairing-friendly cycles of curves, and shows how to use these to construct the first concretely efficient IVC/PCD scheme.

- [Revisiting the Nova Proof System on a Cycle of Curves](https://eprint.iacr.org/2023/969)
  - This paper analyzes the security of the Nova proving system when implemented on a cycle of curves.
  The paper exploits a soundness bug in the original implementation (since patched) and produces a
  convincing proof of $$2^75$$ rounds of the Minroot VDF in 1.46 seconds. A new optimized and secure
  system is introduced together with a formal security proof.

#### Halo

The prototype of the delayed proving approach which Nova puts on steroids.

- [Recursive Proof Composition without a Trusted Setup](https://eprint.iacr.org/2019/1021)

#### Aggregation schemes

Aggregation schemes show how to extend the aggregation ideas in Halo to any additively-homomorphic PC scheme, and construct PCD from these.

- [Halo Infinite: Recursive zk-SNARKs from any Additive Polynomial Commitment Scheme](https://eprint.iacr.org/2020/1536)
    - [Presentation](https://www.youtube.com/watch?v=TydI5xJlhqQ)

### Accumulation schemes

Accumulation schemes are a generalization of both Halo-style aggregation and Nova-style folding schemes that allow analyzing these ideas in a single system.
The papers below show how to use efficient accumulation schemes for certain predicates (e.g., polynomial commitments) to construct efficient PCD schemes.

- [Proof-Carrying Data from Accumulation Schemes](https://eprint.iacr.org/2020/499)
    - [Presentation](https://www.youtube.com/watch?v=UNwlBq1FQ3E)
- [Proof-Carrying Data without Succinct Arguments](https://eprint.iacr.org/2020/1618)
    - [Presentation](https://www.youtube.com/watch?v=TRyep--q6jU)

### Classic Nova

Classic works on the Nova proof system, including seminal papers and accompanying presentations.

- [Nova: Recursive Zero-Knowledge Arguments from Folding Schemes](https://eprint.iacr.org/2021/370)
    - [Presentation](https://www.youtube.com/watch?v=Jj19k2AXH2k)
- [SuperNova: Proving universal machine executions without universal circuits](https://eprint.iacr.org/2022/1758)
    - [Presentation](https://www.youtube.com/watch?v=BiKMCNKwaec)
- [Sangria: a Folding Scheme for PLONK](https://github.com/geometryresearch/technical_notes/blob/main/sangria_folding_plonk.pdf)
    - [Presentation](https://www.youtube.com/watch?v=D7rQbHpxl7Q)

### Nova Extensions (without high-degree gates)

Extensions to the Nova proof system that explore PCS in terms of linear codes, folding, and other concepts.

- [Linear algebra and zero-knowledge](https://www.youtube.com/watch?v=dSsUfKgZlkk)
- [Origami – A Folding Scheme for Halo2 Lookups](https://hackmd.io/@aardvark/rkHqa3NZ2)
- [Folding for Arbitrary Polynomial Custom Gates and Lookups](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)
- [Folding endgame](https://zkresear.ch/t/folding-endgame/106)

### HyperNova / ProtoStar : The next generation (with high-degree gates)

- [Customizable constraint systems for succinct arguments](https://eprint.iacr.org/2023/552)
- [HyperNova: Recursive arguments for customizable constraint systems](https://eprint.iacr.org/2023/573)
- [ProtoStar: Generic Efficient Accumulation/Folding for Special Sound Protocols](https://eprint.iacr.org/2023/620)

## Code (software repositories)

### Reference implementations

- [microsoft/nova](https://github.com/microsoft/Nova)

### Teaching / experimental implementations

- [nova-study](https://github.com/arnaucube/nova-study/): Implementation of Nova using arkworks-rs just forlearning purposes.
- [supernova](https://github.com/jules/supernova): Experimental implementation of the SuperNova protocol
- [multifolding-poc](https://github.com/privacy-scaling-explorations/multifolding-poc): Experimental implementation of HyperNova
- [ccs-hack](https://github.com/thor314/ccs-hack): a hack implementation of CCS generic implementation

### Code Explorations

Code implementations and explorations related to the Nova proof system, including benchmarks, specifications, and experimental versions.

- [Nova benchmarks](https://hackmd.io/@oskarth/rJmSaOtZ2)
- [Nova wishlist and next steps](https://hackmd.io/@oskarth/SJRm4zYbn)
- [Nova-based ZKVM spec](https://hackmd.io/@CPerezz/ByTmhi6yn)
- [Origami-benchmarks](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)

## Other resources (podcasts, etc)

### Podcast episodes

- *Podcast*: [ZK-Podcast Episode 277: Nova and beyond with Srinath Setty](https://www.youtube.com/watch?v=hRza_k8i16s)
- *Podcast*: [ZK-Podcast Episode 280: ProtoStar with Benedikt Bünz and Binyi Chen](https://zeroknowledge.fm/280-2/)
- *Podcast*: [Zk-Podcast Episode 281: Exploring Lurk: a new Language for Recursive zk-SNARKs with Chhi'mèd Künzang and François Garillot](https://zeroknowledge.fm/281-2/)

### Talks & Lectures

- *Talk*: [ZK Study Club: SuperNova with Srinath Setty](https://www.youtube.com/watch?v=ilrvqajkrYY)
- *Talk*: [CCS & HyperNova with Srinath - Folding Schemes FTW](https://youtu.be/pDFmANwwIoY)
- *Talk*: [Advances in the Efficiency of Succinct Proofs (Ying Tong)](https://www.youtube.com/watch?v=KSGE6n66W1M)
- *Video Lectures*: [Zero-knowledge proof composition and recursion](https://www.youtube.com/watch?v=6mcCyQXm8vo&list=PLBJMt6zV1c7GeKkR2SUhzx9KSJ9TsEx6n)

### Forums

- *Forum*: [Privacy Scaling Explorations](https://appliedzkp.org/#top) [Discord Server](https://discord.gg/sF5CT5rzrR)
- *Forum*: [Lurk Lab](https://lurk-lab.com/) [Zulip Server](https://zulip.lurk-lab.com/)

## Applications

- [Nova-Scotia](https://github.com/nalinbhardwaj/Nova-Scotia)
    - This repository provides necessary middleware to take generated output of the Circom compiler (R1CS constraints and generated witnesses) and use them with Nova as a prover.
- [Lurk](https://github.com/lurk-lang/lurk-rs)
    - Lurk is a Turing-complete programming language for recursive zk-SNARKs. It is a statically scoped dialect of Lisp, influenced by Scheme and Common Lisp.
    - [Youtube account](https://www.youtube.com/@lurklab4264/featured)
    - *Talks*: [ZK Summit 9](https://www.youtube.com/watch?v=iLtv4yauW3s), [ZKProof workshop](https://www.youtube.com/watch?v=wKqiIoOeogo)
- [Nova-SHA256](https://github.com/avras/nova-sha256)
    - This repository provides a SHA-256 implementation utilizing Nova to repeatedly apply the SHA-256 compression function at each step.
    - The implementation utilizes SHA-256 from the [bellperson](https://github.com/filecoin-project/bellperson) library
