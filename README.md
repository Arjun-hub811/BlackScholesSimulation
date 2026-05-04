# BlackScholesSimulation
Black-Scholes Simulation Suite (Java)
A comprehensive, menu-driven Black-Scholes option pricing simulator written in Java. This project provides analytic pricing, Monte Carlo simulation, implied volatility solving, Greeks computation, and batch CSV processing — all from an interactive command-line interface.

#Features
Analytic Black-Scholes Pricing — Closed-form option pricing for European calls/puts, binary calls, and digital puts
Monte Carlo Simulation — Standard and antithetic variate methods with configurable simulation count and seed
Multithreaded Monte Carlo — Parallel simulation across multiple threads for faster computation
Implied Volatility Solver — Iterative solver to recover implied vol from a market price
Greeks Calculation — Delta, Gamma, Vega, Theta, and Rho for any supported option type
Batch CSV Processing — Read option contracts from CSV, price them, and export results
ASCII Histogram — Visualize Monte Carlo terminal price distributions in the terminal
Session Logging & History — Persistent logging to file with session history tracking
CSV Validation & Repair — Validate input CSV files and auto-repair malformed rows
Self-Test Demo — Built-in sanity checks to verify engine correctness
Supported Option Types
Type	Description
EUROPEAN_CALL	Standard European call option
EUROPEAN_PUT	Standard European put option
BINARY_CALL	Binary (cash-or-nothing) call option
DIGITAL_PUT	Digital (cash-or-nothing) put option
Project Structure
BlackScholesSimulation-Java/
├── MainSimulation.java          # Main menu-driven application (default package)
├── bs/
│   ├── BlackScholesEngine.java  # Core pricing engine (analytic, MC, implied vol, Greeks)
│   └── OptionType.java          # Enum for supported option types
├── options.csv                  # Sample input CSV for batch pricing
├── options_example.csv          # Example CSV template
├── bs_sim_log.txt               # Simulation log output
└── bs_session_history.txt       # Session history log
Prerequisites
Java 17+ (uses switch expressions and other modern Java features)
Getting Started
Compile
javac bs/OptionType.java bs/BlackScholesEngine.java MainSimulation.java
Run
java MainSimulation
You will be presented with an interactive menu:

--- MAIN MENU ---
1)  Analytic Black-Scholes price
2)  Monte Carlo pricing (standard/antithetic)
3)  Implied volatility (Black-Scholes)
4)  Batch CSV: read options.csv -> results.csv
5)  Save example CSV template
6)  ASCII histogram (MC terminal prices)
7)  Show Greeks for an option
8)  Self-test demo
9)  Show simulation log (last lines)
10) Export session history to CSV
11) Clear main log file
12) Validate & attempt repair of CSV file
13) Advanced options
14) Exit
CSV Format
Option contracts are specified in CSV with the following columns:

type,S,K,r,sigma,T,q
Column	Description	Example
type	Option type (enum name)	EUROPEAN_CALL
S	Spot price	100
K	Strike price	100
r	Risk-free interest rate	0.05
sigma	Volatility	0.2
T	Time to maturity (years)	1.0
q	Continuous dividend yield	0.0
Example (options_example.csv):

# type,S,K,r,sigma,T,q
EUROPEAN_CALL,100,100,0.05,0.2,1.0,0.0
EUROPEAN_PUT,100,95,0.05,0.25,0.5,0.0
BINARY_CALL,100,110,0.03,0.3,0.5,0.0
DIGITAL_PUT,80,85,0.04,0.25,0.75,0.0
Advanced Options
The advanced sub-menu (option 13) provides:

Batch Monte Carlo on CSV — Run MC pricing per row in a CSV file
Multithreaded MC Demo — Distribute simulations across 1–16 threads
Export Log Summary — Export the simulation log as a CSV summary
License
This project does not currently specify a license.
