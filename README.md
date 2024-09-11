# Pair Trading Strategy

This project implements a pair trading strategy using two stocks to exploit price divergences. The strategy uses statistical measures like z-score and moving averages to identify trading opportunities between two correlated assets. The goal is to capitalize on the mean-reverting behavior of asset prices when the ratio between them deviates from the historical average.

## Features

- **Rolling Mean and Standard Deviation:** Calculates the moving averages and standard deviation for the price ratio between two assets.
- **Z-Score Calculation:** Measures how far the current price ratio is from the historical mean.
- **Buy/Sell Signal Generation:**
  - Buy long positions when the price ratio is below a certain threshold (z-score > 1).
  - Sell short positions when the price ratio is above a certain threshold (z-score < -1).
  - Clear positions when the price ratio moves back toward the mean (z-score between -0.75 and 0.75).
- **Profit Calculation:** Tracks cumulative profit from trading activity.
- **Percentage Return Calculation:** Computes percentage return based on the initial investment.

## Getting Started

### Prerequisites

To run the project, you will need:

- Python 3.x
- Pandas (for data manipulation)
- Numpy (for numerical calculations)
- Matplotlib (for plotting, if you wish to visualize results)

### Installing Dependencies

You can install the required dependencies by running the appropriate pip commands for pandas, numpy, and matplotlib.

### Data

You will need price data for two stocks to run the pair trading strategy. This data can be fetched using APIs such as Yahoo Finance or from CSV files containing historical stock prices. Ensure that the two stocks are relatively correlated for the strategy to work effectively.

## Files

- `pair-trading-strategy.ipynb`: The Jupyter notebook that contains the pair trading logic and simulation.
- `README.md`: This file.

## Strategy Logic

The strategy uses a rolling window approach to compute the ratio between two asset prices. It then calculates the z-score of the ratio, which tells how far the current ratio is from its historical mean. The z-score is used to trigger buy or sell signals:

- **Sell Short:** When the z-score is less than -1, the strategy sells the first asset and buys the second asset, expecting the ratio to increase.
- **Buy Long:** When the z-score is greater than 1, the strategy buys the first asset and sells the second, expecting the ratio to decrease.
- **Exit Positions:** When the z-score is between -0.75 and 0.75, the strategy exits all open positions.
