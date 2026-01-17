# Risk-Aware Locational Storage & ASCDE
**A Reliability-Complete Valuation Interface**

**Author:** Justin Candler  
**Date:** 2025-12-04  
**Framework:** Unified Energy Valuation Framework (UEVF)

## 📄 Abstract
Battery storage economics are governed by intertemporal opportunity costs, not fuel costs. his invalidates traditional thermal-centric market mitigation tools[cite: 1824]. [cite_start]This paper integrates **Risk-Aware Bid Bounds** (derived from Chance-Constrained Economic Dispatch) directly into the **System-Aware Cost of Dependable Energy (ASCDE)** paradigm.

We provide a unified view where storage offer caps, reliability targets (LOLE, EUE), and scarcity pricing arise as different slices of a single stochastic optimization problem rather than as independent institutional layers.

## 🧩 Core Concepts

### 1. The Problem with Heuristics
Traditional storage offer caps (e.g., "4th highest LMP") are static and ignore:
* **Net-load uncertainty** (renewables volatility).
* **Operator risk preference** ($\epsilon$).
* **Long-run reliability metrics** (VOLL, LOLE).

### 2. The Solution: Risk-Aware Bid Bounds
Building on Qi & Xu [1], we model storage bid bounds as probabilistic envelopes on truthful marginal opportunity costs[cite: 1826]. [cite_start]These bounds scale dynamically with grid stress and state-of-charge (SoC).

### 3. The Integration: ASCDE
We define the **System-Aware Cost of Dependable Energy (ASCDE)** as the total portfolio cost (Capex + O&M + Reliability Penalties) divided by the reliably deliverable energy (ELCC-weighted MWh):

$$ASCDE(R, \epsilon) = \frac{Capex(R) + \mathbb{E}[C_{sys}(\epsilon)] + RA(R, \epsilon)}{E_{rel}(R)}$$

here $RA(R, \epsilon)$ is the monetized reliability cost derived from the Value of Lost Load (VOLL).

## 🛠️ Implementation Roadmap for ISOs/RTOs
The paper outlines a transition from heuristic caps to a rigorous probabilistic framework:

1.  **Uncertainty Modeling:** Estimate net-load forecast errors and correlations.
2.  **Risk Calibration:** Calibrate the chance-constraint tolerance ($\epsilon$) to match planning reliability targets ($LOLE^*$, $EUE^*$).
3.  **LMP Envelopes:** Solve Chance-Constrained Economic Dispatch (CED) to generate risk-aware LMP distributions
4.  **Operational Integration:** Publish SoC-dependent bid cap tables and validate offers against telemetry in real-time

## 📂 Repository Structure
/paper`: Full PDF of "Risk-Aware Locational Storage Bid Bounds and Reliability-Aware Resource Valuation"
/appendices`: (Planned) Full primal-dual formulations, DRCC derivations, and calibration toy models.
/figures`: Visualizations of the CED-ASCDE architecture, bid cap curves, and ARQ decision maps.

## 📊 Key Figures

### The Link Between Dispatch and Valuation
The architecture connects net-load uncertainty to risk-aware LMPs, which drive both storage bid caps and reliability metrics (LOLE, EUE)

### SoC-Dependent Bid Caps
Bid caps are shown to be monotonically decreasing in State of Charge (SoC)—as the battery fills, its opportunity cost for providing flexibility decreases.

## 🔗 Citation
If you reference this framework, please cite:

```bibtex
@techreport{Candler2025RiskAware,
  title={Risk-Aware Locational Storage Bid Bounds and Reliability-Aware Resource Valuation: An ASCDE/UEVF Perspective},
  author={Candler, Justin},
  year={2025},
  institution={Nous Enterprises},
  note={UEVF Working Paper}
}
