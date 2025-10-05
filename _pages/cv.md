---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* M.S. in Financial Technology (Artificial Intelligence and Finance Track), Tsinghua University, GPA 4.0
  * Honors: Excellence Scholarship, covering 50% tuition
* B.S. in Computer Science and Finance (dual degree), GPA 3.3
  * Select Courses: Econometrics, Probability and Statistics, Deep Learning, Natural Language Processing, Data Mining

Professional Experience
======
* 02/2025 – Present: AI Research Intern
  * Zhipu AI (Series D), Beijing, China
  * Data Methodology Innovation: Conducted research on Enhancing the Perception Ability of Visual Language Models (VLMs) through RL via Data Engine, designing a synthetic data engine that creates auto-verifiable perception QA tasks to support stable on-policy GRPO training and boost fine-grained visual perception.
  * GRPO Mixed-Policy Extension: Built a mixed-policy GRPO variant blending on-policy rollouts with high-reward replay, boosting convergence by 20% and accuracy by +2.3% across 12 benchmarks (e.g. MathVision).

* 11/2024 – 01/2025: Quantitative Research Intern
  * CICC-Fixed Income, Beijing, China
  * Vol Curve Modeling: Enhanced gold futures options wing model by refining fit initialization and mid-price computation to mitigate Call-Put Implied Volatility (CPIV) spread noise, reducing average RMSE by 43%.
  * Outlier Detection: Developed a liquidity-aware loss function with orderbook depth and applied Isolation Forest on Greeks to detect and remove anomalous quotes, increasing R2 of the smile fit by 20%.

* 04/2024 – 08/2024: Quantitative Research Intern
  * Boyu Capital, Beijing, China
  * Order Book Reconstruction: Reconstructed tick-level Limit Order Book (LOB) from tick data, recovering 50 levels of bid/ask depth with millisecond precision for downstream modeling.
  * HFT Forecasting: Designed a CNN model to forecast 30-second price movement by stacking temporal 1-D convolutions over 50-level bid/ask sequences in LOB, achieving 20+% accuracy and 14% AUC lift over baselines.
  * Feature Engineering: Generated 100+ microstructure features (order flow imbalance, liquidity slopes, etc.) using auto-feature pipelines, trained a LightGBM classifier, and achieved 2+ post-cost Sharpe out sample.
  
Skills & Competitions
======
**Programming:** Python, C++
**Certificates:** FRM Level 1, CFA Level I (exam completed, results expected Oct)

**Kaggle -- CURE-Bench @NeurIPS 2025**
* Built a multi-agent system for multi-hop medical tool calls with optimized retrieval and reasoning pipelines.
* Currently ranked #1/223 under team name einsteinGauss

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams
