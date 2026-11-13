# Toward-Explainable-CMAES-with-LLMs
Official repository for the EvoStar 2027 paper “Toward the Explainable Design of Evolutionary Algorithms with LLMs: A Case Study on CMA-ES”, covering Large Language Models (LLMs), CMA-ES, Explainable Algorithm Design, and Automated Evolutionary Algorithm Design.

## Abstract

Large Language Models (LLMs) can generate and refine optimization algorithms, but it is often unclear which code modifications are responsible for the observed performance. This paper presents an explainability-oriented framework that generates variants of the Covariance Matrix Adaptation Evolution Strategy (CMA-ES) one modification at a time. A single LLM is called in four independent roles: an explainer that analyzes the baseline and proposes the first change, a generator that implements each change in the sampling, mean update, or adaptation of CMA-ES, an explainer that reviews the accumulated evidence after every evaluation, and a final explainer that reports on the selected variant. Deterministic rules classify each variant against the baseline on the 24 BBOB functions and select the parent of the next cycle. Runs with GPT-5 mini and Qwen3.5 produced different variants, based on Student-t sampling and on orthogonalized mirrored sampling, respectively, which were competitive with seven established CMA-ES configurations without dominating them. The cycle history made each design trajectory traceable, and the final explanations reconstructed it correctly, but each contained one unsupported causal claim, which shows that LLM explanations of algorithmic behavior require verification against the recorded evidence.

## Framework
The proposed framework refines CMA-ES variants through a closed-loop process composed of five stages:

1. **Initialization**
2. **Generation**
3. **Evaluation**
4. **Explainability-guided feedback**
5. **Final explanation**

Each run uses a single LLM in four independent roles:

<ul>
  <li><b>Explainer (E<sub>0</sub>):</b> analyzes the baseline CMA-ES and proposes the first modification.</li>
  <li><b>Generator (G):</b> implements each proposed modification as executable CMA-ES code.</li>
  <li><b>Explainer (E):</b> analyzes the accumulated experimental evidence after every evaluation and produces the feedback for the next cycle.</li>
  <li><b>Final Explainer (&Phi;):</b> generates the final explainability report for the selected variant.</li>
</ul>

The LLM calls are independent, and each role receives only the information required for its corresponding prompt. The classification of each generated variant, the selection of the best-performing variant, and the choice of the parent for the next cycle are handled through deterministic rules implemented in the framework.

<p>
  The iterative process starts from the baseline CMA-ES (A<sub>0</sub>). At each cycle, the Generator produces a new variant (A<sub>n</sub>), which is evaluated on the BBOB suite. The resulting performance is compared against the baseline, and the Explainer analyzes the accumulated evidence to determine the next proposed modification. The process continues until the predefined number of cycles is completed, after which the Final Explainer analyzes the selected best variant.
</p>

<p align="center">
  <img src="framework_images.jpg" width="700">
</p>

<p align="center">
  <b>Figure 1.</b> Framework for one run. Coloured boxes represent independent calls to the same LLM, with one colour assigned to each prompt (Table 3), whereas grey boxes represent deterministic operations performed by the code. The report R<sub>n</sub> and the selected parent A<sub>p(n+1)</sub> are provided as inputs to the Generator G in the next cycle. The Explainers E<sub>0</sub> and E additionally receive the set of reference mechanisms K.</em>
</p>
