# Advanced Experimentation & Causal Inference Framework

A quantitative experimentation and causal inference framework addressing the common failure modes of classical A/B testing in modern consumer platforms and fintech environments.

---

## 🎯 Objectives & Motivation

Standard hypothesis testing (such as Student's and Welch's $t$-tests) frequently underperforms in real-world digital products due to heavy-tailed revenue distributions, extreme skewness, and an abundance of zero-spending users. These conditions create severe analytical challenges:

1. **Traffic & Sample Size Constraints:** Under extreme metric variance, detecting realistic business-driven effects (e.g., a 3–5% uplift) via classical power calculations demands impractically large samples and prolonged test durations.
2. **The Winner's Curse & Extreme Outliers:** When tests run underpowered, nominal statistical significance is often driven by random outliers, leading to inflated effect estimates and misguided business rollouts.
3. **Computational Inefficiency at Scale:** Running bootstrap simulations and non-parametric tests directly on millions of unaggregated event logs creates unnecessary latency and compute overhead.
4. **Limits of Pure Randomization:** Critical product features, regulatory updates, or regional rollouts often cannot be randomly assigned at the user level, requiring quasi-experimental econometrics to isolate true treatment effects from macro trends.

This project delivers a production-grade toolkit designed to resolve these limitations by combining variance reduction, non-parametric aggregation, and panel econometrics.

---

## 🛠 Methodological Pipeline

* **Baseline EDA & Power Formulation:** Rigorous pre-experiment power modeling to determine sample size requirements and demonstrate the structural failure of unadjusted testing under high variance.
* **Variance Reduction (CUPED):** Leveraging pre-experiment user history to subtract individual baseline variance, neutralizing outlier bias and enabling high-powered experimentation on limited traffic.
* **Deterministic Hash Bucketing:** Employing MD5 hashing to project skewed microdata into normally distributed bucket means, guaranteeing asymptotic validity and fast computational scaling.
* **Quasi-Experimental Causal Inference (Panel DiD):** Implementing Difference-in-Differences with user fixed effects (first-differences) to eliminate unobserved entity heterogeneity and recover precise causal impacts in non-randomized environments.

---

## 📂 Repository Contents

* `QAProject.ipynb` — Full end-to-end reproducible Jupyter Notebook covering EDA, power analysis, SRM validation, CUPED variance reduction, deterministic bucketing, and panel DiD estimation.
* `Analytical_note.pdf` — Formal technical note containing mathematical derivations, methodological justifications, and comprehensive comparative discussions.
