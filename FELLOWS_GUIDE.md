# CardioMechanics · Fellow's Learning Guide
## A Feynman Roadmap for Mastering Pressure–Volume Loops

> *"If you can't explain it simply, you don't understand it well enough."* — Richard Feynman

**Simulator:** [torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/)  
**Contact:** [vibhuparcha@gmail.com](mailto:vibhuparcha@gmail.com) · **For educational use only.**

---

## How to Use This Guide

Work through the five stages **in order**. Each builds on the one before. For each stage:

1. **Read the concept** — understand the physics in plain language
2. **Predict the loop** — before clicking anything, draw what you expect on paper
3. **Test your prediction** — select the pathology and compare
4. **Explain it out loud** — if you can't explain it to a medical student, repeat step 1

> ⏱️ Total time: approximately **3–4 hours** for all five stages. You can pause and resume.
>
> 🖥️ **Animation controls** are available in the **Desktop version only** (`index.html`). The mobile version shows the completed steady-state loop.

---

## The One-Sentence Summary

> A PV loop is a movie of one heartbeat, told through pressure and volume. The **width** is stroke volume. The **height** is the pressure load. The **area** is the work done. Everything else is commentary.

---

# STAGE 1 — Normal Physiology
*"What does a healthy heart actually do?"*

### The Big Idea

The heart is a pressure generator that fills passively and empties actively. Two lines constrain it:

- **ESPVR** — the maximum pressure it can ever generate at any volume (contractility ceiling)
- **EDPVR** — the passive stiffness of the relaxed muscle (filling curve)

The loop must live **between** these two boundaries. Always.

---

### Step 1.1 — The Four Corners

Open the simulator → select **Normal Physiology**. Look at the four labelled points:

| Point | Valve event | What's happening |
|-------|-------------|------------------|
| ① MV Closes | Mitral valve shuts | Filling ends — isovolumetric contraction begins |
| ② AV Opens | Aortic valve opens | LV pressure now exceeds aortic diastolic → ejection begins |
| ③ AV Closes | Aortic valve shuts | Ejection ends — isovolumetric relaxation begins |
| ④ MV Opens | Mitral valve opens | LV pressure drops below LA → filling starts again |

> **Feynman test:** Cover the labels. Point to each corner and say the valve event out loud before moving on.

---

### Step 1.2 — The Four Phases

*Desktop:* Click **Animate Loop** → set speed to **Very slow**. Watch the coloured dot travel. *Mobile:* The completed loop shows all four phases simultaneously.

| Colour | Segment | Phase | Key insight |
|--------|---------|-------|-------------|
| 🟢 Green | ④ → ① | Diastolic filling | Moving **right** along the EDPVR — passive stretch |
| 🔵 Blue | ① → ② | Isovolumetric contraction | **Vertical** line — all valves closed, pressure rises, volume unchanged |
| 🔴 Red | ② → ③ | Systolic ejection | Moving **left and up** — volume falls, pressure rises then falls |
| 🟣 Purple | ③ → ④ | Isovolumetric relaxation | **Vertical** line — all valves closed, pressure falls back |

> **Key insight:** The two vertical lines exist because **all four valves are simultaneously closed** — the ventricle is a sealed box, just building or releasing pressure.

---

### Step 1.3 — The Boundary Lines

**ESPVR (green dashed):** The contractility ceiling.
- The steeper this line, the more contractile the heart
- Point ③ **always** lands exactly on this line
- Dobutamine → line rotates counter-clockwise (steeper) → ③ moves up-left → more SV

**EDPVR (gold dashed):** The exponential passive filling curve.
- **Not linear** — rises steeply at high volumes (law of diminishing returns)
- Hypertrophy or fibrosis → curve rises more steeply (stiffer ventricle fills less)
- Adjust with the **EDPVR Scale** and **EDPVR Slope** sliders

**Ea (blue dashed):** Arterial elastance — the vascular load.
- Drawn from (EDV, 0) → (ESV, ESP)
- Ea = ESP ÷ SV. Higher Ea = stiffer arteries = harder work per beat
- Optimal coupling: **Ea/Ees ≈ 0.6–1.2**

---

### Step 1.4 — Feynman Experiments

**Experiment A — Increase Preload**  
Move the **EDV slider** to 180 mL. Predict first: what happens to SV? To ESV? To EF?

> *Answer:* SV ↑. ESV unchanged (Ees and MAP are fixed). Loop widens. EF ↑ slightly. This is the **Frank-Starling mechanism** — more filling → more force.

