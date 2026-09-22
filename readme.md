# AIMES: Adaptive Multi-Value Control in Large Language Models

This repository contains the anonymous implementation accompanying the paper:

**Adaptive Multi-Value Control in Large Language Models via Causal Activation Steering**

AIMES is a framework for adaptive activation-level steering of multiple human values within a single generation. It constructs model- and layer-specific bipolar value directions and uses intermediate-layer vocabulary readouts as online observers. The resulting observer scores determine value-specific steering coefficients that are updated during decoding.

The experiments study five Moral Foundations Theory (MFT) dimensions:

- Care / Harm
- Fairness / Cheating
- Loyalty / Betrayal
- Authority / Subversion
- Sanctity / Degradation

## Repository Structure

| Notebook | Description |
|---|---|
| `contrastivepair_generation_final.ipynb` | Generates matched positive--negative contrastive vignette pairs for the five MFT dimensions. |
| `valuedirection_generation_final.ipynb` | Extracts model- and layer-specific bipolar value directions from the contrastive corpus. |
| `AIMES_Jlens_final.ipynb` | Runs AIMES using J-Lens as the intermediate-layer value observer. |
| `AIMES_LL_final.ipynb` | Runs AIMES using Logit Lens as the intermediate-layer value observer. |
| `fixed_multivalue_steering_final.ipynb` | Implements the Fixed Multi-Value Steering baseline using the same value directions and intervention layers as AIMES. |
| `prompt_steering_baseline_final.ipynb` | Implements the prompt-based multi-value steering baseline. |
| `phase_1_openloopsteering_final.ipynb` | Auxiliary notebook for examining individual value-direction steering behavior. |

## Models

The experiments include five instruction-tuned models from three model families:

- Gemma-3-4B-IT
- Gemma-3-12B-IT
- Qwen3-4B
- Qwen3-14B
- Llama-3.1-8B-Instruct

Interventions are evaluated at multiple model-specific depths spanning the transformer network.

## Multi-Value Objectives

The main experiments consider three multi-value steering objectives:

$(\uparrow \mathrm{Care}, \uparrow \mathrm{Fairness})$, $(\uparrow \mathrm{Loyalty}, \uparrow \mathrm{Authority}),$  and
$(\uparrow \mathrm{Care}, \uparrow \mathrm{Fairness}, \downarrow \mathrm{Sanctity})$.

These objectives represent different interaction regimes in the learned value-direction geometry.

## Recommended Workflow

The notebooks are organized around the following pipeline:

1. **Generate matched contrastive value pairs**
   - `contrastivepair_generation_final.ipynb`

2. **Construct value directions**
   - `valuedirection_generation_final.ipynb`

3. **Run the fixed multi-value baseline**
   - `fixed_multivalue_steering_final.ipynb`

4. **Run the prompt-steering baseline**
   - `prompt_steering_baseline_final.ipynb`

5. **Run AIMES with J-Lens**
   - `AIMES_Jlens_final.ipynb`

6. **Run AIMES with Logit Lens**
   - `AIMES_LL_final.ipynb`

The notebooks contain the model loading, intervention, generation, and result-saving logic used for the corresponding experiments.

## Reproducibility

The repository is intended to accompany the anonymous submission and contains the core implementation for:

- contrastive value-pair construction;
- layer-wise value-direction extraction;
- adaptive AIMES steering;
- J-Lens and Logit Lens observers;
- Fixed Multi-Value Steering;
- prompt-based steering.

Exact experimental settings, intervention layers, evaluation metrics, and statistical procedures are described in the paper.

## Citation

Citation information will be added after the anonymous review period.
