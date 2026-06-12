# Stochastic Trait Evolution Simulator (Wright-Fisher Model)

A Python framework for simulating allele and trait dynamics in finite populations using the classic Wright-Fisher model. This project uses Monte Carlo simulations to analyze how genetic drift and natural selection interact to determine the probability and time-to-fixation of novel mutations.

## Core Science & Mathematical Model

The Wright-Fisher model describes the stochastic behavior of gene frequencies in an idealized population with non-overlapping generations. Gven a diploid population size of $N$ ($2N$ total alleles) and a trait frequency $p_t$ at generation $t$:

1. **Natural Selection:** The probability $p'$ of selecting a beneficial allele with selection coefficient $s$ is calculated by adjusting its frequency relative to the relative fitness of the population:
   $$p' = \frac{p_t(1 + s)}{1 + s \cdot p_t}$$

2. **Genetic Drift:** The allele count in the next generation ($t+1$) is determined by sampling from a Binomial distribution using the adjusted probability:
   $$X_{t+1} \sim \text{Binomial}(2N, p')$$
   $$p_{t+1} = \frac{X_{t+1}}{2N}$$

The simulation continues until the frequency hits an absorbing state: **Fixation** ($p=1.0$) or **Extinction/Loss** ($p=0.0$).

---

## Project Structure

```text
trait_evolution_sim/
├── README.md               # Project documentation
├── requirements.txt        # Third-party dependencies (numpy, matplotlib)
├── src/
│   ├── __init__.py
│   ├── wright_fisher.py    # Core simulation engine and Markov chain logic
│   └── analytics.py        # Numerical processing of fixation metrics
└── experiments/
    └── run_selection.py    # Execution script for Monte Carlo trials
