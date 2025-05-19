# Brownian Motion and Geometric Brownian Motion Simulation in Python

A Python implementation for simulating and visualizing Brownian Motion (BM) and Geometric Brownian Motion (GBM), foundational models in financial mathematics and quantitative finance.

![Sample GBM Paths](https://i.imgur.com/your-plot-image-placeholder.png)
*(Replace the above image URL with an actual screenshot of your GBM plot if you upload one, e.g., to imgur.com or directly to your GitHub repo)*

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Models Implemented](#models-implemented)
  - [Brownian Motion (BM)](#brownian-motion-bm)
  - [Geometric Brownian Motion (GBM)](#geometric-brownian-motion-gbm)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
  - [Local Execution](#local-execution)
  - [Google Colab](#google-colab)
- [Code Structure](#code-structure)
- [Understanding the Models](#understanding-the-models)
- [Applications in Finance](#applications-in-finance)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [License](#license)
## Overview

This project provides Python scripts to generate and visualize paths for:
1.  **Brownian Motion (Wiener Process):** A continuous-time stochastic process representing a random walk.
2.  **Geometric Brownian Motion:** A continuous-time stochastic process where the logarithm of the randomly varying quantity follows a Brownian motion with drift. It's widely used to model stock prices and other financial assets because it ensures prices remain non-negative.

The simulations are useful for educational purposes, financial modeling, option pricing (e.g., Monte Carlo methods), and risk management simulations.

## Features

-   **Brownian Motion (BM) Simulation:**
    -   Generates one or multiple BM paths.
    -   Customizable time horizon (`T`), number of steps (`N`), and number of paths.
    -   Option to set a random seed for reproducibility.
-   **Geometric Brownian Motion (GBM) Simulation:**
    -   Generates one or multiple GBM paths for asset prices.
    -   Customizable initial price (`S0`), drift (`mu`), volatility (`sigma`), time horizon (`T`), number of steps (`N`), and number of paths.
    -   Option to set a random seed for reproducibility.
-   **Visualization:**
    -   Plots the generated paths using `matplotlib` for easy interpretation.
-   **Educational:**
    -   Clear, commented code to understand the implementation details.
    -   Plain-language documentation explaining the models and their limitations.
## Models Implemented

### Brownian Motion (BM)
A standard Brownian Motion `W(t)` is characterized by:
1.  `W(0) = 0`
2.  `W(t)` has independent increments: `W(t) - W(s)` is independent of the past for `s < t`.
3.  `W(t) - W(s)` is normally distributed with mean 0 and variance `t-s`.
    -   So, `dW_t = W(t+dt) - W(t) ~ N(0, dt)`, which implies `dW_t = Z * sqrt(dt)` where `Z ~ N(0,1)`.

### Geometric Brownian Motion (GBM)
The Stochastic Differential Equation (SDE) for an asset price `S(t)` following GBM is:
`dS_t = Î¼ * S_t * dt + Ïƒ * S_t * dW_t`
Where:
-   `Î¼` (mu) is the drift coefficient (expected rate of return).
-   `Ïƒ` (sigma) is the volatility coefficient.
-   `dW_t` is the increment of a Wiener process.

The discrete-time solution used for simulation is:
`S_{t+dt} = S_t * exp( (Î¼ - ÏƒÂ²/2) * dt + Ïƒ * sqrt(dt) * Z )`
Where `Z ~ N(0,1)`.

## Requirements

-   Python 3.x
-   NumPy: `pip install numpy`
-   Matplotlib: `pip install matplotlib`

## How to Run

### Local Execution
1.  **Clone the repository or download the Python script** (e.g., `gbm_simulator.py`).
    ```bash
    git clone https://github.com/yourusername/your-repo-name.git
    cd your-repo-name
    ```
2.  **Ensure you have the required libraries installed:**
    ```bash
    pip install numpy matplotlib
    ```
3.  **Run the Python script:**
    ```bash
    python gbm_simulator.py
    ```
    This will execute the script, generate the simulations, print some information to the console, and display the plots.

### Google Colab
1.  Open a new Google Colab notebook.
2.  Copy the entire content of the Python script (`.py` file).
3.  Paste it into a single code cell in the Colab notebook.
4.  Run the cell (click the play button or press `Shift + Enter`).
    The plots will be displayed directly within the Colab notebook.

## Code Structure

The main Python script (`gbm_simulator.py` or similar) typically contains:
-   **`generate_brownian_motion(T, N, num_paths, seed)`:** Function to generate BM paths.
-   **`generate_gbm(S0, mu, sigma, T, N, num_paths, seed)`:** Function to generate GBM paths.
-   **Main execution block (`if __name__ == "__main__":`)**:
    -   Sets parameters for BM and GBM simulations.
    -   Calls the generation functions.
    -   Uses `matplotlib.pyplot` to plot the results.
    -   Prints relevant information and a summary of applications/limitations.

## Understanding the Models

-   **Brownian Motion (BM):** Represents a pure random walk. Its value can go positive or negative, and future steps are entirely independent of past ones, given the present value.
-   **Geometric Brownian Motion (GBM):** Models percentage changes as random. This ensures that if a price starts positive, it remains positive. It's characterized by an average growth rate (drift) and a level of randomness (volatility).

## Applications in Finance

-   **Option Pricing:** GBM is a core component of the Black-Scholes model and is widely used in Monte Carlo simulations for pricing exotic options.
-   **Risk Management:** Simulating thousands of GBM paths helps in estimating Value at Risk (VaR) and Conditional Value at Risk (CVaR).
-   **Algorithmic Trading:** Used to generate synthetic market data for backtesting trading strategies under different market scenarios.
-   **Portfolio Simulation:** Can be extended to simulate multiple correlated assets.
