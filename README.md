[README.md](https://github.com/user-attachments/files/33080251/README.md)
# Diagnosing a Flawed Risk Model — VaR, Expected Shortfall & Monte Carlo

## Objective

I examined how distribution assumptions affect portfolio risk estimates and tested ways to improve simulation accuracy and verify model results.

## Methodology

- I compared the analyst's normal-distribution VaR with historical return quantiles.
- I calculated VaR and Expected Shortfall using historical, normal and fitted Student-t methods.
- I compared naive Monte Carlo option pricing with antithetic variates.
- I used `risk_metrics.py` and ran its module tests and self-tests.
- I revised an AI prompt to clarify the backtest's units and checked its results against my own breach counts.

## Key Findings

At 99% confidence, the normal model understated historical VaR by **12.7%**, or **$40,393** on the **$10M portfolio**. However, at 95%, it overstated historical VaR by **3.5%**, showing that the direction of the error depends on the confidence level.

The fitted Student-t had **4.58 degrees of freedom**. Expected Shortfall exceeded VaR for every method, with Student-t producing the highest ES at **$426,060**.

Antithetic variates reduced Monte Carlo standard error by a factor of **1.26x**. All module tests and self-tests passed.

My backtest matched the manual counts: normal 99% VaR was breached on **1.71%** of days, compared with **1.03%** for historical VaR. This supported my diagnosis that the normal model underestimated extreme losses.
