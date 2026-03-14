# 🫀 CardioMechanics · Pressure–Volume Loop Simulator

> **An interactive, browser-based educational simulator for left ventricular pressure–volume loop physiology.**  
> Works entirely offline. No installation. No backend. No accounts. Download one file and open it.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Educational](https://img.shields.io/badge/Use-Educational%20Only-blue.svg)]()
[![Stages: 1–5](https://img.shields.io/badge/Stages-1--5-crimson.svg)]()
[![Offline Ready](https://img.shields.io/badge/Works-Offline-success.svg)]()

**[▶ Launch Desktop Version](https://[your-username].github.io/cardiomechanics/)** &nbsp;|&nbsp; **[📱 Launch Mobile Version](https://[your-username].github.io/cardiomechanics/mobile.html)** &nbsp;|&nbsp; **[📄 Fellows Guide (PDF)](docs/CardioMechanics_Fellows_Guide.pdf)** &nbsp;|&nbsp; **[🔧 Technical Reference (PDF)](docs/CardioMechanics_Technical_Reference.pdf)**

---

## What Is This?

CardioMechanics is a single-file HTML simulator that models left ventricular haemodynamics using the **time-varying elastance model** (Sagawa 1981). It is designed for **cardiology fellows, residents, medical students, and educators** to build mechanistic understanding of PV loop physiology.

It is **not** a clinical tool. It must **never** be used for patient care or clinical decision-making.

---

## The Five Learning Stages

| Stage | Topic | Key Pathologies |
|-------|-------|-----------------|
| **1** | Normal LV Physiology | ESPVR, EDPVR, Ea, Frank-Starling, inotropy, afterload |
| **2** | Heart Failure | HFrEF (systolic), HFpEF (diastolic), EDPVR stiffness |
| **3** | Valvular Disease | AS, AR (AI), Mitral Stenosis, Mitral Regurgitation |
| **4** | Mechanical Circulatory Support | IABP, Impella (P1–P9), VA-ECMO, ECPELLA |
| **5** | Interventions | Pre/Post TAVR, MVR, CRT-P — before and after |

---

## Files in This Repository

```
cardiomechanics/
├── index.html                              ← Desktop simulator (open this)
├── mobile.html                             ← Mobile simulator (offline, Canvas2D)
├── docs/
│   ├── CardioMechanics_Fellows_Guide.pdf   ← Feynman learning roadmap (5 stages)
│   ├── CardioMechanics_Fellows_Guide.docx  ← Word version (editable)
│   ├── CardioMechanics_Technical_Reference.pdf   ← Physics, architecture, refs
│   └── CardioMechanics_Technical_Reference.docx  ← Word version (editable)
├── LICENSE                                 ← MIT License
└── README.md                               ← This file
```

---

## Quick Start

### Online (GitHub Pages)
Click the **Launch** links above. No installation needed.

### Offline
1. Click **Code → Download ZIP** on this page
2. Unzip the folder
3. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)
4. Works completely offline (fonts load from Google Fonts on first use; all physics runs locally)

### Mobile
Open `mobile.html` on any smartphone or tablet. Uses Canvas2D — no external dependencies beyond Google Fonts.

---

## How to Cite

If you use CardioMechanics in teaching, presentations, posters, or publications, please cite:

> **CardioMechanics PV Loop Simulator** (2025). An interactive browser-based educational tool for left ventricular pressure–volume loop physiology. Available at: `https://[your-username].github.io/cardiomechanics/`. Physics engine adapted from: Mark N (2024). *pressure-volume-loops*. GitHub: github.com/nickmmark/pressure-volume-loops (MIT License).

**BibTeX:**
```bibtex
@software{cardiomechanics2025,
  title   = {CardioMechanics PV Loop Simulator},
  year    = {2025},
  url     = {https://[your-username].github.io/cardiomechanics/},
  note    = {Interactive educational tool for cardiology fellows.
             Physics engine adapted from Mark N (2024)
             pressure-volume-loops (MIT License).
             Stages 1–5: normal physiology, HF, valvular disease, MCS, interventions.}
}
```

---

## ⚖️ Attribution & License

### This Project
CardioMechanics is released under the **MIT License**. See [LICENSE](LICENSE).

### Physics Engine — Nick Mark MD (MIT)
The core physics engine is **adapted from** Nick Mark's open-source simulator:

> **Mark N** (2024). *pressure-volume-loops*. GitHub: [github.com/nickmmark/pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops). MIT License.

The MIT License permits use, modification, and redistribution provided the **original copyright notice is preserved**. We comply fully:

- The original MIT license and copyright notice are reproduced in full in [LICENSE](LICENSE)
- All physics engine modifications are clearly documented in the [Technical Reference](docs/CardioMechanics_Technical_Reference.pdf)
- Nick Mark is prominently credited in the simulator footer, all documentation, and in every distributed file

**Modifications made to the original engine:**
- Elastance shape factor changed from n=8 to n=3 (prevents unrealistic LVP spikes above AoP)  
- Aortic valve conductance increased from kAv=18 to kAv=28 (realistic LVP–AoP equalisation)  
- Windkessel runoff resistance reduced from Rr=1.2 to Rr=0.8 (Ao pressure tracks ejection better)  
- ESPVR back-calculated through actual end-systolic point (V₀_eff = ESV − ESP/Ees)  
- PVA potential energy geometry corrected (triangular approximation replaced with correct integration)  
- Extended with valvular pathologies, Stage 5 interventions, 6 UI themes, mobile Canvas renderer  

### Educational Content (Original)
All teaching notes, clinical annotations, stage banners, the Fellows Guide, and the Technical Reference are original content, released under MIT.

### Physics References
The simulator implements models from:
- Sagawa K (1981). *Circulation Research* — time-varying elastance model
- Suga H et al (1981). *Am J Physiology* — PVA and myocardial O₂ consumption  
- Sunagawa K et al (1983). *Am J Physiology* — effective arterial elastance  
- Kelly RP et al (1992). *Circulation* — ESP approximation

### Educational Resources
- Klabunde RE. *cvphysiology.com* — used as educational reference
- Yartsev A. *derangedphysiology.com* — used as educational reference
- Bastos MB et al (2020). *European Heart Journal* 41(12):1286–1297

---

## ⚠️ Disclaimer

**CardioMechanics is for educational purposes only.**

- ❌ Do NOT use for clinical decision-making
- ❌ Do NOT use for patient management or diagnosis  
- ❌ Do NOT use as a substitute for clinical judgment
- ✅ DO use for teaching, self-study, presentations, and research education
- ✅ DO use to build mechanistic intuition for cardiovascular physiology

All physiological values are simplified model approximations. The simulator does not model: right heart function, RV-LV interdependence, heart rate variability, or the full complexity of vascular impedance.

---

## Feedback & Contributions

We actively welcome feedback from fellows, educators, and clinicians.

- **Found a physiological error?** → [Open an Issue](../../issues)
- **Want to suggest a new pathology preset?** → [Open an Issue](../../issues)
- **Teaching scenario to contribute?** → [Open a Discussion](../../discussions)
- **Want to adapt for your institution?** → Permitted under MIT License; please keep attribution

If you use CardioMechanics in a course or curriculum and find it helpful, we'd love to hear from you. A brief note in Issues is much appreciated.

---

## Acknowledgements

| Person | Contribution |
|--------|-------------|
| **Nick Mark MD** | Original pressure-volume-loops simulator (MIT). Physics engine foundation. |
| **Richard E. Klabunde PhD** | cvphysiology.com — the definitive free cardiovascular physiology educational resource |
| **Alex Yartsev** | derangedphysiology.com — precise, referenced PV loop explanations |
| **Hiroyuki Suga & Kiichi Sagawa** | 1970s–80s experimental work establishing the elastance model |

---

## Changelog

| Version | Changes |
|---------|---------|
| 1.0 | Stage 1: Normal physiology |
| 1.1 | Stage 2: HFrEF, HFpEF |
| 1.2 | Stage 3: Valvular disease (AS, AR, MS, MR) |
| 1.3 | Stage 4: MCS (IABP, Impella, VA-ECMO) |
| 1.4 | Stage 5: Interventions (TAVR, MVR, CRT-P) |
| 1.5 | 6 UI themes, mobile Canvas version, EDPVR/ESPVR sliders, physics corrections, full documentation |

---

*CardioMechanics · Educational use only · MIT License · 2025*
