# Genetic Algorithm for Preference Based Matching

A Python implementation of a genetic algorithm for solving a preference-based matching optimization problem.

The goal is to find high quality one to one matches between two groups of participants based on their ranked preferences. 
Each participant ranks the members of the opposite group, and the algorithm searches for a matching that maximizes the overall satisfaction of both sides.

## What is a Genetic Algorithm?

A genetic algorithm is an optimization technique inspired by the process of natural evolution, where fitter individuals are more likely to survive and pass their characteristics to the next generation.

Similarly, a genetic algorithm starts with a population of candidate solutions and improves them over multiple generations using selection, crossover, and mutation.

In this project, each candidate solution represents one complete matching between all participants in the two groups. Therefore, the population is a collection of different possible complete matchings.

Over multiple generations, higher quality matchings are more likely to be selected and combined to create new solutions, while mutations introduce additional variation. This process allows the algorithm to gradually search for better matching solutions.

## Overview

The project uses a genetic algorithm to iteratively improve candidate matchings.

The algorithm follows the main stages of a genetic algorithm:

1. Generate an initial population of random valid matchings
2. Evaluate each solution using a fitness function
3. Select high quality solutions
4. Generate new solutions using crossover
5. Apply mutations to maintain population diversity
6. Validate and repair invalid matchings
7. Repeat until convergence or the maximum number of generations is reached

## Fitness Function

Each matching is evaluated according to the ranked preferences of both participants in every pair.

For each pair, a score is calculated for both participants based on the position of their assigned partner in their preference list. These scores are combined to evaluate the overall quality of the matching.

This allows the algorithm to consider the preferences of both sides rather than optimizing for only one group.

## Genetic Operators

### Selection & Elitism

The highest scoring solutions are preserved for the next generation. Higher quality solutions are also more likely to be selected as parents for crossover.

### Crossover

Two parent matchings are selected and combined using a randomly generated crossover point to create new candidate solutions.

### Mutation

Individual matches can be randomly modified according to a mutation probability, introducing new combinations and maintaining diversity in the population.

### Validation

Since crossover and mutation can produce invalid matchings, each generated solution is validated and repaired when necessary to ensure a valid one to one matching.

## Handling Premature Convergence

The algorithm includes mechanisms for detecting premature convergence or a possible local optimum.

It monitors the diversity of fitness scores in the population and checks whether the best fitness score remains unchanged for several generations.

If the population appears to be stuck before reaching a sufficiently high fitness score, mutation is applied more broadly while preserving the best solution found so far.

## Parameters

The main parameters used in the implementation are:

- Participants in each group: `30`
- Population size: `100`
- Maximum generations: `180`
- Mutation rate: `0.05`
- Elitism(Selection) rate: `0.20`
- Plateau detection: `10` generations

## Input Data

The input file contains the ranked preferences of all participants.

- The first 30 lines represent the men's preferences.
- The next 30 lines represent the women's preferences.
- Each line contains a ranking of all 30 participants from the opposite group, ordered from most to least preferred.

## Results

Different combinations of population size and maximum number of generations were tested to compare solution quality and computational cost.

The program also visualizes the maximum, average, and minimum fitness values throughout the generations and indicates additional mutation rounds used to escape local optima.

## Project Files

- `main.py` – implementation of the genetic algorithm
- `GA_input.txt` – participant preference data
- `Genetic_Algorithm_Matchmaking_Report.pdf` – detailed project report, algorithm explanation, and experimental results

## Technologies

- Python
- NumPy
- Matplotlib

## Running the Project

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Make sure `GA_input.txt` is located in the same directory as `main.py`.

```bash
python main.py
```

The program runs the genetic algorithm, displays the fitness progression across generations, and outputs the final matching and its fitness score.
