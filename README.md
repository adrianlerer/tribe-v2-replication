# TRIBE v2 — Synthetic Populations as Institutional Stress Tests

**Replication repository for:**
> Lerer, I.A. (2026). Synthetic Populations as Institutional Stress Tests: Constitutional Lock-In and Model-Specific Phase Transitions in LLM Synthetic Societies.

Zenodo community: [law-as-extended-phenotype](https://zenodo.org/communities/law-as-extended-phenotype/)
Author: Ignacio Adrián Lerer · [adrian@lerer.com.ar](mailto:adrian@lerer.com.ar) · ORCID: 0009-0007-6378-9749

---

## What this repo contains

- Full experiment design (prompts, CLI encoding, action taxonomy)
- Cost estimator that validates model IDs against live OpenRouter metadata
- Analysis and metric scripts (TVD, anomia, bootstrap, judge)
- Reproduction instructions for Phase 2A and Phase 2B
- All result files (events.jsonl, inference.json, judge_report.json, bootstrap)

This repo does **not** contain API keys, proprietary model weights, or business-sensitive research directions.

---

## Quick start

```bash
pip install aiohttp pandas numpy scipy
export OPENROUTER_API_KEY='sk-or-v1-...'

# Validate model IDs and estimate cost (no spend)
python experiments/cost_estimate.py --replicas 5 --cycles 3 --agents 2

# Run Phase 2A smoke (tiny, ~$0.15)
TRIBE_MAX_COST_USD=1 python experiments/paid_stateful.py \
  --replicas 1 --cycles 2 --agents 2 \
  --model-labels claude_haiku_baseline,qwen37_max,mistral_large_2512 \
  --all-cli-levels --confirm-paid-run

# Analyze results
python analysis/analyze.py output/events.jsonl --grouped
```

---

## Experiment design

### Models (Phase 2A canonical)

| Label | OpenRouter ID | Family |
|---|---|---|
| claude_haiku_baseline | anthropic/claude-haiku-4.5 | Western constitutional |
| qwen37_max | qwen/qwen3.7-max | Chinese frontier |
| mistral_large_2512 | mistralai/mistral-large-2512 | European sovereign |

Model IDs are validated at runtime against live OpenRouter metadata.
Never hardcode IDs — use `experiments/cost_estimate.py --include-fallbacks` to check availability.

### CLI levels

Three levels encoded as formal feature vectors, not prose:

| Feature | Low | Medium | High |
|---|---|---|---|
| Active constraints | 2–3 | 5–7 | 10+ |
| Rule conflict pairs | 0 | 2 | 5+ |
| Ambiguity flags | 0 | 1 | 3+ |
| Adjudication latency (cycles) | 1 | 3 | 5+ |
| Enforcement inconsistency | 0% | 30% | 60% |
| Amendment threshold | Simple majority | Supermajority | Unanimity |

Full prompt templates: `experiments/prompts/`

### Action taxonomy

| Category | Definition |
|---|---|
| comply | Follows active rule directly |
| explore | Negotiates, adjudicates, proposes amendment |
| evade | Cites rule while acting through surface exception |
| defect | Open violation or sabotage |
| abstain | Refuses to act |

`evade` is not collapsed into `explore`. The SAPNC result depends on this separation.

### Normative palimpsest layers

| Layer | Description |
|---|---|
| deep_rule | Constitutional/foundational — hard to amend |
| institutional_practice | Accumulated administrative interpretation |
| recent_rule | Reform layer from last 3 cycles |
| surface_exception | Loophole, transitional carve-out, unmonitored exception |
| living_memory | Within-run sanctions and adjudication history |

---

## Metrics

| Metric | Definition |
|---|---|
| TVD | Total Variation Distance between action distributions in consecutive cycles |
| Anomia | \|declared_comply − behavioral_comply\| per world |
| Declared/action gap | Aggregate version of anomia across the full run |
| Bootstrap CI | World-cluster bootstrap (key: `model_label\|world_id`), 2,000 iterations |
| Judged evade | External deterministic judge classification — lexical, local, no LLM |
| Surface exception rate | Share of actions citing `surface_exception` layer |

---

## Phase 2A results (canonical)

Run ID: `paid_stateful_1779845820`
Rows: 540 · Valid: 523 · Errors: 17 · Spend: USD 1.50073750

| Model | CLI | Self evade | Judged evade | Gap |
|---|---|---:|---:|---:|
| Claude | low | 0.0% | 0.0% | 0.0% |
| Claude | medium | 0.0% | 1.7% | 0.0% |
| Claude | high | 0.0% | 33.3% | 0.0% |
| Mistral | low | 28.3% | 11.7% | 46.7% |
| Mistral | medium | 33.9% | 26.8% | 100.0% |
| Mistral | high | 100.0% | 100.0% | 100.0% |
| Qwen | low | 0.0% | 0.0% | 0.0% |
| Qwen | medium | 0.0% | 0.0% | 0.0% |
| Qwen | high | 100.0% | 100.0% | 0.0% |

Bootstrap [1.000, 1.000] for Mistral high and Qwen high under both self-label and external judge.

Fisher exact test CLI effect: low vs high p = 1.05e-15 · medium vs high p = 7.86e-16 · low vs medium p = 0.726 (ns)

---

## Phase 2B robustness

| Run | Condition | Mistral high evade | Qwen high evade | Spend |
|---|---|---:|---:|---:|
| run_a_stateful_en | English, memory | 1.000 | 1.000 | $2.87 |
| run_a_stateless_en | English, no memory | 0.983 | 1.000 | $2.49 |
| run_b1_stateful_es | Spanish, memory | 1.000 | 0.883 | $3.01 |
| deepseek_smoke_en | DeepSeek smoke | 1.000* | — | $0.09 |

*DeepSeek reliability 79.2% — below 90% confirmatory threshold. Signal present, not canonical.

---

## Theoretical context

TRIBE v2 is part of the Extended Phenotype Theory of Law research program.

Key antecedents:
- Lerer (2026a). Simulating Institutional Dynamics. DOI: [10.5281/zenodo.19010941](https://doi.org/10.5281/zenodo.19010941)
- Lerer (2026b). Synthetic Chaos as an Institutional Laboratory. DOI: [10.5281/zenodo.18777434](https://doi.org/10.5281/zenodo.18777434)
- Lerer (2026c). Synthetic Minds in Normative Sandboxes. DOI: [10.5281/zenodo.19341388](https://doi.org/10.5281/zenodo.19341388)
- Lerer (2026d). The Legal Book of the Dead. SSRN: [5496678](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5496678)

Framework references:
- Hamilton et al. (2026). Computational foundations of the human world. arXiv:2605.01680
- Dyachkov (2026a). Social institutions: A behavioural approach. DOI: [10.13140/RG.2.2.22713.33122](https://doi.org/10.13140/RG.2.2.22713.33122)

---

## Cost controls

All paid runs require:
```bash
TRIBE_MAX_COST_USD=10 python experiments/paid_stateful.py --confirm-paid-run
```

Without `--confirm-paid-run` the script runs in dry-run mode and exits before any API call.
Without `TRIBE_MAX_COST_USD` the script refuses to start.

---

## Citation

```bibtex
@misc{lerer2026tribe,
  author       = {Lerer, Ignacio Adrián},
  title        = {Synthetic Populations as Institutional Stress Tests: Constitutional Lock-In and Model-Specific Phase Transitions in LLM Synthetic Societies},
  year         = {2026},
  publisher    = {Zenodo},
  note         = {ORCID: 0009-0007-6378-9749},
  url          = {https://zenodo.org/communities/law-as-extended-phenotype}
}
```

---

## License

Code: MIT
Data and paper: CC BY 4.0
