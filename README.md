# NBA Team Optimization with Genetic Algorithms

Project for the course **Topics in Computational Modelling: from information theory to evolutionary models**.

This repository implements a **Genetic Algorithm** to optimize the selection of an NBA team under a **salary cap constraint**. The objective is to find the best combination of players that maximizes a fitness score derived from performance metrics while staying within budget.

## Problem

Given a dataset of NBA players with attributes such as salary, rating/performance indicators, age, and role, select a team that:

- respects a fixed **salary cap**
- maximizes overall **team fitness/performance**

This is a constrained combinatorial optimization problem with a very large search space, making it a good fit for evolutionary search.

## Data

The project works with a cleaned dataset containing the most relevant features for the optimization, including:

- **Age**
- **Salary**
- **Rating / performance indicators**
- **Role / position**
- **Ranking**

A small exploratory analysis is included to sanity-check distributions and feature usefulness (e.g., how to treat age within the fitness).

## Approach

A Genetic Algorithm (GA) is used to explore candidate teams.

### GA components
- **Encoding**: an individual represents a candidate team (a set of selected players)
- **Fitness function**: scores a team based on aggregated performance metrics, with penalties / rejection when violating the salary cap
- **Selection strategies tested**:
  - Tournament selection
  - Rank selection
  - Roulette wheel selection
  - Stochastic selection
- **Variation operators**:
  - Crossover to combine two teams
  - Mutation to randomly swap/replace players and maintain diversity
- **Replacement**: controlled replacement rate to balance exploration and exploitation

### Hyperparameter tuning
A grid search is used to tune key GA parameters such as:
- population size
- number of generations
- mutation rate
- replacement rate
- tournament size

## Results

The GA successfully identifies high-performing teams within the budget constraint.  
In the final experiments, the best-performing configuration achieved a top fitness score (reported in the notebook conclusions), showing that well-tuned evolutionary search can effectively solve team selection under constraints.
