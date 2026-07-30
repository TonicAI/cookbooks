# Tonic.ai Cookbooks

Hands-on, end-to-end playbooks for building with synthetic and de-identified data —
each one a runnable notebook backed by a real experiment.

## Playbooks

| Playbook | Products | Run it |
|---|---|---|
| **Safely fine-tuning with sensitive data** — de-identify clinical notes with consistent synthetic PII, fine-tune on the result, and measure that synthesis costs nothing | [Tonic Textual](https://www.tonic.ai/textual) + [Fireworks AI](https://fireworks.ai) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TonicAI/cookbooks/blob/main/sft/healthcare/textual_fireworks_fine_tune.ipynb) |
| **Zero-label fine-tuning with synthetic conversations** — generate clinical conversations structure-first so extraction labels are correct by construction, then trace the accuracy-vs-data curve | [Tonic Fabricate](https://fabricate.tonic.ai) + [Fireworks AI](https://fireworks.ai) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TonicAI/cookbooks/blob/main/sft/clinical_conversations/fabricate_fireworks_transcript_extraction.ipynb) |

## What's inside

- `sft/healthcare/textual_fireworks_fine_tune.ipynb` — the Textual × Fireworks playbook:
  synthesis-based de-identification with per-record consistency, two-arm LoRA fine-tuning
  (synthetic vs. original data), and evaluation on real held-out notes.
- `sft/clinical_conversations/fabricate_fireworks_transcript_extraction.ipynb` — the
  Fabricate × Fireworks playbook: structure-first synthetic conversations with
  machine-verified labels ([TonicAI/synthetic_clinical_conversations](https://huggingface.co/datasets/TonicAI/synthetic_clinical_conversations)),
  a zero-shot capability ladder, and a three-tier fine-tuning learning curve.

Both run on a free Colab CPU runtime; all heavy lifting happens on Tonic and Fireworks
infrastructure.

Each notebook states its own API-key and cost requirements up front.

## Data

Clinical examples use [TonicAI/synthetic_clinical_notes](https://huggingface.co/datasets/TonicAI/synthetic_clinical_notes)
(derived from [Synthea](https://synthetichealth.github.io/synthea/) patient records) and
[TonicAI/synthetic_clinical_conversations](https://huggingface.co/datasets/TonicAI/synthetic_clinical_conversations)
(generated structure-first with Tonic Fabricate). Both are fully synthetic — no real
patient data appears anywhere in these playbooks.
