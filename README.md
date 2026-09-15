# Countercyclical DeFi: A Treasury-Constrained Control Framework for Systemic Risk

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Research License: CC BY 4.0](https://img.shields.io/badge/Research-CC%20BY%204.0-lightgrey.svg)](LICENSE-RESEARCH)

## Abstract

Modern DeFi systems enable rapid capital transfer, automated lending, liquidations, and deep composability. While these properties increase efficiency under normal conditions, they can amplify systemic shocks: a decline in collateral value triggers liquidations, sales worsen market depth, and deteriorating prices trigger further liquidations. 

This repository introduces a countercyclical architecture for systemic-risk management where the protocol observes market conditions, evaluates systemic stress via a multidimensional **System Stress Index (SSI)**, switches policy regimes, and executes limited interventions from a pre-funded treasury. 

The core research objective is to evaluate whether a **treasury-constrained, state-dependent control policy** can reduce expected systemic damage from DeFi liquidation cascades relative to conventional risk-management policies. The framework is formulated as a constrained stochastic control problem.

---

## Core Architecture & Components

1. **System Stress Index (SSI):** A multidimensional index ($SSI_t = \sum_i w_i x_{i,t}$) incorporating normalized volatility, drawdown, utilization deviation, liquidation velocity, liquidity gaps, and demand shocks, smoothed over time and protected against anomalies.
2. **State-Dependent Control:** Transitioning beyond static parameters or utilization-only models by adapting borrowing costs, LTV, liquidation thresholds, and treasury interventions based on market regimes.
3. **Countercyclical Treasury & Budget Constraints:** Accumulating sustainable protocol revenues during favorable periods to execute bounded interventions ($0 \le I_t \le \max(0, \text{Treasury}_t - \text{MinimumReserve})$).
4. **Hysteresis & Regime State Machine:** A five-level state machine (*Normal, Accumulation, Stress, Crisis, Recovery*) utilizing separate entry and exit thresholds ($\theta_{high}, \theta_{low}$) to prevent oscillating false-positives.

---

## Repository Structure

* `Countercyclical_DeFi_Control_Framework_Grant_Version_EN` — Comprehensive theoretical and engineering specification document for research and grant submissions.
* `LICENSE` — MIT License governing the software and code implementation.
* `LICENSE-RESEARCH` — Creative Commons Attribution 4.0 International (CC BY 4.0) governing the research documentation and specification.

---

## Experimental Program & Evaluation

The framework proposes a comparative benchmark across five policy configurations:
* **Baseline A:** Static risk parameters.
* **Baseline B:** Utilization-based policy.
* **Policy C:** SSI-based policy without treasury intervention.
* **Policy D:** SSI + treasury + regime switching + hysteresis.
* **Policy E:** Benchmark optimal control policy in simulation.

Evaluation metrics include maximum drawdown, liquidation volume and velocity, liquidity recovery time, insolvency frequency/severity, treasury depletion cost, and the cost per unit of prevented systemic loss.

---

## License

* **Code:** Licensed under the [MIT License](LICENSE).
* **Research & Documentation:** Licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE-RESEARCH).
