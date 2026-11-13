### GPT5_MINI_GENERATED.ipynb

This file contains the final CMA-ES variant selected from the GPT-5 mini run. 
The variant incorporates adaptive Student-t heavy-tailed sampling, stagnation-driven 
tail adaptation, and a transient population-size increase while preserving the total 
evaluation budget.

The experimental settings reported in the paper were applied externally during the 
BBOB evaluation procedure.

### Qwen3.5 Final Variant

This file contains the final CMA-ES variant selected from the Qwen3.5-122B-A10B run. The variant incorporates **Orthogonalized Mirrored Sampling**, **boundary reflection handling**, and an **elitist mean update**, while preserving the standard CMA-ES step-size and covariance adaptation mechanisms.

In the sampling stage, a subset of search directions is orthogonalized using QR decomposition and combined with their mirrored counterparts to reduce redundancy and improve directional coverage. Candidate solutions that exceed the search-domain bounds are handled through reflection rather than clipping. During the mean update, the weighted offspring recombination is combined with the best solution from the previous generation using a small elitist contribution.

The experimental settings reported in the paper were applied during the BBOB evaluation procedure.
