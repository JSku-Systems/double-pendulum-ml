# Double Pendulum ML : Forecasting Chaotic Dynamics Under Full and Partial Observability

This repository explores data‑driven forecasting for the double pendulum, a classical chaotic mechanical system.
Two complementary modelling settings are examined:

Full‑state forecasting using all eight physical coordinates

Reduced‑order forecasting using only the most informative observables of the second mass

The project combines simulation, dimensionality reduction, sensitivity analysis, and sequence modelling to study how chaos, partial observability, and physical structure influence forecasting performance.

## Overview
The double pendulum is an eight‑dimensional chaotic system with strong sensitivity to initial conditions.
This project investigates:

* how LSTM models behave under full and partial observability

* how dimensionality reduction and predictive sensitivity reveal informative coordinates

* how reduced‑order models compare to full‑state baselines

* how physics‑informed losses influence long‑horizon stability

The two notebooks form a coherent pipeline:

**Notebook 1**: full‑state forecasting using a baseline model and physics informed model

**Notebook 2**: reduced‑order forecasting and coordinate selection


## Notebook 1 : Full‑State Forecasting Dataset
* 20 simulated trajectories

* Approximately 9020 samples

* 8‑dimensional state: (𝑥1,𝑦1,𝑥2,𝑦2,𝑣𝑥1,𝑣𝑦1,𝑣𝑥2,𝑣𝑦2)

* Chronological 80/10/10 train/val/test split

* Max‑value normalisation

Baseline Model
Single‑layer LSTM

Dense output layer predicting the next 8‑D state

50‑step input window

Early stopping, no shuffling

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

