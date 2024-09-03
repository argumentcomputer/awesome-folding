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
  * [Deep Space Nine (New commitment schemes, new lookup & proof arguments)](#deep-space-nine-new-commitment-schemes-new-lookup--proof-arguments)
- [Code (software repositories)](#code-software-repositories)
  * [Reference implementations](#reference-implementations)
  * [Teaching / experimental implementations](#teaching--experimental-implementations)
  * [Code Explorations](#code-explorations)
- [Other resources (podcasts, etc)](#other-resources-podcasts-etc)
  * [Podcast episodes](#podcast-episodes)
  * [Talks & Lectures](#talks--lectures)
    + [Zuzalu talks](#zuzalu-talks)
    + [Articles](#articles)
  * [Forums](#forums)
- [Applications](#applications)

<!-- tocstop -->

## Writings (papers, blog posts, etc)

### Prequels

#### Arithmetization

A gentle introduction to Plonk-like arithmetization, lookup arguments and the birth of lookup arguments in the Plonk world.

- [From AIRs to RAPs](https://hackmd.io/@aztec-network/plonk-arithmetiization-air)
- [A Brief history of lookup arguments](https://github.com/ingonyama-zk/papers/blob/main/lookups.pdf)
- [Multiset checks in PLONK and Plookup](https://hackmd.io/@oL_Ko9OQSfeZhjlLHm2XDw/ByFgSDA7D)

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
- [Revisiting the Nova Proof System on a Cycle of Curves](https://eprint.iacr.org/2023/969)
    - [Presentation](https://www.youtube.com/watch?v=l-F5ykQQ4qw)
    - This paper analyzes the security of the Nova proving system when implemented on a cycle of curves.
    The paper exploits a soundness bug in the original implementation (since patched) and produces a
    convincing proof of $2^{75}$ rounds of the Minroot VDF in 1.46 seconds. A new optimized and secure
    system is introduced together with a formal security proof.
- [CycleFold: Folding-scheme-based recursive arguments over a cycle of elliptic curves](https://eprint.iacr.org/2023/1192)
   - CycleFold uses the second curve in the cycle to merely represent a single
   scalar multiplication ( 1,000--1,500 multiplication gates). CycleFold then
   folds invocations of that tiny circuit on the first curve in the cycle. This
   is nearly an order of magnitude improvement over the prior state-of-the-art
   in terms of circuit sizes on the second curve.
- [Reverie: an end-to-end accumulation scheme from Cyclefold](https://eprint.iacr.org/2023/1888)
    - _"In this technical note, we propose an informal notion of an end-to-end IVC scheme, which means that the amount of data that the prover needs exchange with the previous prover to continue the computation is small.
    We explore the existing design space from this point of view, and suggest an approach to constructing such a scheme by combining the PlonK proof system with the recent Cyclefold construction."_

### Nova Extensions (without high-degree gates)

Extensions to the Nova proof system that explore PCS in terms of linear codes, folding, and other concepts.

- [Linear algebra and zero-knowledge](https://www.youtube.com/watch?v=dSsUfKgZlkk) ([paper](https://angeris.github.io/papers/zk-linalg.pdf))
- [Origami – A Folding Scheme for Halo2 Lookups](https://hackmd.io/@aardvark/rkHqa3NZ2)
    - [Folding Custom Gates with Verifier Input](https://arxiv.org/abs/2401.11364)
- [Folding for Arbitrary Polynomial Custom Gates and Lookups](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)
- [Folding endgame](https://zkresear.ch/t/folding-endgame/106)

### HyperNova / ProtoStar : The next generation (with high-degree gates)

- [Customizable constraint systems for succinct arguments](https://eprint.iacr.org/2023/552)
  This paper introduces customizable constraint system (CCS), a generalization of R1CS that can simultaneously capture R1CS, Plonkish, and AIR without overheads.
- [HyperNova: Recursive arguments for customizable constraint systems](https://eprint.iacr.org/2023/573)
  This paper introduces HyperNova, a recursive argument for proving incremental computations whose steps are expressed with CCS. The prover’s cost at each step is dominated by a single multi-scalar multiplication (MSM) of size equal to the number of variables in the constraint system, which is optimal when using an MSM-based commitment scheme.
- [KiloNova: Non-Uniform PCD with Zero-Knowledge Property from Generic Folding Schemes](https://eprint.iacr.org/2023/1579)
  This paper build a non-uniform ZK-PCD scheme (KiloNova) from the generic folding scheme and improve its performance with some optimization techniques, such as circuit aggregation and decoupling.
    - [Presentation](https://www.youtube.com/watch?v=FDE8WD1QA_Y)
- [Proof-Carrying Data from Multi-folding Schemes](https://eprint.iacr.org/2023/1282)
  This paper generalizes HyperNova to support folding multiple instances of CCS and multiple instance of LCCS into 1 LCCS, in contrast to the original work which folds 1 CCS and 1 LCCS into 1 LCCS.
- [ProtoStar: Generic Efficient Accumulation/Folding for Special Sound Protocols](https://eprint.iacr.org/2023/620)
  We provide a generic, efficient accumulation scheme for any (2k-1)-move special-sound protocol with a verifier that checks l degree-d equations. The accumulation verifier only performs k+2 elliptic curve multiplications and k+d+O(1) field/hash operations.
    - [Presentation](https://www.youtube.com/watch?v=tt00TLFJPpc)
- [ProtoGalaxy: Efficient ProtoStar-style folding of multiple instances](https://eprint.iacr.org/2023/1106)
  Building on ideas from  ProtoStar, we construct a folding scheme where the recursive verifier's "marginal work", beyond linearly combining witness commitments, consists only of a logarithmic number of field operations and a constant number of hashes. Moreover, our folding scheme performs well when _folding multiple instances at one step_.
    - [Presentation](https://www.youtube.com/watch?v=SpkTvRia1EA)

### Deep Space Nine (New commitment schemes, new lookup & proof arguments)

- [LatticeFold: A Lattice-based Folding Scheme and its Applications to Succinct Proof Systems](https://eprint.iacr.org/2024/257)
  The first lattice-based folding scheme that leads to post-quantum secure IVC/PCD/SNARKs. Surprisingly, we estimate the performance to be competitive with top pre-quantum folding schemes.
    - [Presentation](https://www.youtube.com/watch?v=DVHfukc35xk)
    - [zkStudyClub presentation](https://www.youtube.com/watch?v=-k8s7vVUx6s)
- [Proofs for Deep Thought: Accumulation for large memories and deterministic computations](https://eprint.iacr.org/2024/325)
  We break through the "witness barrier" and go beyond the "lookup singularity". We show how to do reads AND writes to memory by committing to just 4 small elements. We also show how to avoid committing to intermediate witnesses.
- [Mangrove: A Scalable Framework for Folding-based SNARKs](https://eprint.iacr.org/2024/416)
  We develop a new "uniformizing" compiler for NP statements that converts any poly-time computation to a sequence of identical simple steps
- [Accumulation without Homomorphism](https://eprint.iacr.org/2024/474)
  We construct an accumulation scheme from *non-homomorphic* vector commitments which can be realized from solely symmetric-key assumptions (e.g. Merkle trees).

## Code (software repositories)

### Reference implementations

- [microsoft/nova](https://github.com/microsoft/Nova)
- [argumentcomputer/arecibo](https://github.com/argumentcomputer/arecibo): This repository is a fork of the original. It's an incubator for experimenting with more advanced variants of the original software and working out the kinks in them

### Teaching / experimental implementations

- [nova-study](https://github.com/arnaucube/nova-study/): Implementation of Nova using arkworks-rs just forlearning purposes.
- [supernova](https://github.com/jules/supernova): Experimental implementation of the SuperNova protocol
- [multifolding-poc](https://github.com/privacy-scaling-explorations/multifolding-poc): Experimental implementation of HyperNova
- [microsoft/nova hypernova experimental PR](https://github.com/microsoft/Nova/pull/175): Experimental implementation of HyperNova in reference implementation
- [ccs-hack](https://github.com/thor314/ccs-hack): a hack implementation of CCS generic implementation
- [protogalaxy-poc](https://github.com/arnaucube/protogalaxy-poc): Proof of concept implementation of ProtoGalaxy
- [pse/nova experimental ParaNova PR](https://github.com/privacy-scaling-explorations/Nova/pull/11): Experimental implementation of ParaNova
- [pse/folding-schemes](https://github.com/privacy-scaling-explorations/folding-schemes/): Experimental arkworks library for accommodating different folding schemes
- [snarkify/sirius](https://github.com/snarkify/sirius): open-source constraint-system-agnostic folding framework for Incrementally Verifiable Computation
- [PayneJoe/PNova](https://github.com/PayneJoe/PNova): Our target is to implement a plonkish versioned NOVA, folding multiple Customer Gate/Lookup instances into one respectively.

### Code Explorations

Code implementations and explorations related to the Nova proof system, including benchmarks, specifications, and experimental versions.

- [Nova benchmarks](https://hackmd.io/@oskarth/rJmSaOtZ2)
- [Nova benchmarks (native SHA256)](https://hackmd.io/u3qM9s_YR1emHZSg3jteQA)
- [Nova wishlist and next steps](https://hackmd.io/@oskarth/SJRm4zYbn)
- [Nova-based ZKVM spec](https://hackmd.io/@CPerezz/ByTmhi6yn)
- [Origami-benchmarks](https://hackmd.io/vn7hWnjCQXCEpQvPDflL8g)
- [Notes on ProtoGalaxy](https://arnaucube.com/blog/protogalaxy.html)
- [Halo2 + Protostar](https://github.com/geometryresearch/protostar)

## Other resources (podcasts, etc)

### Podcast episodes

- _Podcast_: [ZK-Podcast Episode 277: Nova and beyond with Srinath Setty](https://www.youtube.com/watch?v=hRza_k8i16s)
- _Podcast_: [ZK-Podcast Episode 280: ProtoStar with Benedikt Bünz and Binyi Chen](https://zeroknowledge.fm/280-2/)
- _Podcast_: [Zk-Podcast Episode 281: Exploring Lurk: a new Language for Recursive zk-SNARKs with Chhi'mèd Künzang and François Garillot](https://zeroknowledge.fm/281-2/)

### Talks & Lectures

- _Talk_: [ZK Study Club: SuperNova with Srinath Setty](https://www.youtube.com/watch?v=ilrvqajkrYY)
- _Talk_: [CCS & HyperNova with Srinath - Folding Schemes FTW](https://youtu.be/pDFmANwwIoY)
- _Talk_: [Advances in the Efficiency of Succinct Proofs (Ying Tong Lai)](https://www.youtube.com/watch?v=KSGE6n66W1M)
- _Talk_: [Folding Circom circuits: A ZKML case study (Cathie So)](https://www.youtube.com/watch?v=jb6HDEtY4CI)
- _Talk_: [ZK Study Club: Protostar with Binyi Chen](https://www.youtube.com/watch?v=wtxVYiZh7zc)
- _Talk_: [(Super)Nova (Scotia): Unpacking Nova](https://www.youtube.com/watch?v=N6RW_YhLMNw)
- _Talk_: [SBC'23 Session 4: Efficient SNARKs From Folding Schemes](https://www.youtube.com/watch?v=0C3HhWNCpls)
- _Talk_: [ZKP MOOC Lecture 10: Recursive SNARKs](https://www.youtube.com/watch?v=0LW-qeVe6QI)
- _Talk_: [ZK Summit 10: "Recent advances in folding schemes" (Liam Eager)](https://www.youtube.com/watch?v=mqBkhZGNkis)
- _Talk_: [ZK Summit 10: "Visual ProtoStar" (Adrian Hamelink)](https://www.youtube.com/watch?v=Arg63wKiS5g)

#### Zuzalu talks

- _Talk_: [Folding Scheme Math Buildding Blocks (Ying Tong Lai)](https://zuzalu.streameth.org/session/152)
- _Talk_: [SuperNova and Parallelizing Nova (Carlos Perez, Nalin Bardaj)](https://zuzalu.streameth.org/session/169)
- _Talk_: [Nova Track Ad-Hoc Session: ZK Week Research Projects Discussion (Barry Whitehat, Justin Drake, Nalin Bardaj)](https://zuzalu.streameth.org/session/432)
- _Talk_: [Ad-Hoc Session on Goblin PLONK + Nova (Zachary Williamson)](https://zuzalu.streameth.org/session/451)

#### Articles

- _Article_: [Parallelizing Nova - Visualizations and Mental Models behind Paranova](https://zkresear.ch/t/parallelizing-nova-visualizations-and-mental-models-behind-paranova/198)
- _Article_: [Towards a Nova-based ZK-VM](https://zkresear.ch/t/towards-a-nova-based-zk-vm/105)
- _Article_: [Nova: from IVC to general PCD for zkMapReduce](https://lagrangelabs.notion.site/Nova-from-IVC-to-general-PCD-for-zkMapReduce-d04afec2d70c47db9dfb67e84d0d796e?pvs=4)
- _Article_: [An incomplete guide to Folding: Nova, Sangria, SuperNova, HyperNova, Protostar](https://taiko.mirror.xyz/tk8LoE-rC2w0MJ4wCWwaJwbq8-Ih8DXnLUf7aJX1FbU)
- _Article_: [Diagonal folding: Folding protocols with a large amount of rounds using 2-round Protostar](https://zkresear.ch/t/diagonal-folding-folding-protocols-with-a-large-amount-of-rounds-using-2-round-protostar/214)
- _Article_: [SuperSpartan by Hand](https://anoma.net/blog/superspartan-by-hand)
- _Article_: [HyperNova By Hand](https://anoma.net/blog/hypernova-by-hand)
### Forums

- _Forum_: [Privacy Scaling Explorations](https://appliedzkp.org/#top) [Discord Server](https://discord.gg/sF5CT5rzrR)
- _Forum_: [Argument](https://argument.xyz/) [Zulip Server](https://zulip.argument.xyz/)

## Applications

- [Nova-Scotia](https://github.com/nalinbhardwaj/Nova-Scotia)
    - This repository provides necessary middleware to take generated output of the Circom compiler (R1CS constraints and generated witnesses) and use them with Nova as a prover.
- [Lurk](https://github.com/argumentcomputer/lurk-rs)
    - Lurk is a Turing-complete programming language for recursive zk-SNARKs. It is a statically scoped dialect of Lisp, influenced by Scheme and Common Lisp.
    - [Youtube account](https://www.youtube.com/@argumentcomputer/featured)
    - _Talks_: [ZK Summit 9](https://www.youtube.com/watch?v=iLtv4yauW3s), [ZKProof workshop](https://www.youtube.com/watch?v=wKqiIoOeogo)
- [Nova-SHA256](https://github.com/avras/nova-sha256)
    - This repository provides a SHA-256 implementation utilizing Nova to repeatedly apply the SHA-256 compression function at each step.
    - The implementation utilizes SHA-256 from the [bellperson](https://github.com/filecoin-project/bellperson) library
- [Zator: Verified inference of a 512-layer neural network using recursive SNARKs](https://github.com/lyronctk/zator)
- [Reef: Fast Succinct Non-Interactive Zero-Knowledge Regex Proofs](https://eprint.iacr.org/2023/1886)
    - A system for generating zero-knowledge proofs that a committed document matches or does not match a regular expression.
    - [Github repo](https://github.com/eniac/Reef)
