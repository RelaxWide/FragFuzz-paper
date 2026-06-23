# FragFuzz

**FragFuzz: Exploiting FTL Fragmentation to Trigger Deep Maintenance Logic in SSD Firmware**

A greybox fuzzing framework that actively drives SSD firmware toward worst-case
fragmentation states to efficiently trigger deep maintenance logic (e.g., garbage
collection). It integrates three techniques:

- **TVDA** (Threshold-Variable Dependency Analysis) — automatically extracts the
  critical threshold variables that gate maintenance logic, via backward slicing
  on the Program Dependency Graph.
- **DRP** (Dynamic Range Partitioning) — tracks gradual variable changes while
  preserving coverage information under value drift.
- **FFM** (FTL Fragmentation Metric) — mitigates timing noise in nondeterministic
  environments by prioritizing inputs that intensify internal fragmentation.

Evaluated on **FEMU** and **MQSim**, FragFuzz reaches GC triggering with 51.9%
fewer commands and GC completion with 64.2% fewer commands than AFL++, and
improves over CSFuzz by 28.8% / 48.4%.

## Repository contents

| File | Description |
|------|-------------|
| `conference_FragFuzz.tex` | LaTeX source (IEEEtran conference format) |
| `reference.bib` | BibTeX bibliography |
| `fig1.png`, `fig2.png`, `fig3.png` | Figures (architecture, TVDA workflow, partitioning) |

## Building

```bash
pdflatex conference_FragFuzz
bibtex   conference_FragFuzz
pdflatex conference_FragFuzz
pdflatex conference_FragFuzz
```

Requires the `IEEEtran` document class and the `booktabs`, `tabularx`, `multirow`,
`adjustbox`, `enumitem`, and `algorithm`/`algorithmic` packages (all standard in
TeX Live / Overleaf).

> Note: the `.tex` references figures as `\includegraphics{fig1.png}` (no folder
> prefix), so the figure files must sit in the same directory as the `.tex`.
