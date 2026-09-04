---
title: "Difference-in-Differences with “Bad Controls”"
date: 2026-08-04
status: working
weight: 10
coauthors:
  - name: Carolina Caetano
    url: http://www.carolinacaetano.net
  - name: Brantly Callaway
    url: https://bcallaway11.github.io
  - name: Stroud Payne
    url: https://as.vanderbilt.edu/economics/bio/stroud-payne/
links:
  - name: arXiv
    url: https://arxiv.org/abs/2608.03881
  - name: Vignette
    url: https://hsantanna.org/badcontrols/
  - name: R package
    url: https://github.com/hugosantanna/badcontrols
figures:
  - src: /images/att_badcontrols.png
    alt: Bias of two-way fixed effects estimates under time-varying covariates
citation: "Caetano, Carolina, Brantly Callaway, Stroud Payne, and Hugo Sant'Anna. 2026. “Difference-in-Differences with ‘Bad Controls’.” arXiv:2608.03881."
aliases:
  - /workingpapers/badcontrols/
---

This paper considers difference-in-differences identification strategies when the parallel trends assumption holds after conditioning on covariates that may themselves be affected by the treatment (often referred to as "bad controls"). We show that common approaches such as simply dropping bad controls are often ill-advised and develop two alternative approaches that allow bad controls to function as genuine controls despite being affected by treatment. First, we derive explicit conditions that rationalize conditioning only on pre-treatment values of the bad control, leading naturally to the Callaway and Sant'Anna (2021) estimator with pre-treatment values as covariates. Second, under a covariate unconfoundedness condition, we develop imputation and double/debiased machine learning estimators that recover the average treatment effect on the treated. We extend these results to staggered treatment adoption, provide pre-tests for the identifying assumptions, and apply the methods to study the effects of job displacement on earnings.
