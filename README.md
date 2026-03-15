# 🫀 CardioMechanics · Pressure-Volume Loop Simulator

> **An interactive, browser-based educational simulator for left ventricular pressure–volume loop physiology.**  
> No installation. No backend. No accounts. Works in any browser.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Educational Only](https://img.shields.io/badge/Use-Educational%20Only-blue.svg)]()
[![Stages 1-5](https://img.shields.io/badge/Stages-1--5-red.svg)]()
[![Mobile Works Offline](https://img.shields.io/badge/Mobile-Works%20Offline-brightgreen.svg)]()

---

## ▶️ Launch the Simulator

| Version | Link | Best for |
|---------|------|----------|
| 🖥️ **Desktop** | **[Launch Desktop Simulator](https://torsades-de-pointes.github.io/cardiomechanics/index.html)** | Laptop / desktop - animated loop, 6 themes, full sidebar |
| 📱 **Mobile / Offline** | **[Launch Mobile Simulator](https://torsades-de-pointes.github.io/cardiomechanics/mobile.html)** | Phone, tablet, or anywhere without internet |

📄 [Fellow's Learning Guide](FELLOWS_GUIDE.md) · 🔧 [Technical Reference](TECHNICAL_REFERENCE.md)

---

## What Is This?

CardioMechanics is a single-file HTML simulator that models left ventricular haemodynamics using the **time-varying elastance model** (Sagawa 1981). Designed for **cardiology fellows, residents, medical students, and educators** to build mechanistic, intuitive understanding of PV loop physiology.

Inspired by and built on [Nick Mark MD's open-source PV loop simulator](https://nickmmark.github.io/pressure-volume-loops/) (MIT license).

> *Not a clinical tool* Must never be used for patient care or clinical decision-making.

---

## The Five Learning Stages

| Stage | Topic | Key Concepts |
|-------|-------|--------------|
| **1** | Normal LV Physiology | ESPVR, EDPVR, Ea, Frank-Starling, preload, afterload, inotropy, PVA |
| **2** | Heart Failure | HFrEF vs HFpEF - two completely different PV loop problems |
| **3** | Valvular Disease | AS, AR, Mitral Stenosis, MR - each lesion breaks a different phase |
| **4** | Mechanical Circulatory Support | IABP, Impella (P1–P9), VA-ECMO - and why ECMO can worsen the LV |
| **5** | Interventions | Pre/Post TAVR, MVR, CRT-P - the loop before and after |

---

## Quick Start - How to Use the Simulator

### 1. Choose a Pathology
Use the **Physiology / Pathology** dropdown to select any of 13 presets across Stages 1–5. The loop, metrics, and teaching note update instantly.

Or use the **Quick Preset** buttons at the bottom of the sidebar to jump between states.

### 2. Adjust the Sliders
| Slider | What it changes | What to watch |
|--------|----------------|---------------|
| **Contractility (Ees)** | Slope of ESPVR | Loop height and width; EF |
| **Preload (EDV)** | Starting volume | Loop width; SV via Frank-Starling |
| **Afterload (MAP)** | Arterial pressure | Loop height; ESV; SV |
| **Unstressed Vol (V₀)** | ESPVR x-intercept | Position of ESPVR |
| **EDPVR Scale** | Vertical stiffness | Steepness of passive filling curve |
| **EDPVR Slope** | Exponential rate | Shape of EDPVR at high volumes |

### 3. Animate the Loop (Desktop only)
Click **Animate Loop** to watch the cardiac cycle in real time. Use the speed controls:
- **Very slow** - ideal for teaching, shows each phase clearly
- **Normal / Fast** - for exploring how the loop changes dynamically

The coloured dot traces four phases: 🟢 Filling → 🔵 Isovol. Contraction → 🔴 Ejection → 🟣 Isovol. Relaxation

### 4. Add a Stage 4 MCS Device
Use the **Stage 4 · MCS Device** dropdown:
- **IABP** - observe modest leftward shift
- **Impella** - increase P-level; watch loop triangularise → teardrop shape
- **VA-ECMO** - increase RPM; watch loop shift **right** (paradoxical LV worsening)

A ghost loop (dashed) shows the unsupported reference state for direct comparison.

### 5. Toggle Overlays
| Toggle | Shows |
|--------|-------|
| **ESPVR** | Contractility ceiling (green dashed) |
| **EDPVR** | Passive filling curve (gold dashed) |
| **Ea** | Arterial elastance - vascular load (blue dashed) |
| **PE shading** | Potential energy region (≈ MVO₂ indicator) |
| **Ao SBP/DBP** | Aortic systolic and diastolic pressure lines |
| **Peak LVP** | Peak left ventricular pressure line |
| **Valve labels** | Points ①②③④ with event labels |
| **Ghost loop** | Unsupported reference state (MCS comparison) |

### 6. Read the Metrics
| Metric | Meaning |
|--------|---------|
| **Stroke Vol** | EDV - ESV (mL) |
| **EF** | Ejection fraction (%) |
| **Total CO** | Cardiac output including device flow (L/min) |
| **Ao SBP/DBP** | Aortic systolic / diastolic pressure (mmHg) |
| **Stroke Work** | Loop area = mechanical work per beat (mmHg·L) |
| **Ea** | ESP ÷ SV - arterial load index (mmHg/mL) |
| **PVA** | Pressure-volume area ≈ myocardial O₂ consumption |
| **Efficiency** | SW ÷ PVA × 100% - mechanical efficiency (%) |

### 7. Use Offline on Your Phone
1. Open the **[Mobile Simulator](https://torsades-de-pointes.github.io/cardiomechanics/mobile.html)** in your phone's browser
2. **iPhone/iPad (Safari):** Tap Share → **"Add to Home Screen"** → it becomes a permanent app icon
3. **Android (Chrome):** Tap ⋮ → **"Add to Home Screen"** or **"Install app"**
4. Once added, it works **completely offline** - no internet needed

---

## Documentation

| Document | Format | Description |
|----------|--------|-------------|
| [Fellow's Learning Guide](FELLOWS_GUIDE.md) | Markdown | Feynman 5-stage learning roadmap with experiments, mastery checks, and clinical challenges |
| [Technical Reference](TECHNICAL_REFERENCE.md) | Markdown | Physics engine, equations, architecture, limitations, 18 references |

---

## How to Cite

```
CardioMechanics PV Loop Simulator (2026). An interactive browser-based educational 
tool for left ventricular pressure–volume loop physiology. 
Available at: https://torsades-de-pointes.github.io/cardiomechanics/
Physics engine adapted from: Mark N (2024). pressure-volume-loops. 
GitHub: github.com/nickmmark/pressure-volume-loops (MIT License).
```

**BibTeX:**
```bibtex
@software{cardiomechanics2026,
  title  = {CardioMechanics PV Loop Simulator},
  author = {Parcha, Vibhu},
  year   = {2026},
  url    = {https://torsades-de-pointes.github.io/cardiomechanics/},
  note   = {Physics engine adapted from Mark N (2024)
            pressure-volume-loops (MIT License).
            Stages 1-5: normal physiology, HF, valvular
            disease, MCS, interventions.}
}
```

---

## Attribution & License

### This Project
Released under the **MIT License**. See [LICENSE](LICENSE).

### Physics Engine - Nick Mark MD (MIT)
The core physics engine is adapted from Nick Mark's open-source simulator:

> **Mark N** (2024). *pressure-volume-loops*. GitHub: [github.com/nickmmark/pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops). MIT License.

**Modifications from original:**
- Elastance shape factor: n=8 → n=3 (prevents unrealistic LVP spikes above aortic pressure)
- Aortic valve conductance: kAv=18 → kAv=28 (physiological LVP–AoP equalisation)
- Windkessel resistance: Rr=1.2 → Rr=0.8
- ESPVR back-calculated through actual end-systolic point
- PVA potential energy geometry corrected (exact integration, not triangular)
- Extended with Stages 2–5, 6 UI themes, mobile Canvas2D renderer, EDPVR sliders

See [TECHNICAL_REFERENCE.md](TECHNICAL_REFERENCE.md) for full physics documentation.

---

## ⚠️ Disclaimer

CardioMechanics is **for educational purposes only.**

-  Do NOT use for clinical decision-making
-  Do NOT use for patient management or diagnosis
-  DO use for teaching, self-study, and presentations
-  DO use to build mechanistic intuition for cardiovascular physiology

---

## Feedback & Contact

Questions, physiological errors, suggestions for new pathologies?
- **Email:** [vibhuparcha@gmail.com](mailto:vibhuparcha@gmail.com)
- **GitHub Issues:** [Open an issue](https://github.com/torsades-de-pointes/cardiomechanics/issues)
- **GitHub Discussions:** [Start a discussion](https://github.com/torsades-de-pointes/cardiomechanics/discussions)

If you use CardioMechanics in teaching or training, a GitHub ⭐ helps others find it. Please also cite when appropriate. 

---

## Acknowledgements

| Person | Contribution |
|--------|-------------|
| **Nick Mark MD** | Original [pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops) (MIT). Physics engine foundation. |
| **Richard E. Klabunde PhD** | [cvphysiology.com](https://cvphysiology.com) - definitive free cardiovascular physiology resource |
| **Alex Yartsev** | [derangedphysiology.com](https://derangedphysiology.com) - precise, referenced PV loop explanations |
| **Hiroyuki Suga & Kiichi Sagawa** | 1970s–80s experimental work establishing the elastance model |

---

## Changelog

| Version | Changes |
|---------|---------|
| 1.5 | 6 UI themes, mobile Canvas2D offline version, EDPVR/ESPVR sliders, physics corrections, GitHub Pages deployment |
| 1.4 | Stage 5: Interventions (TAVR, MVR, CRT-P) |
| 1.3 | Stage 4: MCS (IABP, Impella, VA-ECMO) |
| 1.2 | Stage 3: Valvular disease (AS, AR, MS, MR) |
| 1.1 | Stage 2: HFrEF, HFpEF |
| 1.0 | Stage 1: Normal physiology |

---

*[torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/) · Educational use only · MIT License · 2026*
