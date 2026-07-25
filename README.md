# RegimeShift

Summer of Quant 2026 (Advanced Track)

This project implements a regime-aware portfolio allocation framework using Hidden Markov Models (HMMs) and convex portfolio optimisation. The strategy identifies different market regimes and dynamically adjusts portfolio weights across equity, gold and bonds. The complete pipeline is evaluated using an expanding walk-forward framework with transaction costs and benchmark comparisons.

---

**Name:** Tathagata Roy  <br>
**Roll No.:** 25B3954 <br>

---

## Project Overview

The workflow followed in this project is:

1. Collect historical market data.
2. Engineer market features.
3. Detect market regimes using a Gaussian Hidden Markov Model.
4. Optimise portfolio weights using CVXPY.
5. Evaluate performance using walk-forward validation.
6. Compare against static benchmark portfolios.

---

## Key Design Decisions

### Why three regimes?

Three regimes were chosen to represent the broad phases observed in financial markets:

- Bull
- Bear
- Crisis

Using three regimes provides a simple and interpretable market structure while capturing meaningful differences in market behaviour.

### Why these features?

The HMM is trained using market-level features:

- Daily return
- 5-day momentum
- 21-day momentum
- 63-day momentum
- 20-day rolling volatility
- India VIX

These features capture both market direction and risk, making them suitable for identifying different market environments.

### Why walk-forward validation?

Walk-forward validation avoids look-ahead bias by training the model only on historical data before evaluating it on unseen future periods. This provides a more realistic estimate of strategy performance.

### Why CVXPY?

CVXPY is used to optimise portfolio weights under long-only and fully invested constraints. Separate allocations are learned for different market regimes based only on the training data.

---

## Repository Structure

```
RegimeShift_Portfolio.ipynb     Main project notebook
Performance_Summary.pdf         Project summary
README.md                       Project documentation
```

---

## Requirements

Install the required Python packages before running the notebook.

```bash
pip install numpy pandas matplotlib yfinance scikit-learn hmmlearn cvxpy
```

---

## Running the Project

1. Clone this repository.

```bash
git clone <repository-link>
```

2. Open `RegimeShift_Portfolio.ipynb`.

3. Run all notebook cells from top to bottom.

The notebook downloads historical data automatically and reproduces all figures, portfolio allocations and performance metrics.

---

## Results

The strategy is evaluated using:

- Sharpe Ratio
- Sortino Ratio
- Maximum Drawdown
- Calmar Ratio
- Portfolio Turnover

Performance is compared with:

- Equal Weight Portfolio
- Static 60/40 Portfolio

---

## Future Improvements

Some possible extensions include:

- Alternative market features
- Different numbers of HMM states
- Additional asset classes
- Alternative optimisation objectives
- Rolling parameter tuning
