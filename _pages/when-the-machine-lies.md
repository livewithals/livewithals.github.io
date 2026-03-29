---
layout: research
title: "When the Machine Lies"
eyebrow: Research — Case Report
permalink: /research/when-the-machine-lies/
hero_image: hero-research.jpg
math: true          # <-- enables MathJax on this page
authors: "Harsh Kumar Narula"
date_published: "2025"
pdf_link: "https://drive.google.com/file/d/1q7m-QBSKB7Ku7cXuZpQzywNuHiXjT6vC/view?usp=drive_link"
description: >
  A case report documenting how a substituted exhalation valve caused silent
  tidal volume overestimation in a home ventilator-dependent ALS patient,
  with a proposed bedside correction heuristic (PAVC).
---

When you love someone, you do everything possible to protect them. Nine years on,
that has not changed. As our father's ALS caregivers, we noticed a troubling
discrepancy — his ventilator was displaying normal values while he kept telling us
something was wrong. So we investigated.

**The machine was lying.**

<div class="finding-box">
<h4>Key Finding</h4>
<p>
A single exhalation valve substitution was silently skewing tidal volume readings
by an <strong>average of 84 mL per breath</strong> — with no alarm, no alert, and
no visible indication on the display.
</p>
</div>

---

## Background

In closed-loop ventilation modes such as **iVAPS, AVAPS, and VAT**, the ventilator
continuously adjusts delivered pressure to maintain a target tidal volume ($V_T$).
This feedback loop assumes that the measured $V_T$ accurately reflects actual
lung delivery.

When a non-native exhalation valve is substituted, its different flow-resistance
characteristics cause the ventilator's internal flow sensor to **systematically
overestimate** exhaled volume — leading the machine to under-deliver pressure
while displaying apparently normal numbers.

---

## Methods

### Valve curve digitization

The manufacturer's valve resistance curve was digitized from published data using
image analysis. Resistance $R$ as a function of flow $\dot{V}$ was modelled as a
power law:

$$
R(\dot{V}) = a \cdot \dot{V}^{\,b}
$$

where $a$ and $b$ are valve-specific constants determined by least-squares fitting.

### Tidal volume error estimation

The measured tidal volume overestimation $\Delta V_T$ was derived by integrating
the flow-resistance discrepancy over a full breath cycle:

$$
\Delta V_T = \int_0^{T_e} \left[ \dot{V}_{\text{native}}(\tau) - \dot{V}_{\text{substituted}}(\tau) \right] d\tau
$$

Bootstrap uncertainty analysis ($n = 10{,}000$ resamples) was used to quantify
confidence intervals around the estimate.

---

## Proposed Correction: PAVC

We propose a novel bedside heuristic — **Pressure-Anchored Tidal Volume
Correction (PAVC)** — for fully passive patients on closed-loop ventilation,
requiring no additional equipment and no bench measurement.

The correction leverages the known relationship between peak inspiratory
pressure $P_\text{peak}$, respiratory system compliance $C_{rs}$, and
delivered volume:

$$
V_{T,\text{corrected}} = P_\text{peak} \cdot C_{rs} - V_\text{deadspace}
$$

For a passive patient where $C_{rs}$ can be estimated from a brief
end-inspiratory pause:

$$
C_{rs} = \frac{V_{T,\text{measured}}}{P_\text{plateau} - \text{PEEP}}
$$

<div class="tip-box">
<p>
<strong>PAVC in practice:</strong> Compare the pressure-derived volume estimate
against the displayed $V_T$ during routine checks. A consistent discrepancy
$> 50$ mL warrants valve inspection and, if necessary, replacement with the
manufacturer's native component.
</p>
</div>

---

## Results

| Parameter | Native Valve | Substituted Valve | Difference |
|-----------|-------------|-------------------|------------|
| Mean $V_T$ displayed (ml) | 412 ± 18 | 496 ± 22 | **+84 ml** |
| Peak pressure (cmH₂O) | 18.2 ± 1.1 | 18.0 ± 1.2 | ~0 |
| SpO₂ trend | Stable | Gradual decline | — |

The substituted valve produced **no pressure alarm** and **no visual indication**
of error, while silently under-ventilating the patient.

---

## Conclusion

If it happened to our father, it is happening to others.

Families and clinicians managing ventilator-dependent patients at home should:

1. **Use only native, manufacturer-supplied exhalation valves**
2. **Periodically verify** displayed $V_T$ against a pressure-derived estimate
3. **Report unexplained gradual SpO₂ decline** as a potential valve issue,
   even in the absence of alarms

A full PDF version of this report is available for [download]({{ page.pdf_link }}).

<div class="disclaimer-box">
We are not medical professionals — just a family doing their best, sharing what
has worked for us. Please read our <a href="/disclaimer/">disclaimer</a> before
referencing anything on this site.
</div>
