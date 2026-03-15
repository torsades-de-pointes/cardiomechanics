# CardioMechanics · Technical Reference
## Physics Engine · Architecture · Limitations · References

**Simulator:** [torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/)  
**Contact:** [vibhuparcha@gmail.com](mailto:vibhuparcha@gmail.com) · **MIT License · Educational use only.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Built with D3.js](https://img.shields.io/badge/Desktop-D3.js%20v7-orange.svg)](https://d3js.org/)
[![Mobile Canvas](https://img.shields.io/badge/Mobile-Canvas2D-brightgreen.svg)]()
[![Stages: 5](https://img.shields.io/badge/Stages-1--5-blue.svg)]()

---

## Overview

**CardioMechanics** is a single-file, browser-based left ventricular pressure–volume (PV) loop simulator. Two versions are provided:

| Version | File | Renderer | Dependencies | Best for |
|---------|------|----------|--------------|----------|
| Desktop | `index.html` | D3.js v7 SVG | D3 CDN + Google Fonts | Laptop/desktop, animation, teaching |
| Mobile / Offline | `mobile.html` | Canvas2D | None (system fonts) | Phone, tablet, offline use |

The simulator spans five progressive learning stages:

| Stage | Content |
|-------|---------|
| 1 | Normal LV physiology — ESPVR, EDPVR, Ea, preload/afterload/inotropy, PVA |
| 2 | Heart failure — HFrEF (systolic), HFpEF (diastolic) |
| 3 | Valvular disease — AS, AR, MS, MR |
| 4 | Mechanical circulatory support — IABP, Impella (P1–P9), VA-ECMO |
| 5 | Interventions — Pre/Post TAVR, MVR, CRT-P |

---

## Attribution

The physics engine is adapted from **Nick Mark MD's** open-source simulator:

> **Mark N** (2024). *pressure-volume-loops*. GitHub: [nickmmark/pressure-volume-loops](https://github.com/nickmmark/pressure-volume-loops). **MIT License.**

Used under the MIT License. Original copyright notice preserved. See [LICENSE](LICENSE) for full text.

**Modifications from original (documented for MIT compliance):**

| Parameter | Original | CardioMechanics | Reason |
|-----------|----------|-----------------|--------|
| Elastance shape factor n | 8 | **3** | Prevents unrealistic LVP spikes above aortic pressure |
| Aortic valve conductance kAv | 18 mL/s/mmHg | **28 mL/s/mmHg** | More physiological LVP–AoP equalisation on opening |
| Windkessel runoff Rr | 1.2 mmHg·s/mL | **0.8 mmHg·s/mL** | Aortic pressure tracks ejection more closely |
| ESPVR V₀ | Slider value directly | **Back-calculated** from end-systolic point | Guarantees ESPVR passes through ③ in all pathologies |
| PVA potential energy | Triangular approximation | **Correct integration** bounded by ESPVR + EDPVR | Physiologically accurate |

*Extended with:* Stages 2–5 pathologies, 6 UI themes, mobile Canvas2D renderer, EDPVR Scale/Slope sliders, stage educational banners.

---

## Physics Engine

### Core Model

The simulator uses the **time-varying elastance model** (Sagawa 1981).

#### Ventricular Elastance E(t)

```
E(t) = (Ees − 0.1) × sin³(πt/Ts) + 0.1    for t ∈ [0, Ts]
E(t) = 0.1                                    for t > Ts
```

- **Ees** — end-systolic elastance (mmHg/mL): slope of ESPVR, load-independent contractility index
- **Ts = 0.30 s** — systolic duration
- **n = 3** — shape factor (smoother activation curve; prevents LVP spikes above aortic pressure)

#### Instantaneous LV Pressure

```
P(t) = max( E(t) × (V(t) − V₀),  EDPVR(V(t)) )
```

The maximum of active contraction pressure **or** passive diastolic filling pressure, whichever is greater.

#### EDPVR (End-Diastolic Pressure-Volume Relationship)

```
P_ed = (2 × scale) + (1.2 × scale) × exp(0.016 × slope × V)
```

Exponential passive stiffness curve. `scale` and `slope` are independently adjustable via sidebar sliders.

#### ESPVR (End-Systolic Pressure-Volume Relationship)

```
P_es = Ees × (V − V₀_eff)

where: V₀_eff = ESV − ESP/Ees    (back-calculated from simulation-derived end-systolic point)
```

`V₀_eff` is back-calculated from the actual AV-closes event — guaranteeing the line passes through point ③ in all pathologies regardless of the V₀ slider value.

#### Effective Arterial Elastance (Sunagawa 1983)

```
Ea = ESP / SV
```

Drawn as a line from (EDV, 0) → (ESV, ESP). Optimal ventriculo-arterial coupling: **Ea/Ees ≈ 0.6–1.2**.

#### Windkessel Aortic Model

```
dPao/dt = [ (Q_out + Q_pump + Q_ecmo − Q_AI) − (Pao − MAP)/Rr ] / C_ao_eff
```

Parameters:
- **Rr = 0.8 mmHg·s/mL** — peripheral runoff resistance
- **C_ao_eff = C × (1 + 0.5 × (1 − Pao/90))** for Pao < 90 mmHg — pressure-dependent compliance
- **C_ao** auto-calibrated per pathology to target SV ≈ 80 mL at baseline (candidates: 1.0–4.2)

#### Valve Conductance Flows

| Flow | Condition | Formula |
|------|-----------|---------|
| Mitral inflow Q_in | P_la > P_lv | `(P_la − P_lv) × kFill_eff` |
| Aortic outflow Q_out | P_lv > P_ao | `(P_lv − P_ao) × kAv_eff` |
| AI regurgitation Q_AI | Diastole AND P_ao > P_lv | `(P_ao − P_lv) × kAI` |
| MR regurgitation Q_MR | Systole AND P_lv > P_la | `(P_lv − P_la) × kMR` |

Default conductances: **kFill = 22 mL/s/mmHg**, **kAv = 28 mL/s/mmHg**

#### Valvular Pathology Modifiers

| Condition | Parameter | Value (severe) | Mechanism |
|-----------|-----------|----------------|-----------|
| Aortic Stenosis | avObs | 0.35 | `kAv_eff = kAv × avObs` |
| Aortic Insufficiency | aiReg | 0.18 | `kAI = kAv × aiReg` |
| Mitral Regurgitation | mrReg | 0.28 | `kMR = kFill × mrReg` |
| Mitral Stenosis | msRed | 0.55 | `kFill_eff = kFill × (1 − msRed)` |

#### MCS Device Models

**IABP:**
```
MAP_eff = MAP − 25 mmHg
```
Approximates systolic unloading via diastolic augmentation. Isovolumetric phases remain vertical (no direct volume drainage).

**Impella:**
```
Q_pump = (1.5 + P_level × 0.65) × 26.7 mL/s × pumpFrac(P_lv, P_ao)
```
Continuous LV drainage modulated by sigmoid pressure function. P-levels 1–9. Loop triangularises at P7–P9 ("teardrop" shape).

**VA-ECMO:**
```
MAP += (10 + 15 × flow/4.5) / 2          (retrograde aortic flow → ↑ afterload)
kFill_eff = kFill × exp(−0.04 × flow)     (reduced venous return)
```
LV distension occurs when MAP exceeds maximal LV pressure generation.

#### PVA and Myocardial Energetics (Suga 1981)

```
PVA = SW + PE
```

- **SW (Stroke Work)** = area enclosed by PV loop (shoelace theorem)
- **PE (Potential Energy)** = ∫(ESPVR − EDPVR) dV from V₀_eff to ESV  
  Bounded by: ESPVR (top), IVR vertical at ESV (right), EDPVR curve (bottom)
- **Myocardial Efficiency** = SW / PVA × 100%  (normal ≈ 25–35%)

PVA is proportional to myocardial O₂ consumption (MVO₂) across physiological and pathological states.

#### Simulation Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| dt | 0.002 s | Integration timestep |
| Cycle length | 0.85 s | Cardiac cycle (~71 bpm) |
| Ts | 0.30 s | Systolic duration |
| Warmup beats | 7 | Beats to haemodynamic steady state before recording |
| LA pressure | 10 mmHg | Fixed left atrial pressure |
| C_ao candidates | [1.0, 1.5, 2.0, 2.8, 3.5, 4.2] | Auto-selected for SV ≈ 80 mL at baseline |

---

## Pathology Configurations (Stage 1–5)

| Key | Ees | EDV | MAP | V₀ | Notes |
|-----|-----|-----|-----|-----|-------|
| normal | 1.8 | 140 | 80 | 10 | Reference state |
| hf (HFrEF) | 0.6 | 230 | 70 | 15 | edpvrScale=1.1 |
| dd (HFpEF) | 2.2 | 115 | 95 | 22 | edpvrScale=1.55, edpvrSlope=1.20 |
| as (AS) | 1.6 | 200 | 105 | 10 | avObs=0.35 |
| ai (AR) | 2.0 | 210 | 70 | 8 | aiReg=0.18 |
| ms (MS) | 1.8 | 90 | 75 | 10 | msRed=0.55 |
| amr (MR) | 1.7 | 190 | 65 | 12 | mrReg=0.28 |
| pre_tavr | 1.6 | 200 | 105 | 10 | avObs=0.35 |
| post_tavr | 1.9 | 155 | 82 | 10 | avObs=1.0 |
| pre_mvr | 1.5 | 210 | 65 | 12 | mrReg=0.32 |
| post_mvr | 1.8 | 155 | 72 | 10 | mrReg=0.0 |
| pre_crtp | 0.7 | 240 | 68 | 16 | edpvrScale=1.15, mrReg=0.12 |
| post_crtp | 1.2 | 195 | 74 | 13 | edpvrScale=1.05, mrReg=0.04 |

---

## Software Architecture

```
index.html  (Desktop — D3.js, ~92 KB)
mobile.html (Mobile/Offline — Canvas2D, ~60 KB)
│
├── <style>
│     CSS design system: variables, 6 themes via [data-theme] attribute
│     Responsive layout: desktop sidebar + mobile single-column
│
├── HTML
│     Theme bar       — theme selector chips, localStorage persistence
│     Header          — logo, stage pill, pathology + MCS dropdowns
│     Canvas/SVG area — plot + metrics + energetics + phase chips
│     Teaching note   — contextual educational card (below canvas)
│     Sidebar/Controls— cardiac parameter sliders, MCS controls,
│                        overlay toggles, quick preset buttons
│
└── <script>
      PATHS {}         Pathology config objects (13 presets, Stages 1–5)
      ST {}            Current simulator state
      getPWC()         EDPVR exponential model
      solveLoop()      7-beat warmup + Windkessel differential equation solver
      calcMetrics()    SV, EF, CO, ESP, Ea, SW, PE, PVA, efficiency
      draw()           Render all SVG/Canvas elements
      updateBanners()  Stage-contextual educational banners
      [Desktop only]
        D3 SVG setup   Layers, scales, axes, Catmull-Rom splines
        runAnim()      Phase-aware rAF loop with 4 speed tiers
        Hover tooltip  Closest-point proximity detection
      [Mobile only]
        Canvas2D renderer — no external dependencies
        Touch event handlers
      initSliders()    Reactive UI — slider → state → redraw
      setTheme()       CSS variable theme switching
```

### Key Design Decisions

**Single-file architecture:** All CSS, JS, and HTML in one file. Share via email, WhatsApp, USB — no web server needed.

**ESPVR back-calculation:** Rather than trusting V₀ from the slider, V₀_eff is computed from the simulation-derived end-systolic point. This guarantees ESPVR always passes through ③ regardless of pathology or MCS state.

**CSS variable theming:** Six UI themes (Morning, Midnight, Goodnight, Chill, Obsidian, Champagne) implemented as CSS variable overrides on `[data-theme]` — no JS required for switching.

**Warmup beats:** Simulation runs 7 beats before recording to allow the Windkessel model and mitral filling to reach haemodynamic steady state, eliminating transient artefacts.

**Mobile Canvas2D:** D3 replaced with native Canvas2D API — no CDN, works completely offline. System font stack (−apple-system, BlinkMacSystemFont, Segoe UI...) eliminates Google Fonts dependency.

---

## Limitations

These are inherent model simplifications trainees should understand:

1. **Two-element Windkessel:** Approximates vascular impedance. Does not model characteristic impedance, wave reflections, or pulse wave velocity.

2. **Fixed heart rate:** HR fixed at ~71 bpm (cycle = 0.85 s). No Frank-Starling × HR interaction modelled.

3. **Left heart only:** No RV PV loop, no RV-LV interdependence, no pulmonary vascular dynamics.

4. **Linear valve conductance:** Q = ΔP × k only. No orifice dynamics, no gradual opening/closing, no flow inertia.

5. **MCS approximations:**
   - IABP: MAP reduction only (no pulsatility modelling)
   - Impella: Sigmoid pressure-dependent drain (no true rotor physics)
   - VA-ECMO: MAP increase (no retrograde pulsatility, no mixing zone)
   These do not capture pulsatile interactions or catheter position effects.

6. **CRT-P:** Dyssynchrony approximated by reduced Ees + functional MR. True intraventricular dyssynchrony mechanics (septal bounce, LBBB activation pattern) not modelled.

7. **Compliance calibration:** C_ao chosen from a coarse candidate list. Fine patient-level arterial compliance variation not captured.

8. **LA pressure fixed:** LAP is fixed at 10 mmHg. No pulmonary venous model or dynamic LAP response.

---

## Technologies & Dependencies

### Desktop (`index.html`)
| Dependency | Version | Purpose | Source |
|------------|---------|---------|--------|
| D3.js | 7.8.5 | SVG rendering, scales, axes, splines | cdnjs.cloudflare.com |
| Google Fonts | — | Nunito, JetBrains Mono, Cormorant Garamond | fonts.googleapis.com |

### Mobile (`mobile.html`)
| Dependency | Version | Purpose | Source |
|------------|---------|---------|--------|
| None | — | All rendering via Canvas2D API | Built-in |
| System fonts | — | -apple-system, Segoe UI, Roboto, etc. | Operating system |

> **For fully offline desktop use:** Download D3 locally and replace the CDN `<script>` tag. Replace Google Fonts `<link>` with system font stack.

---

## References

### Core Physics Models
1. **Sagawa K** (1978). The ventricular pressure-volume diagram revisited. *Circulation Research* 43(5):677–687. https://doi.org/10.1161/01.RES.43.5.677
2. **Sagawa K et al** (1981). The ventricular pressure-volume relationship. *Cardiovascular Physiology* — elastance model foundation.
3. **Suga H, Hayashi T, Shirahata M** (1981). Ventricular systolic pressure-volume area as predictor of cardiac oxygen consumption. *American Journal of Physiology* 240(1):H39–H44.
4. **Suga H** (1979). External mechanical work from relaxing ventricle. *American Journal of Physiology* 236(3):H494–H497.
5. **Sunagawa K et al** (1983). Left ventricular interaction with arterial load studied in isolated canine ventricle. *American Journal of Physiology* 245(5):H773–H780.
6. **Kelly RP et al** (1992). Effective arterial elastance as index of arterial vascular load in humans. *Circulation* 86(2):513–521.

### Educational Resources
7. **Klabunde RE** (2021). *Cardiovascular Physiology Concepts*, 3rd ed. Wolters Kluwer. https://cvphysiology.com
8. **Yartsev A** (2020). Ventricular pressure-volume loops. *Deranged Physiology*. https://derangedphysiology.com
9. **Bastos MB et al** (2020). Invasive left ventricle pressure–volume analysis. *European Heart Journal* 41(12):1286–1297. https://doi.org/10.1093/eurheartj/ehz552

### MCS Device Models
10. **Burkhoff D et al** (2006). Hemodynamics of mechanical circulatory support. *JACC* 48(11):2134–2145.
11. **Naidu SS** (2011). Novel percutaneous cardiac assist devices. *Circulation* 123(5):533–543.
12. **Uriel N et al** (2012). Hemodynamic ramp tests in patients with LVADs. *JACC Heart Failure*.
13. **Meani P et al** (2017). LV distension during VA-ECMO. *ASAIO Journal* 63(1):e1–e5.

### Intervention Data
14. **Généreux P et al** (2014). Outcomes following TAVR: PARTNER trial. *JACC* 63(22):2349–2361.
15. **Stone GW et al** (2021). Transcatheter vs surgical AVR in low-risk patients. *NEJM* 384:2032–2041.
16. **Moss AJ et al** (2002). Cardiac-resynchronization therapy. *NEJM* 346:1845–1853.
17. **Cleland JGF et al** (2005). CRT-P in heart failure (CARE-HF). *NEJM* 352:1539–1549.

### Original Code Base
18. **Mark N** (2024). pressure-volume-loops. GitHub: https://github.com/nickmmark/pressure-volume-loops (MIT License). Physics engine adapted under MIT licence.

---

## Acknowledgements

- **Nick Mark MD** — open-source pressure-volume-loops simulator (MIT). Physics engine foundation.
- **Richard E. Klabunde PhD** — cvphysiology.com, the definitive free cardiovascular physiology resource
- **Alex Yartsev** — Deranged Physiology's precise and referenced PV loop explanations
- **Hiroyuki Suga & Kiichi Sagawa** — 1970s–80s experimental work establishing the elastance model

---

## License

CardioMechanics is released under the **MIT License**.

The physics engine is adapted from Nick Mark's `pressure-volume-loops` (MIT License). The original copyright notice is preserved in [LICENSE](LICENSE) as required.

Educational content (teaching notes, clinical annotations, stage banners) is original.

**For educational use only. Not for clinical decision-making.**

---

## Changelog

| Version | Changes |
|---------|---------|
| 1.5 | 6 UI themes, mobile Canvas2D offline version, EDPVR Scale/Slope sliders, physics corrections (n=3, kAv=28, Rr=0.8), PVA geometry fix, GitHub Pages deployment |
| 1.4 | Stage 5: Interventions (pre/post TAVR, MVR, CRT-P) |
| 1.3 | Stage 4: MCS (IABP, Impella P1–P9, VA-ECMO) |
| 1.2 | Stage 3: Valvular disease (AS, AR, MS, MR) |
| 1.1 | Stage 2: HFrEF, HFpEF |
| 1.0 | Stage 1: Normal physiology |

---

*CardioMechanics Technical Reference · v1.5 · 2025*  
*[torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/) · MIT License · For educational use only*