**Experiment B — Increase Afterload**  
Move the **MAP slider** to 130 mmHg.

> *Answer:* Loop gets taller and narrower. ESV ↑ (heart can't fully empty against high pressure). SV ↓. This is why chronic hypertension causes **concentric hypertrophy** over time.

**Experiment C — Increase Contractility**  
Move the **Ees slider** to 3.5.

> *Answer:* ESPVR rotates counter-clockwise (steeper). Point ③ moves up and left. ESV ↓, SV ↑, EF ↑. This is the **inotropic effect** — e.g. dobutamine, digoxin, levosimendan.

---

### Stage 1 Mastery Check

- [ ] Why are there two vertical lines in a normal PV loop?
- [ ] What does the **slope** of the ESPVR tell you? What changes it?
- [ ] Why is the EDPVR **exponential** rather than linear?
- [ ] What is Ea/Ees and why does it matter clinically?
- [ ] What is PVA and why does it approximate MVO₂?

---

# STAGE 2 — Heart Failure
*"When the engine breaks down"*

### The Big Idea

Heart failure is not one disease — it is **two different PV loop problems**:

| Type | The problem | Loop appearance |
|------|-------------|-----------------|
| **HFrEF** | Pump too weak — ESPVR too flat | Wide, flat, shifted right |
| **HFpEF** | Pump too stiff — EDPVR too steep | Narrow, tall EDPVR, normal ESPVR |

---

### Step 2.1 — HFrEF (Systolic Heart Failure)

Select **Systolic HF (HFrEF)**. Compare to Normal.

What changed:
- Ees ↓ from 1.8 → 0.6 (ESPVR much flatter)
- ESV markedly ↑ (heart can't empty)
- EDV ↑ compensatory (Frank-Starling trying to help)
- SV ↓↓, EF < 40%

The vicious cycle:
```
↓ Ees → ↑ ESV → ESV + venous return → ↑ EDV → ↑ LVEDP → pulmonary oedema
```

> **Feynman test:** What happens if you give a vasodilator (↓ MAP) in HFrEF? Try MAP → 55.
>
> *Answer:* ESV ↓, SV ↑. Loop shifts left and gets slightly taller. This is why **afterload reduction** (ACE-i, sacubitril, ARNi) works in HFrEF — it directly increases SV.

---

### Step 2.2 — HFpEF (Diastolic Heart Failure)

Select **Diastolic HF (HFpEF)**. Look at the EDPVR curve.

What changed:
- EDPVR much steeper (↑ edpvrScale, ↑ edpvrSlope)
- EDV **smaller** — stiff ventricle won't accept volume
- EDP (pressure at ①) is **higher** despite lower volume
- EF near normal (ESPVR intact)

Try the **EDPVR Scale** and **EDPVR Slope** sliders independently — watch the filling curve steepen without changing contractility.

> **Feynman test:** Why is HFpEF harder to treat than HFrEF?
>
> *Answer:* In HFrEF you can augment contractility or reduce afterload. In HFpEF you cannot easily make the ventricle more compliant. Diuretics reduce filling pressures but risk reducing SV further. No drug has proven benefit on EDPVR stiffness.

---

### Stage 2 Mastery Check

- [ ] Draw (from memory) the HFrEF loop vs normal — including ESPVR and EDPVR
- [ ] Draw the HFpEF loop vs normal
- [ ] Explain why EF can be normal in HFpEF yet the patient has heart failure
- [ ] What does Ea/Ees >> 1 mean in HFrEF?

---

# STAGE 3 — Valvular Disease
*"Each lesion breaks one specific phase of the cardiac cycle"*

### The Elegant Insight

Know which phase each valve lesion disrupts → know the loop shape. This is mechanism, not memorisation.

| Lesion | Phase broken | Loop signature |
|--------|-------------|----------------|
| Aortic Stenosis | Ejection obstructed | Tall, narrow, ↑ peak LVP >> Ao SBP |
| Aortic Regurgitation | IVR broken (diastolic backflow) | Wide, no IVR, wide pulse pressure |
| Mitral Stenosis | Filling obstructed | Narrow, left-shifted, ↓ EDV |
| Mitral Regurgitation | IVC broken (systolic backflow) | Wide, no IVC, ↓ peak LVP |

---

### Step 3.1 — Aortic Stenosis

Select **Aortic Stenosis**. Toggle ON **Peak LVP line** and **Ao SBP/DBP lines**.

The gap between Peak LVP (red) and Ao SBP (gold) **is the transvalvular gradient**.

- Loop is **TALL** — LV generating enormous pressure against obstruction
- Loop is **NARROW** — SV reduced
- In severe AS: LV peak ~200 mmHg while aortic SBP only ~120 mmHg

> **Feynman test:** Why does the ventricle hypertrophy in chronic AS?
>
> *Answer:* Chronically elevated wall stress (Laplace: stress = P×r/2h). Concentric hypertrophy reduces r/h ratio, normalising wall stress. But the trade-off: EDPVR steepens → diastolic dysfunction co-develops.

---

### Step 3.2 — Aortic Regurgitation

Select **Aortic Insufficiency**. Look at points ③ and ④.

The IVR phase is **absent or truncated** — when the AV "closes," it leaks. Blood flows back from aorta → LV during "relaxation," so volume keeps rising. No sealed box → no isovolumetric relaxation.

Loop is **WIDE** (EDV massive = regurgitant volume + venous return). Wide pulse pressure — Ao DBP is low because aorta drains backward into LV during diastole.

---

### Step 3.3 — Mitral Stenosis

Select **Mitral Stenosis**. The loop shifts **LEFT**.

- EDV ↓ (MV can't open fully → LV fills poorly)
- Frank-Starling → SV ↓
- ESPVR is **normal** — LV systolic function preserved
- Symptoms arise from elevated LAP (gradient across MV), not LV dysfunction

> **Clinical lesson:** A patient with MS can have a "normal EF" and still have heart failure — because the problem is upstream of the LV.

---

### Step 3.4 — Mitral Regurgitation

Select **Mitral Regurgitation**. Look at points ① and ②.

The IVC phase is **absent** — as soon as LVP exceeds LAP, blood leaks backward into LA. So there is never a moment when all four valves are closed during systole.

Peak LVP is **LOW** — the LA is a low-pressure escape route. The loop "width" (EDV − ESV) is **deceptive** — much goes backward, not forward.

> **Feynman test:** A patient with MR has EF 62%. Is this truly normal?
>
> *Answer:* No. In MR, the low-impedance LA escape makes LV appear to contract well. EF 62% in MR may reflect significant underlying systolic dysfunction. The surgical guideline threshold for MR is EF < 60% (not 50%) for this exact reason.

---

### Stage 3 Mastery Check

- [ ] Explain the AS transvalvular gradient using the PV loop
- [ ] Why is there no IVR in AR?
- [ ] Why is there no IVC in MR?
- [ ] Why does MS show normal ESPVR but reduced SV?

---

# STAGE 4 — Mechanical Circulatory Support
*"Moving the loop with machines"*

### The Core Principle

Every MCS device shifts the PV loop — but in **different directions**, for different reasons:

| Device | Primary effect | MVO₂ | Mechanism |
|--------|---------------|-------|-----------|
| **IABP** | Modest ↓ afterload, slight left shift | ↓ modest | Deflates before systole, reduces ejection impedance |
| **Impella** | Strong leftward + triangularisation | ↓↓ significant | Continuously drains LV → aorta |
| **VA-ECMO** | **Rightward + upward** | ↑ **DETRIMENTAL** | Retrograde aortic flow ↑ afterload |

---

### Step 4.1 — IABP

Select **Normal** → IABP device. Compare ghost (unsupported) vs active loop.

- Loop shifts slightly left and down
- IABP is a "helping hand" — reduces afterload but **does not drain LV volume**
- Isovolumetric phases remain **perfectly vertical** (no volume change during these phases)

---

### Step 4.2 — Impella

Select **HFrEF** → Impella. Increase from P2 → P5 → P9.

Watch the transformation:
- P2: Loop slightly smaller
- P5: Loop triangular — IVC slopes (volume draining during contraction)
- P9: "Teardrop" — IVC and IVR converge nearly to a point

The Impella continuously drains LV → aorta, emptying the ventricle **before** the AV even opens. IVC slopes because volume is falling during isovolumetric contraction.

> **Key insight:** Despite the smaller loop area, the heart is doing **less work** and consuming **less O₂**. This is myocardial unloading — the primary goal in cardiogenic shock recovery.

---

### Step 4.3 — VA-ECMO (The Paradox)

Select **HFrEF** → VA-ECMO. Increase RPM gradually.

Loop shifts **RIGHT and UP**. Why?
- ECMO returns blood to the **aorta** (retrograde)
- This increases aortic pressure → LV must pump against **higher afterload**
- EDV and EDP rise (LV distension risk)
- Systemic MAP improves, but LV is **worse off**

> **Feynman test:** A cardiogenic shock patient on VA-ECMO has MAP 75 but worsening pulmonary oedema. Explain using PV loops. What's the next step?
>
> *Answer:* VA-ECMO increased LV afterload → EDV/LVEDP rising → pulmonary oedema worsening despite better MAP. Solution: **LV venting** with Impella (ECPELLA). Try selecting both VA-ECMO + Impella — watch the loop shift back left.

---

### Stage 4 Mastery Check

- [ ] Why does Impella reduce MVO₂ even though the heart beats at the same rate?
- [ ] Why does VA-ECMO increase LV afterload?
- [ ] What does "LV distension" look like on a PV loop?
- [ ] Why does IABP keep vertical isovolumetric lines while Impella makes them slope?

---

# STAGE 5 — Interventions
*"The loop before and after treatment"*

### Step 5.1 — TAVR

Select **Pre-TAVR** → observe the tall narrow loop. Then **Post-TAVR**.

After TAVR:
- Transvalvular gradient disappears (Peak LVP ≈ Ao SBP)
- Loop **widens** (↑ SV) and **shortens** (↓ peak LVP)
- EF may paradoxically **FALL** transiently

> **Teaching pearl:** The pre-TAVR "preserved" EF was maintained by high afterload from stenosis. After TAVR, the true (lower) Ees is revealed. A falling EF post-TAVR does not mean the procedure failed — it means the AS was masking poor underlying contractility.

---

### Step 5.2 — MVR (Mitral Valve Repair/Replacement)

Select **Pre-MVR** → observe the wide, IVC-less loop. Then **Post-MVR**.

After repair:
- IVC is **restored** (no more regurgitation at onset of systole)
- Loop **smaller** (regurgitant volume eliminated)
- EF may **DROP** despite clinical improvement

> **Timing principle:** Operate before EF falls below 60% or LVESD exceeds 40 mm — because by that point, the masked contractile dysfunction is too advanced.

---

### Step 5.3 — CRT-P (Cardiac Resynchronisation Therapy)

Select **Pre-CRT-P** → wide, flat, dyssynchronous loop. Then **Post-CRT-P**.

After resynchronisation:
- Ees ↑ (functional inotropy — more coordinated contraction)
- Functional MR ↓ (better LV geometry)
- Loop **rises and narrows**
- PVA ↓ despite better SV (more efficient energy use per beat)

> **Key insight:** CRT doesn't give the heart more fuel. It teaches it to fire in the right order. The efficiency improvement — more work, less energy — is the signature of restored synchrony.

---

# Final Self-Test — The Consultant's Challenge

For each scenario, predict the PV loop features **before** selecting anything:

1. A 75-year-old with severe AS and EF 35% undergoes TAVR. Post-procedure EF is 28%. Was the TAVR a failure?

2. A 45-year-old in cardiogenic shock (HFrEF, EF 18%) is placed on VA-ECMO. MAP improves to 75 mmHg but pulmonary oedema worsens. Explain using PV loops. What is the next step?

3. A 60-year-old with LBBB, EF 28%, on optimal medical therapy, is proposed for CRT-P. What does CRT add on a PV loop? Why might 30% of patients not respond?

4. A 50-year-old with severe MR has EF "preserved" at 62%. Asymptomatic. Why operate now rather than wait for symptoms?

---

## Feynman's Rule for PV Loops

If you truly understand PV loops, you can explain from **first principles** — without memorising:

- Why afterload reduction helps HFrEF
- Why VA-ECMO can worsen cardiogenic shock
- Why MR looks worse after valve repair (transiently)
- Why AS patients can have "preserved" EF but severe heart failure

If you can do all four from mechanism, you own this material.

---

*CardioMechanics Fellow's Guide · v1.5 · 2025*  
*Simulator: [torsades-de-pointes.github.io/cardiomechanics](https://torsades-de-pointes.github.io/cardiomechanics/)*  
*Contact: [vibhuparcha@gmail.com](mailto:vibhuparcha@gmail.com)*  
*"The goal is not to learn facts about PV loops. The goal is to see haemodynamics through them."*  
*For educational use only. Not for clinical decision-making.*
