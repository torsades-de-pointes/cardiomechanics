# 🫀 CardioMechanics · Pressure–Volume Loop Simulator

> **An interactive, browser-based educational simulator for left ventricular pressure–volume loop physiology.**  
> No installation. No backend. No accounts. Works in any browser.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Educational Only](https://img.shields.io/badge/Use-Educational%20Only-blue.svg)]()
[![Stages 1-5](https://img.shields.io/badge/Stages-1--5-red.svg)]()
[![Works Offline](https://img.shields.io/badge/Mobile-Works%20Offline-brightgreen.svg)]()

---

## ▶️ Launch the Simulator

| | Version | Link | Best for |
|---|---------|------|----------|
| 🖥️ | **Desktop** | **[Launch Desktop Simulator](https://torsades-de-pointes.github.io/cardiomechanics/index.html)** | Laptop / desktop — full features, animated loop, 6 themes |
| 📱 | **Mobile / Offline** | **[Launch Mobile Simulator](https://torsades-de-pointes.github.io/cardiomechanics/mobile.html)** | Phone, tablet, or anywhere without internet |

📄 [Fellows Learning Guide (PDF)](https://torsades-de-pointes.github.io/cardiomechanics/CardioMechanics_Fellows_Guide.pdf) &nbsp;·&nbsp; 🔧 [Technical Reference (PDF)](https://torsades-de-pointes.github.io/cardiomechanics/CardioMechanics_Technical_Reference.pdf)

---

## What Is This?

CardioMechanics is a single-file HTML simulator that models left ventricular haemodynamics using the **time-varying elastance model** (Sagawa 1981). It is designed for **cardiology fellows, residents, medical students, and educators** to build mechanistic, intuitive understanding of PV loop physiology.

Inspired by and built on [Nick Mark MD's open-source PV loop simulator](https://nickmmark.github.io/pressure-volume-loops/) (MIT license).

> ⚠️ **Not a clinical tool.** Must never be used for patient care or clinical decision-making.

---

## The Five Learning Stages

| Stage | Topic | Key Concepts |
|-------|-------|--------------|
| **1** | Normal LV Physiology | ESPVR, EDPVR, Ea, Frank-Starling, preload, afterload, inotropy, PVA |
| **2** | Heart Failure | HFrEF vs HFpEF — two completely different PV loop problems |
| **3** | Valvular Disease | AS, AR, Mitral Stenosis, MR — each lesion breaks a different phase |
| **4** | Mechanical Circulatory Support | IABP, Impella (P1–P9), VA-ECMO — and why ECMO can worsen LV |
| **5** | Interventions | Pre/Post TAVR, MVR, CRT-P — the loop before and after treatment |

---

## Quick Start

### 🌐 Online (easiest — works on any device)
Click the Launch links above. No download needed.

### 📱 Use Offline on Your Phone (no internet needed after first load)
1. Open the **[Mobile Simulator](https://torsades-de-pointes.github.io/cardiomechanics/mobile.html)** in your phone's browser
2. **iPhone/iPad (Safari):** Tap the Share button → "Add to Home Screen" → it becomes an app icon  
3. **Android (Chrome):** Tap ⋮ → "Add to Home Screen" or "Install app"  
4. Once added, it works **completely offline** — no internet needed

### 💾 Download and Use Locally (no internet at all)
1. Click **Code → Download ZIP** above
2. Unzip the folder
3. Open `mobile.html` in any browser — works from your Downloads folder with no internet
4. `index.html` is the full desktop version (needs internet for D3.js library)

---

## How to Cite

```
CardioMechanics PV Loop Simulator (2025). An interactive browser-based educational 
tool for left ventricular pressure–volume loop physiology. 
Available at: https://torsades-de-pointes.github.io/cardiomechanics/
Physics engine adapted from: Mark N (2024). pressure-volume-loops. 
GitHub: github.com/nickmmark/pressure-volume-loops (MIT License).
```

**BibTeX:**
```bibtex
@software{cardiomechanics2025,
  title  = {CardioMechanics PV Loop Simulator},
  author = {Parcha, Vibhu},
  year   = {2025},
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

### Physics Engine — Nick Mark MD (MIT)
The core physics engine is adapted from Nick Mark's open-source simulator:

> **Mark N** (2024). *pressure-volume-loops*. GitHub: [github.com/nickmmark/pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops). MIT License.

**Modifications from original:**
- Elastance shape factor: n=8 → n=3 (prevents unrealistic LVP spikes)
- Aortic valve conductance: kAv=18 → kAv=28
- Windkessel resistance: Rr=1.2 → Rr=0.8
- ESPVR back-calculated through actual end-systolic point
- PVA potential energy geometry corrected
- Extended with Stages 2–5, 6 UI themes, mobile Canvas renderer, EDPVR sliders

### Physics References
- Sagawa K (1981). *Circ Research* — time-varying elastance model
- Suga H et al (1981). *Am J Physiology* 240(1):H39–H44 — PVA & MVO₂
- Sunagawa K et al (1983). *Am J Physiology* 245(5):H773 — Arterial Elastance  
- Kelly RP et al (1992). *Circulation* 86(2):513 — ESP approximation

---

## ⚠️ Disclaimer

CardioMechanics is **for educational purposes only.**

- ❌ Do NOT use for clinical decision-making
- ❌ Do NOT use for patient management or diagnosis
- ✅ DO use for teaching, self-study, and presentations
- ✅ DO use to build mechanistic intuition for cardiovascular physiology

---

## Feedback & Contact

Questions, errors, suggestions? I'd love to hear from you.

- **Email:** [vibhuparcha@gmail.com](mailto:vibhuparcha@gmail.com)
- **GitHub Issues:** [Open an issue](https://github.com/torsades-de-pointes/cardiomechanics/issues)
- **GitHub Discussions:** [Start a discussion](https://github.com/torsades-de-pointes/cardiomechanics/discussions)

If you find CardioMechanics useful in your teaching or training, a GitHub ⭐ is always appreciated and helps others discover it!

---

## Acknowledgements

| Person | Contribution |
|--------|-------------|
| **Nick Mark MD** | Original [pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops) simulator (MIT). Foundation for this project. |
| **Richard E. Klabunde PhD** | [cvphysiology.com](https://cvphysiology.com) — definitive free cardiovascular physiology resource |
| **Alex Yartsev** | [derangedphysiology.com](https://derangedphysiology.com) — precise, referenced PV loop explanations |
| **Hiroyuki Suga & Kiichi Sagawa** | 1970s–80s experimental work establishing the elastance model |

---

## Changelog

| Version | Changes |
|---------|---------|
| 1.5 | 6 UI themes, mobile Canvas offline version, EDPVR/ESPVR sliders, physics corrections, GitHub Pages |
| 1.4 | Stage 5: Interventions (TAVR, MVR, CRT-P) |
| 1.3 | Stage 4: MCS (IABP, Impella, VA-ECMO) |
| 1.2 | Stage 3: Valvular disease (AS, AR, MS, MR) |
| 1.1 | Stage 2: HFrEF, HFpEF |
| 1.0 | Stage 1: Normal physiology |

---

*[torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/) · Educational use only · MIT License · 2025*
