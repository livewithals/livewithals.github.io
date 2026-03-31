---
layout: single
title: "When the Machine Lies"
permalink: /research/when-the-machine-lies/
author_profile: true
sidebar:
  nav: "main"
toc: true
toc_label: "Contents"
toc_sticky: true
header:
  overlay_image: /assets/images/hero-research.jpg
  overlay_filter: 0.5
---

<div class="research-meta">
  <span>Harsh Kumar Narula</span> &nbsp;&bull;&nbsp;
  <span>2025</span> &nbsp;&bull;&nbsp;
  <a href="https://drive.google.com/file/d/1q7m-QBSKB7Ku7cXuZpQzywNuHiXjT6vC/view?usp=drive_link" target="_blank">Download PDF</a>
</div>

When you love someone, you do everything possible to protect them. Nine years on, that has not changed. As our father's ALS caregivers, we noticed a troubling discrepancy — his ventilator was displaying normal values while he kept telling us something was wrong. So we investigated.

**The machine was lying.**

<div class="notice--als-finding">
<h4>Key Finding</h4>
<p>A single exhalation valve substitution was silently skewing tidal volume readings by an <strong>average of 84 mL per breath</strong> — with no alarm, no alert, and no visible indication on the display.</p>
</div>

## Background

In closed-loop ventilation modes such as iVAPS, AVAPS, and VAT, the ventilator continuously adjusts delivered pressure to maintain a target tidal volume ($V_T$). This feedback loop assumes that the measured $V_T$ accurately reflects actual lung delivery.

When a non-native exhalation valve is substituted, its different flow-resistance characteristics cause the ventilator's internal flow sensor to **systematically overestimate** exhaled volume — leading the machine to under-deliver pressure while displaying apparently normal numbers.

## Methods

### Valve curve digitization

The manufacturer's valve resistance curve was digitized from published data. Resistance $R$ as a function of flow $\dot{V}$ was modelled as a power law:

$$R(\dot{V}) = a \cdot \dot{V}^{\,b}$$

where $a$ and $b$ are valve-specific constants determined by least-squares fitting.

### Tidal volume error estimation

The measured tidal volume overestimation $\Delta V_T$ was derived by integrating the flow-resistance discrepancy over a full breath cycle:

$$\Delta V_T = \int_0^{T_e} \left[ \dot{V}_{\text{native}}(\tau) - \dot{V}_{\text{substituted}}(\tau) \right] d\tau$$

Bootstrap uncertainty analysis ($n = 10{,}000$ resamples) quantified confidence intervals around the estimate.

## Proposed Correction: PAVC

We propose a novel bedside heuristic — **Pressure-Anchored Tidal Volume Correction (PAVC)** — for fully passive patients on closed-loop ventilation, requiring no additional equipment:

$$V_{T,\text{corrected}} = P_\text{peak} \cdot C_{rs} - V_\text{deadspace}$$

where respiratory system compliance $C_{rs}$ is estimated from an end-inspiratory pause:

$$C_{rs} = \frac{V_{T,\text{measured}}}{P_\text{plateau} - \text{PEEP}}$$

<div class="notice--als-tip">
<strong>PAVC in practice:</strong> Compare the pressure-derived volume estimate against the displayed $V_T$ during routine checks. A consistent discrepancy $> 50$ mL warrants valve inspection and replacement with the manufacturer's native component.
</div>

## Results

| Parameter | Native Valve | Substituted Valve | Difference |
|-----------|-------------|-------------------|------------|
| Mean $V_T$ displayed (ml) | 412 ± 18 | 496 ± 22 | **+84 ml** |
| Peak pressure (cmH₂O) | 18.2 ± 1.1 | 18.0 ± 1.2 | ~0 |
| SpO₂ trend | Stable | Gradual decline | — |

## Conclusion

If it happened to our father, it is happening to others. Families and clinicians should:

1. Use only native, manufacturer-supplied exhalation valves.
2. Periodically verify displayed $V_T$ against a pressure-derived estimate.
3. Report unexplained gradual SpO₂ decline as a potential valve issue, even without alarms.

Full PDF available for [download here](https://drive.google.com/file/d/1q7m-QBSKB7Ku7cXuZpQzywNuHiXjT6vC/view?usp=drive_link).

<div class="notice--als-disclaimer">
We are not medical professionals — just a family doing their best, sharing what has worked for us. Please read our <a href="/disclaimer/">disclaimer</a>.
</div>
