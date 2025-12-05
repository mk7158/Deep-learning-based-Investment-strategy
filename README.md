# Deep Learning Time Series Momentum (LSTM-TSMOM)

This project implements and compares traditional **Time Series Momentum (TSMOM)** strategies against **Deep Learning (LSTM)** based trading strategies.

The project utilizes various Long Short-Term Memory (LSTM) architectures—including **Attention mechanisms** and **Multi-task learning**—to predict the direction of asset returns and construct a diversified, volatility-scaled portfolio across multiple asset classes (Equities, Bonds, Commodities, and Currencies).

## Key Features

* **Baseline Strategy:** Implementation of a standard TSMOM strategy using 12-month price momentum and inverse volatility scaling.
* **Deep Learning Models:**
    * **Vanilla LSTM:** Standard recurrent neural network for time-series forecasting.
    * **Multi-Task LSTM:** Neural network designed to predict returns for all assets simultaneously, capturing cross-asset dependencies.
    * **Bidirectional LSTM:** Processes time-series data in both forward and backward directions to capture fuller context.
    * **Attention LSTM:** Adds a custom Attention Layer to weigh specific time steps in the lookback window (e.g., focusing on specific past months).
* **Robust Backtesting:**
    * **Walk-Forward Validation:** Simulates real-world trading by retraining models on expanding windows to prevent look-ahead bias.
    * **Volatility Scaling:** Portfolios are scaled to a target volatility (default: 10% annualized).
    * **Transaction Costs:** Accounts for trading costs (default: 5bps) to calculate realistic net returns.
* **Performance Metrics:** Automatically calculates Sharpe Ratio, Calmar Ratio, Max Drawdown, and Annualized Returns.

## Data Requirements

The project expects CSV files containing historical price data in the root directory. The script looks for files using the naming convention `{ticker}_us_m.csv` or `{ticker}.csv`.

**Asset Universe:**
* **Equities:** `^SPX` (S&P 500), `EEM` (Emerging Markets), `IWM` (Russell 2000)
* **Fixed Income:** `IEF` (7-10 Yr Treasury), `TLT` (20+ Yr Treasury), `SHY` (1-3 Yr Treasury), `TIP` (TIPS), `LQD` (Corp Bonds), `HYG` (High Yield)
* **Currencies:** `UUP` (US Dollar), `FXE` (Euro)
* **Commodities/Real Estate:** `GLD` (Gold), `SLV` (Silver), `USO` (Oil), `VNQ` (Real Estate)
