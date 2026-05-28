# yongle-mural-annotation-tools

Browser-based research tools for the **Yongle Palace Taoist mural** patch-annotation project (companion to the *Scientific Data* Data Descriptor and its public dataset, Zenodo DOI [10.5281/zenodo.19718760](https://doi.org/10.5281/zenodo.19718760)).

Two self-contained single-file HTML tools (no build step; open in a modern browser):

| Tool | File | What it does |
|---|---|---|
| **IAA Reproducibility Toolkit** | `src/yongle-iaa-toolkit-v2.9.60.html` | Inter-annotator agreement for human + machine annotation: Cohen's / Fleiss' κ and Krippendorff's α with bootstrap 95% CIs, CI-based acceptance gates, sensitivity analysis, a self-contained reproducibility bundle, and swappable domain profiles. Deterministic (fixed demo fixture: κ = 0.768971, α = 0.769219). |
| **Annotation Workflow** | `src/yongle-workflow-v2.9.60.html` | Front-end for the multi-step patch-annotation pipeline (image → 512×512 patches → multi-engine VLM candidate labels → rule-based consensus → review/export). Intended as a local research console. |

## Quick start

Both files are standalone. The IAA Toolkit runs fully client-side — just open it in a browser. The Workflow tool additionally expects a local helper server and your own model-API credentials (see **Setup & Security** below).

This repository is intentionally not enabled as a hosted web app. Use the tools locally so API keys, local helper endpoints, and dataset paths remain under your control.

## Setup & Security (read before use)

This is a *bring-your-own-key, run-it-locally* research console. Please note:

- **API keys.** The Workflow tool has input fields for model API keys. Keys you enter are stored **only in your own browser's `localStorage`** (e.g. `gemini_api_key`); they are never bundled in this repository (shipped defaults are empty). Treat `localStorage` as plaintext: **do not enter keys on a shared/public machine, and clear them when done.** No key is required to use the IAA Toolkit.
- **Local server / `localhost`.** The Workflow tool references `localhost` / `127.0.0.1` for a local helper server and local file access. It is designed to run on your own machine, not as a hosted web app.
- **Model endpoints.** GPT-4o, Gemini, and Claude were accessed in the original study via the OpenAI-compatible **`api.gptsapi.net`** proxy; Qwen via Alibaba **DashScope**. These endpoints appear as defaults and can be changed in the tool.
- **Data paths.** Storage/base-path fields default to the placeholder `/path/to/your/dataset` — set them to your own location.

## Relation to the dataset and papers

- The released dataset (patches, per-engine labels, consensus, agreement statistics) is on Zenodo: [10.5281/zenodo.19718760](https://doi.org/10.5281/zenodo.19718760) (CC BY 4.0).
- The IAA Toolkit reproduces the agreement metrics reported in the associated manuscripts.
- These GUI tools are **not** part of the Data Descriptor's minimal reproduction code package; that pipeline code is released separately.

## Versioning

This is the **first public release** of the tools repository. The bundled tools are at internal build **2.9.60**; earlier internal iterations are not published here.

## License

[MIT](LICENSE) © 2026 Bingbing Liang.

## Citation

See [`CITATION.cff`](CITATION.cff). A tagged release will be archived to Zenodo to mint a software DOI; update the citation file with the real repository URL and DOI after publishing.
