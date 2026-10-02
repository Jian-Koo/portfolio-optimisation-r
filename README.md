# Portfolio Optimisation and Risk Analysis

A quantitative portfolio-construction case study in R, combining risk-return analysis, diversification, constrained optimisation and out-of-sample validation.

## Overview

This project develops an investment strategy for John and Mary Davis, a hypothetical recently retired couple with a combined investment portfolio of $1.5 million.

The clients have different attitudes towards risk. John prioritises capital preservation and seeks to minimise portfolio volatility, while Mary is willing to accept greater risk in pursuit of stronger long-term growth.

The analysis translates these competing preferences into two quantitative portfolio objectives, constructs optimised portfolios using historical equity data, and evaluates their behaviour using an out-of-sample validation period. A blended portfolio is then proposed as a practical compromise between the two objectives.

## Data and Analysis

The analysis considers ten equities:

`AMT`, `AXP`, `BRK-B`, `C`, `ELA`, `EOG`, `MA`, `MS`, `NFLX`, `REGN`

Monthly adjusted closing prices are retrieved using `tidyquant`.

- **Estimation period:** January 2015 – December 2024
- **Validation period:** January 2025 – December 2025
- **Portfolio value:** $1.5 million
- **Short selling:** Not permitted
- **Maximum allocation per stock:** 40%

The workflow covers:

- historical price retrieval and return calculation;
- data-quality and completeness checks;
- return, variance and volatility estimation;
- 95% confidence intervals for expected returns;
- risk-adjusted stock ranking;
- correlation and diversification analysis;
- selection of five assets for portfolio construction;
- minimum-variance optimisation for the conservative strategy;
- mean-variance optimisation for the growth-oriented strategy;
- constrained quadratic programming using `quadprog`;
- construction of a blended portfolio;
- out-of-sample performance validation; and
- statistical testing of portfolio returns.

## Portfolio Strategies

### Conservative Portfolio

John's portfolio prioritises capital preservation and is constructed by minimising portfolio variance subject to the allocation constraints.

### Growth-Oriented Portfolio

Mary's portfolio uses a mean-variance objective that places greater emphasis on expected return while retaining a penalty for portfolio risk.

A risk-aversion coefficient of **α = 0.25** is used for the growth-oriented strategy.

### Blended Portfolio

The final strategy combines:

- **55% Conservative Portfolio**
- **45% Growth-Oriented Portfolio**

The resulting allocation is:

| Asset | Weight |
|---|---:|
| Mastercard (MA) | 40.0% |
| Netflix (NFLX) | 22.2% |
| Berkshire Hathaway (BRK-B) | 22.0% |
| Morgan Stanley (MS) | 12.1% |
| American Express (AXP) | 3.7% |

## Key Findings

The five selected equities were **MA, NFLX, BRK-B, MS and AXP**.

An equally weighted portfolio of these five stocks produced monthly volatility of **5.95%**, compared with an average individual-stock volatility of **7.95%**, illustrating the diversification benefit of combining imperfectly correlated assets.

During the 2025 validation period:

| Portfolio | Average Monthly Return | Monthly Volatility |
|---|---:|---:|
| Conservative | 1.17% | 3.18% |
| Growth-Oriented | 1.40% | 5.22% |
| Blended | 1.28% | 3.71% |

The validation results reflected the intended trade-off: the conservative strategy exhibited lower volatility, while the growth-oriented strategy achieved a higher average return with greater risk. The blended portfolio remained between the two strategies on both measures.

## Repository Structure

```text
portfolio-optimisation-r/
├── README.md
├── .gitignore
├── src/
│   └── portfolio_analysis.Rmd
└── reports/
    ├── investment_strategy_report.pdf
    └── portfolio_analysis.pdf
