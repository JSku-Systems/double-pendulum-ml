# Double Pendulum ML : Forecasting Chaotic Dynamics Under Full and Partial Observability

This repository explores data‑driven forecasting for the double pendulum, a classical chaotic mechanical system.
Two complementary modelling settings are examined:

* Full‑state forecasting using all eight physical coordinates

* Reduced‑order forecasting using only the most informative observables of the second mass

The project combines simulation, dimensionality reduction, sensitivity analysis, and sequence modelling to study how chaos, partial observability, and physical structure influence forecasting performance.

## Overview :
The double pendulum is an eight‑dimensional chaotic system with strong sensitivity to initial conditions.
This project investigates:

* how LSTM models behave under full and partial observability

* how dimensionality reduction and predictive sensitivity reveal informative coordinates

* how reduced‑order models compare to full‑state baselines

* how physics‑informed losses influence long‑horizon stability

The two notebooks form a coherent pipeline:

**Notebook 1**: full‑state forecasting using a baseline model and physics informed model

**Notebook 2**: reduced‑order forecasting and coordinate selection <br>


## Notebook 1 : Full‑State Forecasting 

### Dataset 
* 20 simulated trajectories

* Approximately 9020 samples

* 8‑dimensional state: (𝑥1,𝑦1,𝑥2,𝑦2,𝑣𝑥1,𝑣𝑦1,𝑣𝑥2,𝑣𝑦2)

* Chronological 80/10/10 train/val/test split

* Max‑value normalisation

### Baseline Model :

* Single‑layer LSTM

* Dense output layer predicting the next 8‑D state

* 50‑step input window

* Early stopping, no shuffling

#### Short‑horizon (20‑step) behaviour

* Tracks true motion well

* Divergence remains modest

* Errors grow gradually, consistent with early‑stage chaotic amplification

#### Long‑horizon (100‑step) behaviour

* Rapid divergence once autoregressive errors accumulate

* Loss of physical plausibility

* Deviation curves show exponential‑like error growth

### Physics‑Informed Model : 

* Adds an energy‑based penalty term

* Scale‑matched weighting (λ ≈ 10⁻³–10⁻⁴)

* Similar architecture as baseline

#### Short‑horizon (20 step) behaviour

* Preserves oscillatory structure

* Exhibits a consistent positional offset

* More structurally coherent than the baseline

#### Long‑horizon (100 step) behaviour

* Retains oscillatory geometry longer

* Diverges under chaos but collapses more gracefully

* Vertical coordinates show largest deviations

### Notebook 1 Summary

**Baseline:** accurate short‑term, unstable long‑term

**Physics‑informed:** less precise locally, more stable structurally

**Both:** diverge eventually due to chaotic amplification <br>


## Notebook 2 : Reduced‑Order Forecasting

### Dimensionality‑Reduction & Sensitivity Analysis:

To identify informative coordinates, the full dataset is analysed using:

* PCA — variance structure and principal‑axis loadings

* t‑SNE / UMAP — nonlinear state‑space geometry and regime separation

* Predictive sensitivity; one‑step regression errors for each coordinate

* Across all methods, x₂ and vₓ₂ consistently emerge as the most informative observables.


### Reduced‑Order Models :

Three LSTM models are trained to forecast the full 8‑D state using:

* x₂ only

* vₓ₂ only

* [x₂ , vₓ₂]  (2‑D reduced state)

All models use the same:

* scaling

* train/val/test split

* architecture

* early stopping

* 20‑step and 100‑step rollouts

#### Short‑Horizon (20 steps) behaviour

* x₂‑only: captures short‑term structure, diverges moderately

* vₓ₂‑only: weaker performance, consistent with sensitivity ranking

* [x₂,vₓ₂]: most stable, lowest deviation growth


#### Long‑Horizon (100 steps) behaviour

* All models diverge due to partial observability

* [x₂,vₓ₂] retains coherent structure longest

* Errors accumulate smoothly and plausibly

  

### Notebook 2 Summary

* A minimal pair of coordinates can support meaningful short‑term forecasting

* Partial observability imposes strict limits on long‑range prediction

* Reduced‑order models reveal how much structure is retained in a small set of observables <br>



## Key Insights:
* Chaotic systems allow accurate short‑term but not long‑term prediction

* Physics‑informed losses improve structural stability

* Data‑driven analyses (PCA, t‑SNE, UMAP, sensitivity) identify informative coordinates

* Reduced‑order models using [x₂,vₓ₂] recover a substantial fraction of full‑state performance

* Partial observability leads to smooth, physically plausible divergence rather than numerical instability


## Running the Project: 

git clone https://github.com/JSku-Systems/double-pendulum-ml.git

cd double-pendulum-ml

pip install -r requirements.txt

Run the notebooks in order:

01_full_state_forecasting.ipynb

02_reduced_order_forecasting.ipynb

Both notebooks generate their own simulation data; you may run the notebooks locally or in cloud environments.


## Future Work: 

* Physics‑informed reduced‑order models

* Transformer‑based sequence models

* Lyapunov exponent estimation


## License: 
Released under the MIT License
retains a meaningful fraction of full‑state accuracy

