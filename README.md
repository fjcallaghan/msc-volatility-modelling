# Volatility Modelling in Continuous Time

Heston and Dupire volatility modelling in Python — building, calibrating and stress-testing option pricing models end to end.

## About

This was completed as coursework for **Advanced Techniques for Finance**, a module on my MSc, and was awarded a mark of **86%**. The project was accompanied by a written report containing the theoretical exposition and analysis of results.

This repository contains the Jupyter notebook I wrote to complete the tasks, generate the figures and produce the numerical results that the report is built on.

All cell outputs (including plots) are embedded in the notebook, so it can be read in full directly on GitHub.

## What the notebook does

The notebook works through a six-stage pipeline:

1. **Heston model setup, simulation and validation** — simulate asset paths under the Heston stochastic volatility model and validate Monte Carlo prices against QuantLib's semi-analytic Heston pricer.
2. **European call price surface** — build a 50×50 grid of call prices across strikes and maturities.
3. **Implied volatility surface** — invert the price surface through Black–Scholes to recover the implied volatility surface.
4. **Dupire local volatility** — construct the Dupire local volatility surface from the price surface and use it to price an off-grid option.
5. **Re-pricing without recalibration** — re-price the same option along simulated paths without recalibrating the Dupire surface, examining how the local vol model degrades as the market moves.
6. **Blind Heston calibration** — calibrate a Heston model to a noisy price surface with no knowledge of the true parameters, and compare the recovered dynamics against the originals.

## Tools used

- **Python** with **NumPy** and **SciPy** for the numerical work
- **QuantLib** for semi-analytic Heston pricing and calibration utilities
- **Matplotlib** for the surface and diagnostic plots

## Running it yourself

```bash
pip install numpy scipy matplotlib QuantLib
jupyter notebook OptionC_Volatility_Modelling.ipynb
```

The notebook is self-contained and runs top to bottom.
