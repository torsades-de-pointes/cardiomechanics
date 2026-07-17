# 🫀 CardioMechanics 2.0 · Pressure-Volume Loop Simulator

**An interactive, browser-based educational simulator for left ventricular pressure-volume loop physiology.**
No installation. Works in any browser, on any device, offline.

![License: MIT](https://img.shields.io/badge/License-MIT-a8465c) ![Educational Only](https://img.shields.io/badge/Use-Educational%20only-5f5449) ![Conditions](https://img.shields.io/badge/Conditions-24-2f7a5c) ![FOAMed](https://img.shields.io/badge/FOAMed-Free%20for%20all-a9761b) ![Works offline](https://img.shields.io/badge/Works-Offline-41608f)

### ▶ [Launch the Simulator](https://torsades-de-pointes.github.io/cardiomechanics/)

Version 2.0 is a single responsive build. The separate desktop and mobile pages are gone. The same file now adapts to phone, tablet and desktop, and still runs with no internet.

| Where to go | What it gives you |
|---|---|
| **Learn** tab, in the app | An 8 chapter handbook that starts from first principles |
| **Library** tab, in the app | 24 calibrated conditions, each one card, each opening live in the simulator |
| **Reference** tab, in the app | The equations, the calibration, the model limits and the citations |
| [FELLOWS_GUIDE.md](FELLOWS_GUIDE.md) | The fellow's roadmap, with experiments and mastery checks |
| [TECHNICAL_REFERENCE.md](TECHNICAL_REFERENCE.md) | Physics engine, equations, architecture, references |

---

## What Is This?

CardioMechanics is a single-file HTML simulator that models left ventricular haemodynamics with the **time-varying elastance** model (Suga and Sagawa), a **two-element Windkessel** arterial load, and **pressure-driven valve conductances**. It is written for cardiology fellows, residents, medical students and educators who want mechanistic, intuitive understanding of the PV loop.

Every loop on the screen is solved live from the physics. Nothing is a stored picture.

Inspired by and built on Nick Mark MD's open-source PV loop simulator (MIT license).

> **Not a clinical tool.** It must never be used for patient care or clinical decision-making.

---

## What Is New in 2.0

**Four tabs instead of one screen.** Simulator, Learn, Library and Reference.

**The dotted reference loop.** Any loop can be compared against a dotted reference drawn on the same axes. The default is **Automatic**, which picks the comparison that makes the teaching point:

| What you are viewing | Dotted reference shown |
|---|---|
| Normal physiology | None. There is nothing to compare |
| Any pathology | The normal heart |
| Any condition plus a device | The same heart without the device |
| Post-TAVR, Post-MVR, Post-CRT | The matching pre-treatment loop |

You can also pick the reference by hand, or **pin** any loop and then move the sliders to watch the live loop separate from the frozen one. That is the fastest way to see what a single lever actually does.

**24 conditions, up from 13.** Now including exercise, hypovolaemia, inotropes, vasoconstriction, vasodilatation, restrictive cardiomyopathy, HCM, hypertensive heart disease, and both the acute and the chronic forms of AR and MR.

**A fourth device, ECPELLA** (VA-ECMO plus an Impella to vent the LV), alongside IABP, Impella P1 to P9 and VA-ECMO.

**An 8 chapter handbook inside the page.** Every teaching step has a button that loads the exact scenario into the simulator. Progress is tracked.

**Live time tracings.** Pressure against time and volume against time sit beside the loop and sweep with the animation.

**Two themes.** *Champagne* for day and *Monitor* for night.

**Recalibrated physics.** See below.

---

## Learning Path

The five stages from version 1.x are still the backbone. They now map onto the Library groups and the Learn chapters.

| Stage | Topic | Key concepts |
|---|---|---|
| 1 | Normal LV physiology | ESPVR, EDPVR, Ea, Frank-Starling, preload, afterload, inotropy, PVA |
| 2 | Heart failure and cardiomyopathy | HFrEF and HFpEF are two different problems. Restrictive, HCM, hypertensive heart |
| 3 | Valvular disease | AS, AR, MS, MR. Each lesion breaks a different phase. Acute and chronic differ |
| 4 | Mechanical circulatory support | IABP, Impella P1 to P9, VA-ECMO, ECPELLA, and why ECMO can worsen the LV |
| 5 | Interventions | Pre and post TAVR, MVR and CRT, read as before and after pairs |

The Learn tab covers this in 8 chapters: what a PV loop is, the four phases, the three lines, the three levers, energetics, HFrEF against HFpEF, reading valve disease, and devices and interventions.

---

## Quick Start

### 1. Pick a condition

Use the **Condition** dropdown on the left. The 24 conditions are grouped as physiology, heart failure and cardiomyopathy, valvular disease, and interventions. The loop, the metrics and the teaching notes update at once.

The **Library** tab shows the same conditions as cards, each with a one line signature and the evidence behind it. Any card opens straight into the simulator.

### 2. Set a reference loop

Use **Reference loop (dotted)**, under the device selector. Leave it on **Automatic** and it does the right thing. To study one lever, load a condition, press **Pin this loop**, then move a single slider and watch the live loop pull away from the dotted one.

### 3. Move one lever at a time

| Slider | What it changes | What to watch |
|---|---|---|
| Contractility (Ees) | Slope of the ESPVR | Loop height, ESV, EF |
| Preload (EDV) | Filling volume | Loop width, SV by Frank-Starling |
| Afterload (MAP) | Arterial pressure | Loop height, ESV, SV |
| Unstressed volume (V₀) | ESPVR x-intercept | Lateral position of the ESPVR |
| Stiffness (amplitude) | Height of the EDPVR | Filling pressure at any volume |
| Curvature (β) | Exponential rate of the EDPVR | Shape of the EDPVR at high volume |

Moving one lever at a time is something you can never do at the bedside. That is the point of the tool.

### 4. Animate the cycle

Press **Animate the cycle**. The dot traces the four phases and the phase rail lights up with it. Speeds are **Teaching**, **Real-time** and **Fast**. The time tracings sweep in step with the dot.

### 5. Add mechanical support

Use **Mechanical support**. The dotted reference switches automatically to the same heart without the device, so the effect is visible at once.

- **IABP**: modest unloading. The loop shifts down and left
- **Impella**: raise the P-level. The loop shrinks and triangularises, PVA falls
- **VA-ECMO**: raise the RPM. The loop is pushed up and right and PVA rises. This is the LV distension paradox
- **ECPELLA**: ECMO plus an Impella vent. The loop is pulled back down

### 6. Toggle the overlays

The overlay row sits under the plot: ESPVR, EDPVR, Ea, PVA energy shading, stroke work fill, aortic pressure lines, peak LV pressure and valve event labels.

### 7. Read the metrics

| Metric | Meaning |
|---|---|
| Stroke volume | EDV minus ESV, in mL |
| Ejection fraction | SV / EDV, as a percentage |
| Cardiac output | At a fixed rate of 75, including any device flow, in L/min |
| Aortic BP | Aortic systolic and diastolic pressure, in mmHg |
| VA coupling | Ea/Ees. Optimal is about 0.6 to 1.2 |
| Stroke work | Loop area, the mechanical work per beat, in mmHg·L |
| PVA | Pressure-volume area, a proxy for myocardial oxygen consumption |
| Efficiency | Stroke work / PVA. This is the mechanical ratio, not whole-body oxygen efficiency |

### 8. Use it offline on your phone

1. Open the simulator in your phone browser
2. **iPhone or iPad (Safari)**: tap Share, then **Add to Home Screen**
3. **Android (Chrome)**: tap the ⋮ menu, then **Add to Home Screen** or **Install app**

It then works with no internet. Only the web fonts need a connection, and the page falls back to system fonts without one.

---

## Calibration and Validation

Two choices keep the model honest for teaching.

**1. A normal heart shows no gradient.** In version 1.5 a normal loop showed a false 35 mmHg difference between peak LV pressure and aortic systolic pressure. In 2.0 the aortic valve conductance is set so that peak LV pressure equals aortic systolic pressure in normal physiology, while severe aortic stenosis still produces a genuine gradient of about 50 mmHg. The gradient now means what it says.

**2. Arterial compliance is fixed, not re-tuned for each condition.** Version 1.5 searched for a compliance that pushed every condition toward a stroke volume of 92 mL, which quietly normalised away the abnormality being taught. In 2.0 compliance is fixed, so a failing heart reads a genuinely low stroke volume.

All 24 conditions were checked against expected ranges for stroke volume, ejection fraction, chamber volumes, aortic pressure, filling pressure and ventriculo-arterial coupling. Chronic volume overload is modelled with compliant, eccentric chambers. Acute lesions and restrictive or hypertrophic hearts are modelled with stiff chambers. Devices were verified too: IABP and Impella lower PVA, Impella raises output while shrinking the loop, VA-ECMO reproduces the LV distension paradox, and ECPELLA vents it.

### Model limits

This is a **single left ventricle** model. There is no right heart, no explicit atria, no lungs, no baroreflex and no variable heart rate. It cannot represent tamponade, constriction, right heart failure, pulmonary hypertension or dynamic LVOT obstruction. Cardiac output at high heart rates is conservative. Conditions that depend on those mechanisms are described in the Library but are not simulated. Numbers are physiologically plausible, not patient specific.

---

## Deploy Your Own Copy

There is no build step and no dependencies.

**Update this repository**

1. Open the repository on GitHub
2. Click **Add file**, then **Upload files**
3. Drag in `index.html`. It replaces the old one
4. Write a commit message and click **Commit changes**
5. GitHub Pages rebuilds by itself. Hard refresh the site with Ctrl+Shift+R or Cmd+Shift+R

**Start a new repository**

1. Create a **Public** repository
2. Upload `index.html` to the root. The file must keep that name
3. Open **Settings**, then **Pages**
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**
5. Set the branch to `main` and the folder to `/ (root)`, then **Save**
6. The URL appears at the top of that page after about a minute

**Run it locally**: double-click `index.html`. Nothing else is needed.

---

## How to Cite

```
Parcha, V. CardioMechanics 2.0 PV Loop Simulator (2026). An interactive browser-based educational
tool for left ventricular pressure-volume loop physiology.
Available at: https://torsades-de-pointes.github.io/cardiomechanics/
```

BibTeX:

```bibtex
@software{cardiomechanics2026,
  title  = {CardioMechanics 2.0 PV Loop Simulator},
  author = {Parcha, Vibhu},
  year   = {2026},
  url    = {https://torsades-de-pointes.github.io/cardiomechanics/},
  note   = {Physics engine adapted from Mark N (2024)
            pressure-volume-loops (MIT License).
            24 conditions across normal physiology, heart failure,
            valvular disease, mechanical support and interventions.}
}
```

---

## Attribution and License

### This project

Released under the MIT License. See [LICENSE](LICENSE). The educational content is offered under CC BY 4.0. Attribution is appreciated.

### Physics engine, Nick Mark MD (MIT)

The core physics engine is adapted from Nick Mark's open-source simulator: Mark N (2024). *pressure-volume-loops*. GitHub: [github.com/nickmmark/pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops). MIT License.

**Modifications in version 1.x**

- Elastance shape factor n=8 to n=3, which prevents unrealistic LVP spikes above aortic pressure
- Aortic valve conductance raised, for physiological LVP and aortic pressure equalisation
- ESPVR back-calculated through the actual end-systolic point
- PVA potential energy geometry corrected by exact integration rather than a triangle
- Extended with Stages 2 to 5

**Further modifications in version 2.0**

- Aortic valve conductance raised again, so a normal heart shows no false LV to aortic gradient while aortic stenosis keeps a true one
- The per-condition arterial compliance search was removed and replaced with a fixed physiologic compliance, so stroke volume is no longer normalised across conditions
- Condition library rebuilt and recalibrated to 24 conditions. Chronic lesions are modelled as compliant chambers and acute lesions as stiff chambers
- ECPELLA (VA-ECMO plus Impella venting) added
- Dotted reference loops, with automatic selection of the useful comparison, and loop pinning
- Rewritten as one responsive, dependency-free file. The D3 dependency and the separate mobile build are gone

Full physics documentation is in [TECHNICAL_REFERENCE.md](TECHNICAL_REFERENCE.md).

---

## ⚠️ Disclaimer

CardioMechanics is for **educational purposes only**.

- **Do not** use it for clinical decision-making
- **Do not** use it for patient management or diagnosis
- **Do** use it for teaching, self-study and presentations
- **Do** use it to build mechanistic intuition for cardiovascular physiology

---

## Feedback and Contact

Questions, physiological errors, or suggestions for new pathologies are welcome.

- Email: vibhuparcha@gmail.com
- GitHub Issues: open an issue
- GitHub Discussions: start a discussion

If you use CardioMechanics in teaching, a GitHub ⭐ helps others find it. Please also cite it when appropriate.

---

## Acknowledgements

| Person | Contribution |
|---|---|
| Nick Mark MD | Original *pressure-volume-loops* (MIT). Physics engine foundation |
| Richard E. Klabunde PhD | cvphysiology.com, a definitive free cardiovascular physiology resource |
| Alex Yartsev | derangedphysiology.com, precise and referenced PV loop explanations |
| Hiroyuki Suga and Kiichi Sagawa | The 1970s and 1980s experimental work that established the elastance model |
| Daniel Burkhoff | PV loop analysis of heart failure and mechanical circulatory support |

---

## Changelog

| Version | Changes |
|---|---|
| **2.0** | Four tabs (Simulator, Learn, Library, Reference). Dotted reference loops with automatic comparison and loop pinning. 24 conditions. ECPELLA. 8 chapter handbook. Live pressure and volume time tracings. Champagne and Monitor themes. Physics recalibrated, so a true aortic gradient appears only in AS and arterial compliance is fixed. One responsive file, no D3, no separate mobile build |
| 1.5 | 6 UI themes, mobile Canvas2D offline version, EDPVR and ESPVR sliders, physics corrections, GitHub Pages deployment |
| 1.4 | Stage 5: interventions (TAVR, MVR, CRT-P) |
| 1.3 | Stage 4: MCS (IABP, Impella, VA-ECMO) |
| 1.2 | Stage 3: valvular disease (AS, AR, MS, MR) |
| 1.1 | Stage 2: HFrEF, HFpEF |
| 1.0 | Stage 1: normal physiology |

---

[torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/) · Educational use only · MIT License · 2026
