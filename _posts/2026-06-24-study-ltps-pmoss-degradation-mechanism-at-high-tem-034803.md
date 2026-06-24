---
layout: post
title: "Study LTPS pMOS's degradation mechanism at high temperature like 80 degrees celcius with high frequency switching. The driver often fails to drive high capacitance load after the high temp./high frequency reliability cycles. It somehow recovers  when cooled down - 2026-06-24 03:48"
date: 2026-06-24 03:48:03 +0900
categories: [research]
permalink: /research/20260624-034803-study-ltps-pmoss-degradation-mechanism-at-high-tem/
---

⚠️ Only claude responded:

# LTPS pMOS Degradation at High Temperature / High Frequency: Analysis

## Overview of the Failure Signature

The symptom you're describing is quite specific and revealing:
- **Fails** to drive high-capacitance load after high-temp + high-frequency stress
- **Recovers** upon cooling down
- This points to a **thermally activated, partially reversible** degradation mechanism

---

## Primary Degradation Mechanisms to Consider

### 1. 🔴 Hot Carrier Injection (HCI) + Thermal Enhancement

**Mechanism:**
- High-frequency switching → repeated high-field transients at drain
- At 80°C, carrier energy distribution shifts → **more hot holes** in pMOS channel
- Hot holes inject into gate oxide / SiO₂-Si interface at poly-Si grain boundaries

**Why it's worse in LTPS:**
- Poly-Si has **grain boundaries** acting as local field enhancement sites
- Trap density is inherently higher than single-crystal Si
- Grain boundary traps act as **hole trap centers**

**Degradation effect:**
- ΔVth shifts positive (for pMOS, threshold becomes harder to turn ON)
- Reduced |Ids|, degraded drive current → **fails to charge high-Cap load fast enough**

**Recovery:**
- At lower temp → trapped charges partially **de-trap** (thermal emission reduced, but trap filling equilibrium shifts)
- Actually HCI is typically **not fully reversible** → so this may be a secondary contributor

---

### 2. 🔴 Negative Bias Temperature Instability (NBTI) — Most Likely Primary Mechanism

**Mechanism:**
- pMOS under negative gate bias (ON state) at elevated temperature
- Si-H bonds at Si/SiO₂ interface break → **interface traps (Dit) generated**
- Hydrogen diffuses away → forms fixed positive charges in oxide

**Reaction-Diffusion Model:**
```
Si-H + hole → Si• (trap) + H⁺ (diffuses into oxide)
```

**Why high frequency makes it worse:**
- AC NBTI: during negative half-cycle (device ON), degradation occurs
- During positive half-cycle (device OFF), **partial recovery** occurs
- But at **high frequency + high temp**, the recovery per cycle is incomplete
- Net degradation **accumulates over stress cycles**

**Effect on pMOS:**
- Vth shifts more negative (|Vth| increases)
- μeff decreases
- gm decreases
- **Drive current degrades → cannot supply enough current to high-Cap load**

**Why it recovers when cooled:**
- NBTI has a well-known **recovery component**
- Upon removing stress (cooling + no bias), H⁺ back-diffuses → partial interface trap passivation
- This is the **Reaction-Diffusion recovery** — thermally driven, happens faster at lower temp gradient
- **This matches your observation perfectly** ✅

---

### 3. 🟡 Self-Heating + Grain Boundary Trap Activation (LTPS-Specific)

**Mechanism:**
- LTPS on glass/plastic substrate → **poor thermal conductivity**
- High-frequency switching → significant self-heating in poly-Si channel
- Local temperature may exceed **nominal 80°C significantly**

**Grain boundary effects:**
```
E_grain boundary trap activation ~ 0.3–0.6 eV
At 80°C (353K): kT ~ 30 meV → traps near this energy actively capture/emit
```

- Grain boundary traps fill during high-frequency operation
- Filled traps act as **Coulomb scattering centers** → mobility degradation
- Also cause **threshold voltage shift** via trapped charge

**Recovery:**
- Upon cooling, trap occupancy changes (Fermi level shift)
- Some traps **thermally emit** captured carriers at lower temperature paradoxically shifting behavior
- Grain boundary potential barrier height changes with temperature

---

### 4. 🟡 Oxide Charge Trapping / Stress-Induced Leakage (High-Freq Specific)

**Mechanism:**
- Repeated gate oxide stress during switching transients
- In LTPS: thinner or defect-rich gate oxide (especially older a-Si converted LTPS)
-