# CG-LLM

Research code and synthetic benchmark for **CG-LLM: A large language model decision-support framework for low-altitude airspace authorization**.

The framework combines natural-language fact extraction, a human-ratified constraint catalog, deterministic geometry and policy checks, verified time/altitude modification search, and evidence-linked explanations.

## Contents

Download and extract `CG-LLM-reproducibility.zip`. The archive contains source code, experiment configurations, unit tests, synthetic benchmarks, rule catalogs, geographic study data, regulatory text inputs, and selected recorded experimental outputs. `MANIFEST.json` lists SHA-256 checksums for all archived files. Manuscript drafts, downloaded research PDFs, credentials and local databases are excluded.

## Setup

Use Python 3.12. From the extracted CG-LLM directory:

```sh
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q tests/v2
```

For live model calls, copy `.env.example` to `.env` and set your own provider API key. API calls may incur charges. Existing recorded outputs can be analyzed without rerunning model calls.

## Experiments

```sh
python -m experiments.analyze main ablation robustness language temperature
python -m experiments.run experiments/configs/main.yaml
```

The base benchmark contains 780 cases (624 test and 156 development). The main model is GLM-5.3-Flash. Main configurations request hybrid retrieval, with BM25 fallback when optional dense-retrieval dependencies are absent. Check recorded run metadata when comparing results. Provider-specific `thinking: false` configuration may map to `reasoning_effort: low`; these settings should not be treated as interchangeable across APIs.

Reported main-run accuracy is 92.5% and unsafe permissive rate is 1.0%. Paraphrase accuracy is 92.5%, compared with 50.1% for regular-expression extraction linked to the same engine. Reference labels are generated from the study rule catalog. The scenarios are synthetic and the software is a research implementation.

## Data provenance and rights

Regulatory text files are research inputs, including prepared English text; consult official sources for authoritative wording. Study thresholds and policies are recorded in `data/constraints/constraints.yaml`. No additional reuse license has yet been selected by the authors; public availability alone does not grant an open-source license. Third-party materials retain their applicable rights.

## Authors

Tianhao Mu, Xianke Yin, Yonghai Liu, Feilong Ye, Feng Chen, and Tao Ma.

Correspondence: Tao Ma, matao@seu.edu.cn.
