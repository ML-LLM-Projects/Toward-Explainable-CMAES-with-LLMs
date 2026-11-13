<h2>LLM Prompts</h2>

<p>
  This section contains the four prompts used in the proposed framework. Each prompt corresponds to a specific LLM call and defines the information provided to the model, the task to be performed, and the expected output.
</p>

<ul>
  <li>
    <b>Prompt 1 – Initial LLM Explainer (E<sub>0</sub>):</b>
    contains the baseline CMA-ES implementation and the reference mechanisms used to analyze the initial algorithm and propose the first modification.
  </li>

  <li>
    <b>Prompt 2 – LLM Generator (G):</b>
    contains the selected parent algorithm and the explainability report from the previous cycle, which are used to generate the next executable CMA-ES variant.
  </li>

  <li>
    <b>Prompt 3 – Iterative LLM Explainer (E):</b>
    contains the baseline CMA-ES, the evaluated variant, the current best variant, the accumulated experimental evidence, and the reference mechanisms used to analyze the results and propose the next modification.
  </li>

  <li>
    <b>Prompt 4 – Final LLM Explainer (&Phi;):</b>
    contains the selected final variant and the accumulated evidence from the complete run, which are used to generate the final explainability report.
  </li>
</ul>
