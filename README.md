# Travelling Salesman Problem (TSP): Implementation & Time Analysis

A Jupyter notebook implementing and comparing three approaches to the **Travelling Salesman Problem** in Python: find the shortest tour that visits every city exactly once and returns to the start.

## Algorithms
- **Brute Force** — tries every ordering of cities, `O(n!)`
- **Held-Karp Dynamic Programming** — exact solution over subsets of cities (bitmasks), `O(n² · 2ⁿ)`
- **Nearest Neighbor heuristic** — fast, approximate, `O(n²)`
- **2-opt improvement** — repairs a heuristic tour by reversing segments

## Features
- Interactive user input for a custom distance matrix (`rows separated by ;, values by ,`)
- Real runtime measurement using Python's `time` module
- Time and space complexity analysis for every algorithm
- Tour reconstruction (the actual route, not just its length)
- Map visualization of the tours found by Nearest Neighbor, Nearest Neighbor + 2-opt, and the optimal tour
- Optimality-gap study over 30 random 10-city instances, with a histogram
- Runtime comparison chart (log scale) from 4 to 15 cities, cross-checking that the exact methods agree

## Getting Started
1. Clone the repo
2. Install dependencies: `pip install jupyter matplotlib`
3. Open `tsp_analysis.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab
4. Run the cells top to bottom — the demo cell uses a classic 4-city matrix by default; swap in `get_user_matrix()` (no arguments) to enter your own

## Complexity Summary

| Algorithm                  | Time Complexity | Space Complexity | Optimal? | Practical Limit (pure Python) |
|------------------------------|-------------------|---------------------|-----------|----------------------------------|
| Brute Force                  | O(n!)             | O(n)                | Yes       | about 10 cities                  |
| Held-Karp (DP)               | O(n² · 2ⁿ)        | O(n · 2ⁿ)           | Yes       | about 15-20 cities               |
| Nearest Neighbor             | O(n²)             | O(n)                | No        | thousands of cities              |
| Nearest Neighbor + 2-opt     | O(n²) per pass    | O(n)                | No        | hundreds to thousands of cities  |

Where `n` = number of cities.

TSP is **NP-hard**. Held-Karp tames the factorial search by remembering the best cost for each *(set of visited cities, current city)* pair, but it is still exponential. In the notebook's experiment on random 10-city instances, Nearest Neighbor averaged about 12% above optimal, and adding 2-opt brought the average gap down to under 1%.

## License
MIT
