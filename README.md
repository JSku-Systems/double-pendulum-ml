# Double Pendulum ML — Forecasting Chaotic Dynamics Under Full and Partial Observability

This repository explores data‑driven forecasting for the double pendulum, a classical chaotic mechanical system.
Two complementary modelling settings are examined:

Full‑state forecasting using all eight physical coordinates

Reduced‑order forecasting using only the most informative observables of the second mass

The project combines simulation, dimensionality reduction, sensitivity analysis, and sequence modelling to study how chaos, partial observability, and physical structure influence forecasting performance.



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

