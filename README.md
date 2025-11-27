
# Evolutionary Optimization for Solving the N-Queens Problem

This project investigates how evolutionary algorithms can be used to efficiently solve the N-Queens problem by exploring and evaluating a wide range of genetic operators, parameter configurations, and adaptive evolutionary strategies. The work was conducted as part of the Artificial Intelligence course at Jönköping University and is based on a comprehensive comparative study of algorithmic performance.

---

## Overview

The N-Queens problem requires placing N queens on an N×N chessboard such that none threaten each other. While small instances can be solved through brute force or backtracking, larger boards quickly become computationally expensive, making heuristic and population-based approaches ideal candidates.

This project applies a Genetic Algorithm (GA) to the reduced N! search space (one queen per column) and systematically explores:

- Multiple recombination operators  
- Multiple mutation strategies  
- Dynamic vs. static parameter schedules  
- Survival-selection weighting  
- Genocide-based stagnation recovery  
- Sampling methods for parameter tuning  
- A total of **500 unique GA configurations** were evaluated, each tested over **100 randomized initial populations**, to identify the strongest operator combinations and parameter values.
  
---

## Core Concepts

### **Genetic Representation**
Boards are represented as permutations of length N, ensuring no row or column conflicts. Remaining conflicts (diagonal threats) are evaluated through a normalized fitness function.

### **Operators Evaluated**
The project benchmarks a wide range of operators, including:

**Recombination**  
- Partially Mapped Crossover (PMX)  
- PMX with duplication removal  
- Ordered Crossover (OX)  
- One-point, Two-point, and Even-Cut-and-Crossfill  

**Mutation**  
- Swap  
- Inversion  
- Scramble  
- Creep  
- Duplicate Replacement  

**Selection**  
- Tournament-based parent selection  
- Probabilistic survival selection with adjustable weighting  

**Additional Strategies**  
- Dynamic mutation & recombination rates  
- Genocide mechanism to escape stagnation  
- Latin Hypercube Sampling for parameter search  

---

## Key Findings

### **1. PMX + Duplicate Removal was the strongest recombination strategy**  
Consistently produced the shortest convergence times and lowest evaluation counts.

### **2. Duplicate Replacement excelled as a mutation strategy**  
Particularly useful for restoring valid permutations and reducing horizontal conflicts.

### **3. Dynamic parameter schedules offered limited gains**  
Adjusting mutation and recombination rates each generation did not meaningfully outperform static configurations.

### **4. Genocide significantly improved performance**  
Replacing a fraction of the population upon stagnation prevented the search from getting trapped in local minima, especially for smaller N. 

### **5. The enhanced GA vastly outperformed the baseline**  
- **Up to 30% fewer evaluations**  
- **Up to 99.8% faster execution**, especially at higher N values (e.g., N=12)  

---

## Experimental Approach

- Over **500 configurations** generated via Latin Hypercube Sampling  
- Each configuration evaluated over **100 randomized initial populations**  
- Additional cross-dimensional experiments conducted for N = 6, 8, 10, 11, 13, 14  
- Performance measured using evaluation count, time per run, and convergence reliability  
- Stochastic behaviours analyzed via visualization of operator distributions and sampling patterns  

This thorough investigation yielded a well-balanced, robust evolutionary algorithm tuned specifically for the N-Queens problem.

---

## Final Outcome

The resulting evolutionary algorithm is:

- **More efficient**  
- **More stable**  
- **Better at avoiding local minima**  
- **Significantly faster than the baseline implementation**  

Its design incorporates the best-performing genetic operators and parameter choices discovered through extensive experimentation.

---

## Future Work

The report outlines several promising directions for continued research:  
- Exploring additional genetic operators and hybrid strategies  
- Dynamic operator selection based on population state  
- Introducing evolutionary aging to balance exploration and exploitation  
- Evaluating performance across much larger N values  
- Broadening comparison against other evolutionary or heuristic approaches  

---

### Prerequisites

Make sure you have Python and pip installed on your machine.

1.  **Install Python**
    
    *   **Windows**: Download the installer from the [official Python website](https://www.python.org/downloads/windows/) and run it. Make sure to check the box that says "Add Python to PATH" during installation.
    *   **macOS**: You can use Homebrew to install Python. Open your terminal and run:
        
        ```bash
        brew install python
        ```
    *   **Linux**: Use your package manager to install Python. For example, on Ubuntu, run:
        
        ```bash
        sudo apt update
        sudo apt install python3 python3-pip
        ```
        
2.  **Verify the installation**
    
    After installation, verify that Python and pip are installed correctly by running the following commands in your terminal or command prompt:
    
    ```bash
    python --version
    pip --version
    ```
    
3.  **Clone the repository**
    
    ```bash
    git clone https://github.com/mosmar99/Evolutionary_Computation_HT2024.git
    cd Evolutionary_Computation_HT2024
    ```

4.  **Create a virtual environment (optional but recommended)**
    
    ```bash
    python -m venv venv
    # Activate the virtual environment
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```
    
5.  **Install dependencies**
    
    ```bash
    pip install -r requirements.txt
    ```

### Usage
You can view the sample logs found in the **`sample logs`** sub folder, these can be visualized by running (warning this will open 5 windows):
```bash
    python parts/visuals.py
```
You can generate your own logs by running the different main files found in the **`parts`** sub folder. Below are the available main files and their respective functions, visuals will be stored in **`logs`** subfolder:

- **`main_final.py`**: Runs the the best version of the genetic algorithm, and visualises the results as a lineplot.
- **`main_basic.py`**: The most basic setup of our genetic algorithm, no visuals besides prints to the terminal.
- **`main_setup_comparison_bar_chart.py`**: Caution!, this will run multiple setups at all available cores on your pc. Will store the setups in **`LHS_Setups.log`**, will store the evalutations of the setups in **`LHS_Setups_evals.log`**
- **`main_setup_comparison_density_heatmap.py`**: Caution!, this will run multiple setups at all available cores on your pc. Will store the setups in **`test_setups.log`**, will store the evalutations of the setups in **`test_results.log`**
- **`main_stagnation_mean_vs_max.py`**: This file compares the genetic algorithm with regards to average / mean fitness score and maximum fitness score. creates a two-column lineplot visualisation of the results. Stores the data in **`max_vs_mean_geno.log`**
- **`main_static_vs_dynamic_stagnation.py`**: compares the static and dynamic stagnation handling, visualizes the results as a two-column lineplot. Stores the data in **`dyn_vs_static_stagn.log`**
- **`main_with_and_without_genocide(static).py`**: used to run the Genetic Algorithm with and without genocide, and create a two-column lineplot, Stores the data in **`geno_plot8.log`**
- **`main_with_static_genocide_comparing_dynamic_vs_static_mutation_and_recombination_rates.py`**: Runs the genetic algorithm, with static genocide and compares the algorithm with regards to dynamic vs static mutation and recombination rates. Visualizes the results in a lineplot. Stores the data in  **`dynamic_vs_static.log`**


You can visualize the logs directly by running the following command, Caution this will open 7 windows.:

```bash
python parts/visualise.py
```

## Contributors

Mahmut Osmanovic  
Isac Paulsson  
Sebastian Tuura  
Mohamed Al Khaled  
Emil Wagman  
