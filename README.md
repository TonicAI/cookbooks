# Tonic.ai Cookbooks

Hands-on, end-to-end cookbooks for building with synthetic and de-identified data —
each one a runnable notebook backed by a real experiment.

## Cookbooks

| Cookbook | Products | Run it |
|---|---|---|
| **Safely fine-tuning with sensitive data** — de-identify clinical notes with consistent synthetic PII, fine-tune on the result, and measure that synthesis costs nothing | [Tonic Textual](https://www.tonic.ai/textual) + [Fireworks AI](https://fireworks.ai) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TonicAI/cookbooks/blob/main/sft/healthcare/textual_fireworks_fine_tune.ipynb) |
| **Zero-label fine-tuning with synthetic conversations** — generate clinical conversations structure-first so extraction labels are correct by construction, then trace the accuracy-vs-data curve | [Tonic Fabricate](https://fabricate.tonic.ai) + [Fireworks AI](https://fireworks.ai) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TonicAI/cookbooks/blob/main/sft/clinical_conversations/fabricate_fireworks_transcript_extraction.ipynb) |
| **Teaching an AI agent your policies with RFT** — reinforcement fine-tune an agent against a fully synthetic store whose APIs enforce a written policy, then show the tuned agent follows a *revised* policy document without retraining | [Tonic Fabricate](https://fabricate.tonic.ai) + [Fireworks AI](https://fireworks.ai) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TonicAI/cookbooks/blob/main/rft/retail_policy/fabricate_fireworks_policy_rft.ipynb) |

## What's inside

- `sft/healthcare/textual_fireworks_fine_tune.ipynb` — the Textual × Fireworks cookbook:
  synthesis-based de-identification with per-record consistency, two-arm LoRA fine-tuning
  (synthetic vs. original data), and evaluation on real held-out notes.
- `sft/clinical_conversations/fabricate_fireworks_transcript_extraction.ipynb` — the
  Fabricate × Fireworks cookbook: structure-first synthetic conversations with
  machine-verified labels ([TonicAI/synthetic_clinical_conversations](https://huggingface.co/datasets/TonicAI/synthetic_clinical_conversations)),
  a zero-shot capability ladder, and a three-tier fine-tuning learning curve.
- `rft/retail_policy/fabricate_fireworks_policy_rft.ipynb` — the Fabricate × Fireworks
  **RFT** cookbook: a synthetic retail environment whose mock APIs enforce a written store
  policy, deterministic episode rewards (exact action match, no LLM judge), reinforcement
  fine-tuning of qwen3-32b (held-out policy application 44% → 67%), and policy-variation
  experiments (prompt swap + 8-policy grid) showing the policy stays a prompt-level
  control rather than being baked into the weights.

All notebooks run on a free Colab CPU runtime; the heavy lifting happens on Tonic and
Fireworks infrastructure.

Each notebook states its own API-key and cost requirements up front.

## Data

Clinical examples use [TonicAI/synthetic_clinical_notes](https://huggingface.co/datasets/TonicAI/synthetic_clinical_notes)
(derived from [Synthea](https://synthetichealth.github.io/synthea/) patient records) and
[TonicAI/synthetic_clinical_conversations](https://huggingface.co/datasets/TonicAI/synthetic_clinical_conversations)
(generated structure-first with Tonic Fabricate). Both datasets are fully synthetic — no real
patient data appears anywhere in these cookbooks.
The retail-agent cookbook generates its entire environment (users, orders, products,
scenarios) live in Fabricate — every record is synthetic. The frozen reference world from
the published run is available as
[TonicAI/synthetic_retail_policy_environment](https://huggingface.co/datasets/TonicAI/synthetic_retail_policy_environment).
