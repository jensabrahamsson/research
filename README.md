# Research: Jens Abrahamsson

I am an independent researcher and developer based in Sweden. I worked as a professional systems developer until 2015. I have no institutional affiliation. My current research is empirical and computational. It looks at how newly launched tokens behave on-chain, how to detect fraud transparently, and how to evaluate predictive systems honestly. I build all of it with a multi-LLM agentic software-engineering workflow.

This repository describes the research. It contains no source code. The underlying systems are private and partly commercial. The research outputs listed below are intended to be public and non-commercial.

## Research themes

### 1. Explainable, non-ML, linear-time rug and honeypot detection
Static analysis of EVM bytecode that flags a token contract's *capability* to defraud holders, such as wallet blacklisting, hidden self-destruct, mutable transfer fees, and time- or balance-based traps. It does not ask only whether the token is a honeypot right now. Every verdict can be traced to concrete patterns, and the analysis needs no trained model.

Internal evaluation (not yet peer reviewed): against 6,050 externally labelled tokens, plus fork-simulation sell tests as a second ground truth, the analyzer detected 95–100% of honeypots, depending on the ground-truth definition, at roughly 1,200 tokens per second. "Safe" tokens that it blocked mostly carried latent rug capabilities that had not yet been activated. How to count these is discussed openly rather than hidden.

### 2. Funder-lineage "rug memory"
A deterministic, explainable rule that looks at the funding history behind new token launches. It identifies funders whose recent launches collapsed before a modelled exit. The rule is computed in a single as-of pass over settled outcomes, with strict controls against look-ahead leakage. The frozen research dataset contains 3,422 settled outcomes from 367 funders.

### 3. Time-to-rug prediction
Predicting *when* a newly launched token is likely to fail, not just *whether* it will. Datasets are split chronologically into train, calibration and holdout sets, and audited for leakage. For example, later market data must never leak into decision-time features.

### 4. Honest evaluation in forced simulation
Strategies and detectors are evaluated in a forced-simulation environment before any real capital is involved. Analyses are reproducible and pinned by hash. They report Wilson confidence intervals and confounders, and they publish negative results. For example, one month-long study concluded that a hypothesised on-chain block pattern did *not* reliably separate rugs from successful outcomes.

### 5. Multi-LLM agentic software engineering
The systems above are built and reviewed with several LLM coding agents working in parallel. Independent models review each other's plans and code, and changes go through explicit safety contracts and fail-closed defaults. I treat this workflow as a research subject in its own right.

## Supporting projects
- **Pohlman:** calibrated probabilistic temperature forecasting for weather prediction markets. It collects decision-time-clean evidence for replay and calibration. ML weather models such as GraphCast and Pangu are treated as challengers that must earn promotion on reproducible holdout evidence.
- **Nostradamus:** a read-only prediction-market intelligence system that produces probability assessments, evidence and forecast ledgers with full provenance. Execution is limited to simulation.

## Planned outputs (6–12 months)
- A preprint on explainable, linear-time rug and honeypot detection, with an honest evaluation
- A public, labelled dataset of token outcomes
- Open-source release of non-proprietary analysis tools
- Write-ups on forecast calibration and on multi-model agentic software engineering

These outputs will be linked from this repository as they are released.
