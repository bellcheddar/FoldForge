# ⚙️ ForgeFold

> **A single-file browser GUI for the whole Boltz-2 workflow: build, run, review.**

![type](https://img.shields.io/badge/type-single--file%20HTML-E34F26?logo=html5&logoColor=white) ![engine](https://img.shields.io/badge/engine-Boltz--2-467FF7) ![build step](https://img.shields.io/badge/build%20step-none-00897B) ![runs](https://img.shields.io/badge/runs-in%20browser-9b51e0) ![author](https://img.shields.io/badge/author-Marc%20C.%20Deller%2C%20D.Phil.-1C244B)

<table>
<tr>
<td>🌐 <b>Website</b></td><td><a href="https://marcdeller.com" target="_blank" rel="noopener noreferrer">marcdeller.com</a></td>
<td>✉️ <b>Contact</b></td><td><a href="mailto:marc@marcdeller.com">marc@marcdeller.com</a></td>
<td>🐙 <b>GitHub</b></td><td><a href="https://github.com/bellcheddar/FoldForge" target="_blank" rel="noopener noreferrer">bellcheddar/FoldForge</a></td>
</tr>
</table>

---

ForgeFold is a browser-based interface for preparing, running, and reviewing Boltz-2 structure-prediction jobs. It brings Boltz setup, YAML construction, job-script generation, and result inspection into a single lightweight HTML application. 

Why it matters: the Boltz-2 workflow normally means hopping between a text editor for YAML, a shell for the run script, and a spreadsheet for the results, with plenty of room for format mistakes along the way. ForgeFold pulls all four stages (set the binary path, build the input YAML from sequences and SMILES, generate the run script, and review confidence and affinity metrics) into one lightweight HTML application that opens in any browser with no build step. It is useful for structure-guided teams who want to lower the friction of repeated co-folding runs and give less command-line-comfortable colleagues a clean, guided path from input preparation to result triage.

## Overview

The application is organized around a simple four-step workflow: set the local Boltz-2 binary path, build an input YAML from protein and ligand definitions, configure a run script, and review output metrics from analyzed results. 

This design is meant to reduce friction for structure-guided workflows where users repeatedly move between FASTA/SMILES input preparation, command-line execution, and affinity-oriented output review. 

## Core workflow

1. **Setup installation** — store the path to the local Boltz-2 executable so it can be reused across sessions. 
2. **Build YAML input** — enter protein FASTA sequences and ligand SMILES, then export an `input.yaml` file for Boltz-compatible predictions. 
3. **Configure and write jobs** — choose run parameters and generate a `run_boltz.zsh` shell script for local execution. 
4. **Analyse results** — load processed outputs such as `boltz_summary.csv` to inspect confidence and affinity-related metrics. 

## Features

- Browser-based GUI for Boltz-2 workflow management. 
- YAML builder for protein and ligand input definition. 
- Job-script generation for local prediction runs. 
- Results view for summary CSV uploads and prediction review. 
- Support for metrics including `confidence_score`, `affinity_pred_value1`, and derived `pIC50` display. 

## Input model

ForgeFold is built around Boltz-style YAML inputs that define one or more protein chains and optional ligands. The example interface content shows protein entries with `id` and `sequence`, ligand entries with `id` and `smiles`, plus optional constraint and property blocks for pocket and affinity settings. 

A typical workflow is to paste receptor and partner sequences, add a ligand SMILES string, and export the resulting YAML before launching prediction jobs locally. 

## Results interpretation

The interface is designed to surface key prediction outputs after external analysis. The bundled UI text highlights `confidence_score` as an overall model-confidence measure, `affinity_pred_value1` as an affinity-related score, `affinity_probability_binary1` as a binder-likelihood output, and `pIC50` as a derived potency-style estimate. 

These values are intended for rapid triage and comparison of modeled complexes rather than as a substitute for experimental validation. 

## Running ForgeFold

Because ForgeFold is delivered as a standalone HTML application, the simplest way to use it is to open the file in a modern browser and interact with the GUI directly. 

Typical usage:

```bash
# Example: open the app locally
open ForgeFold.html
```

Or host it with any lightweight static server:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a browser.

## Expected companion tools

ForgeFold is designed to sit alongside a local Boltz-2 installation and a downstream analysis script such as `analyze_boltz.py`, which generates CSV outputs for the Results tab. 

To make the full workflow work smoothly, keep the following available:

- A working local `boltz` executable. 
- Input biomolecular sequences and ligand SMILES strings. 
- A results-processing script that emits `boltz_summary.csv` or compatible output. 

## Suggested repository structure

```text
ForgeFold/
├── README.md
├── ForgeFold.html
├── analyze_boltz.py
├── examples/
│   └── input.yaml
└── outputs/
```

## Roadmap ideas

Potential future improvements suggested by the current UI structure include more robust YAML validation, richer job templating, tighter integration with local output directories, and more detailed downstream result visualizations. 

## License

Add the project license here.

## Source context

This README was drafted from the attached ForgeFold application content and interface text.

---

## 👤 Author

**Marc C. Deller, D.Phil.**  
Structural biologist & drug discovery scientist  

<table>
<tr>
<td>🌐</td><td><a href="https://marcdeller.com" target="_blank" rel="noopener noreferrer">marcdeller.com</a></td>
<td>✉️</td><td><a href="mailto:marc@marcdeller.com">marc@marcdeller.com</a></td>
<td>🐙</td><td><a href="https://github.com/bellcheddar/FoldForge" target="_blank" rel="noopener noreferrer">github.com/bellcheddar/FoldForge</a></td>
</tr>
</table>
