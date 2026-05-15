# Double Pendulum ML — Forecasting Chaotic Dynamics
This project explores data‑driven forecasting for the double pendulum, a classical chaotic system.
Using simulated trajectories from the nonlinear ODEs, two modelling approaches are developed:

**I. Full‑state forecasting using all 8 physical coordinates**

**II. Reduced‑order forecasting using the deduced,  most informative observables (𝑥2, 𝑣𝑥2)**

Dimensionality‑reduction and sensitivity analysis guide the choice of reduced coordinates, and LSTM models are evaluated under both full and partial observability.


## Overview
The double pendulum exhibits sensitive dependence on initial conditions, making long‑horizon prediction difficult.
This project examines how sequence models behave under:

full observability (all 8 state variables)

reduced observability (1–2 coordinates)

The goal is to understand what predictive structure remains when only a subset of physically meaningful coordinates is available.

## Key Results
Full‑State Model
Accurate short‑horizon predictions

Divergence over long horizons, consistent with chaotic dynamics

Stable autoregressive rollouts

Reduced‑Order Models
x₂‑only: captures short‑term behaviour, diverges quickly

vₓ₂‑only: weaker performance

[x₂, vₓ₂]:

best reduced‑order performance

slower deviation growth

## Scientific Insight
A minimal pair of physically meaningful coordinates can support non‑trivial forecasting of an 8‑dimensional chaotic system, but long‑horizon divergence is unavoidable due to exponential Lyapunov growth.




retains a meaningful fraction of full‑state accuracy

