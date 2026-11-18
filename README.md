# Eric Newton

I was a professional software engineer; I am now a master's student in artificial intelligence at Oregon State
University. I am interested in what trained neural networks compute, and I work on making networks small with
quantization and binarization, down to the GPU kernels that run them.

## Research

**Grothendieck identity hypersphere binarization** (2026)

A paper with Peter Cowal and Nicholas F. Marshall, under review at TMLR. It builds on
[G-Net](https://arxiv.org/abs/2511.21063) (NeurIPS 2025), by Prof. Alireza Aghasi, Prof. Marshall and colleagues. We
binarize each weight row and input of a linear layer by taking the signs of a random projection, `u ↦ sign(Gu)`, and
keep their norms in floating point. The paper proves lower bounds on the average error of this binarization, and shows
that random Hadamard blocks are asymptotically optimal in this construction when the weights and inputs are random.
Prof. Marshall led the theory, Dr. Cowal worked on both theory and experiments, and I designed and led the experiments
and the software. To test the theory, we trained a GPT-2-small model from scratch on WikiText-103. Averaged over its 48
weight matrices, the error with orthogonal blocks came within 0.1% of what the theory predicts.

**Low-bit GPU kernels** (private, research collaboration, 2026)

For Prof. Aghasi's angular-networks paper (NeurIPS 2026), I directed the development of CUDA and Triton kernels for its
low-bit layers: binary matrix multiplication with XNOR and popcount, Hadamard transforms, and the backward pass for
training. I also benchmarked latency and memory for a ViT-S/16 and a ResNet-18 built from these layers, against the same
models in dense FP16.

**Weight signatures of RL fine-tuning** (paper in preparation, sole author, since September 2026)

I am testing published claims about how reinforcement-learning fine-tuning changes the weights of language models, using
null models that keep each update's size and timing but randomize its sign.

## Systems

I have put a lot of work into the two systems below. Since coding agents let you build everything around your own way of
working, these are built entirely around mine. The task of turning them into something other people could pick up and
use would take real work, so I am keeping them private and describing them below for now.

**Options paper-trading research system** (private, November 2025 to present)

A system that tests whether a decision model can find an edge in US equity and ETF options. It tracks volatility with
Hierarchical Gaussian Filters, chooses policies with a modified expected-free-energy score, and runs a debate between
locally hosted language models. I designed it, directed all of its software development, and run the whole thing myself,
from the market-data feed to the model servers. It has been paper trading on live market data since May 2026.

Apart from the software, much of my work on it is checking whether an apparent edge survives real quotes and trading
costs. For one trading rule, I ran a pre-registered replay on option quotes from 2008 to 2025. As a control, I rebuilt a
published Cboe index whose result is known. The control failed, so I kept the replay's result sealed until I found the
cause: an optimistic bias in one quote source. With or without a correction for that, the replay found no edge for the
rule.

**Research apparatus** (private, May 2026 to present)

A system that uses language-model agents to automate much of the work on the RL study above and on post-training
quantization experiments. I designed it and direct its development. I generally choose the questions, set the rules, and
decide which directions are publishable. A lot of the engineering is in the checks: the system searches its own paper
library and recent arXiv papers for prior work I might have missed, the job queue won't take an experiment's GPU job
without a pre-registration, pre-registered results stay sealed until the analysis that reads them is frozen, and any
claim that leaves the repository is first reviewed by a model from a different family.

## Before graduate school

- Software engineer at Puppet by Perforce (2021 to 2024). I worked on the Clojure backend of Puppet Enterprise, a
  distributed system that configures servers across large fleets. Most of the forks on this profile are from that job.
- Software test engineer at MKS Instruments (2020 to 2021).
- [ochat](https://github.com/rileynewton/ochat), a small multicore chat program in OCaml.

**Languages:** Python, C/C++, C#, Clojure, OCaml, SQL, Bash.

**Tools:** PyTorch, CUDA, Triton.
