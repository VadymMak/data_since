# 8-Week Education Program: Quantum Computing and Pandas for Data Science (5 Days per Week, Enhanced Quantum Focus with Crypto Data)

## Program Overview
This 8-week program is designed for a data science and engineering researcher learning Pandas and focusing on quantum computing, using cryptocurrency data (BTC, ETH, BNB) from `crypto_market_data.csv`. It emphasizes quantum computing fundamentals and applications (e.g., Qiskit, QSVM, QAOA) while leveraging Pandas for data preprocessing, culminating in hybrid projects. Each week includes detailed theory, hands-on exercises, and mini-projects, requiring ~5–6 hours spread over 5 days (Monday–Friday, ~1–1.5 hours daily). Days off (Saturday–Sunday) are for review or catch-up. The program starts from Day 5 of Week 1, assuming completion of Days 1–4 (Pandas basics, quantum intro, IBM Quantum setup).

**Prerequisites**: Basic Python knowledge, familiarity with Jupyter Notebook, Qiskit installed, IBM Quantum Experience account, `crypto_market_data.csv` dataset.
**Tools**: Python, Pandas, Qiskit, Matplotlib, NumPy, IBM Quantum Experience.
**Goals**:
- Master quantum computing concepts and Qiskit for data science applications.
- Use Pandas proficiently for cleaning and analyzing crypto data.
- Develop hybrid quantum-classical pipelines for crypto data tasks (e.g., trend classification, portfolio optimization).

## Week 1: Pandas for Crypto Data and Quantum Computing Introduction
**Objective**: Build Pandas skills for crypto data analysis and establish quantum computing foundations (Days 1–4 completed, per PDF and prior progress).
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Hybrid workflows combine classical data processing (Pandas) with quantum algorithms. Pandas cleans and structures crypto data (e.g., `close_btc`, `volume_eth`) for quantum tasks like anomaly detection or optimization. Quantum computing’s parallelism offers potential speedups for specific data science problems.
  - **Exercises**:
    1. Load `crypto_market_data.csv`, compute summary stats (mean, median, std) for `close_btc` and `volume_eth` using `.describe()`.
    2. Save stats to `summary_stats.csv` with `.to_csv()`.
    3. Create a 2-qubit circuit in Qiskit (H on qubit 1, CNOT), simulate with Aer, and save probabilities to a Pandas DataFrame.
    4. Write a 3-sentence explanation of how quantum search (e.g., Grover’s) could identify significant crypto price movements.
- **Resources**:
  - [Pandas Getting Started](https://pandas.pydata.org/docs/getting_started/index.html)
  - [Qiskit Tutorials](https://qiskit.org/learn)
  - Dataset: `crypto_market_data.csv` (from PDF).

## Week 2: Quantum Gates and Crypto Data Cleaning
**Objective**: Deepen quantum gate knowledge and clean crypto data for quantum use.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: Quantum gates (Hadamard, Pauli, CNOT) manipulate qubits to enable computations. Hadamard creates superposition for parallel processing, CNOT entangles qubits for correlated states, and Pauli gates (X, Y, Z) rotate qubit states. These gates are essential for quantum algorithms like QSVM.
  - **Exercises**:
    1. Create a 3-qubit circuit: Apply H to qubit 1, CNOT between qubits 1 and 2, X to qubit 3.
    2. Simulate with Aer, plot histogram with `plot_histogram`.
    3. Add a Y gate to qubit 2, compare results.
    4. Explain (2 sentences) how entanglement could model crypto market correlations.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: Quantum circuits sequence gates to transform qubits, with measurement yielding classical outputs. Visualization (e.g., Bloch sphere, statevector) helps debug circuits. Simulators like Aer approximate real quantum hardware, critical for testing algorithms.
  - **Exercises**:
    1. Build a 2-qubit circuit: Apply H to both qubits, CNOT, measure.
    2. Visualize with `plot_bloch_multivector`.
    3. Run 2000 shots, plot outcome distribution.
    4. Modify with a Z gate before measurement, analyze changes.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: Missing data (NaN) in crypto datasets (e.g., `close_btc` rows 5–7, per PDF) biases analysis. Methods like `.bfill()` (backward fill, as you’ve used) and `.interpolate()` impute values contextually. `.isna()` quantifies missingness.
  - **Exercises**:
    1. Load `crypto_market_data.csv`, count NaN values with `.isna().sum()` (expect 3 in `close_btc`).
    2. Fill NaN in `close_btc` with `.bfill()`.
    3. Interpolate NaN in `close_bnb`, compare with mean fill.
    4. Save cleaned DataFrame to `cleaned_btc_bnb.csv`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Outliers (e.g., `volume_eth` at 1e12, row 10; `close_bnb` at 0, row 15) distort models. The IQR method identifies values outside `[Q1 - 1.5*IQR, Q3 + 1.5*IQR]`. Replacing with median (as you’ve done) preserves distribution.
  - **Exercises**:
    1. Detect outliers in `volume_eth` using IQR (per PDF).
    2. Replace outliers with median, verify with `.describe()`.
    3. Detect and replace outliers in `close_bnb` with mean.
    4. Plot boxplots of `volume_eth` before/after cleaning.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Cleaned crypto data ensures reliable inputs for quantum algorithms. Synthetic qubit data (e.g., probabilities from circuits) can be analyzed with Pandas to bridge classical and quantum workflows.
  - **Exercises**:
    1. Run a 2-qubit circuit (H, CNOT), save probabilities to a Pandas DataFrame.
    2. Summarize probabilities with `.describe()`.
    3. Load cleaned `crypto_market_data.csv`, select high-volume days (`volume_btc` > 90th percentile, per PDF Day 2), save to `high_volume_quantum.csv`.
    4. Write a 3-sentence explanation of how cleaned data supports quantum anomaly detection.
- **Resources**:
  - [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
  - [Qiskit Quantum Gates](https://qiskit.org/documentation/stable/0.36/stubs/qiskit.circuit.QuantumCircuit.html)

## Week 3: Quantum Algorithms and Crypto Data Aggregation
**Objective**: Explore quantum algorithms (Grover’s, QAOA) and aggregate crypto data.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: Grover’s algorithm provides quadratic speedup for unstructured search, ideal for finding anomalies in crypto data (e.g., significant price changes). It uses an oracle to mark target states and a diffuser to amplify probabilities.
  - **Exercises**:
    1. Implement a 2-qubit Grover’s algorithm in Qiskit to find `|11>`.
    2. Simulate with Aer, plot histogram.
    3. Change oracle to find `|10>`, rerun.
    4. Explain (2 sentences) how Grover’s could detect crypto price spikes.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: QAOA optimizes combinatorial problems (e.g., portfolio optimization with BTC, ETH, BNB). It uses variational circuits and classical optimization to approximate solutions, suitable for NISQ devices.
  - **Exercises**:
    1. Define a 4-node Max-Cut problem for QAOA.
    2. Run with p=1, simulate with Aer.
    3. Increase p to 2, compare cut values.
    4. Draw circuit with `circuit.draw()`.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: GroupBy aggregates crypto data (e.g., weekly averages, per PDF Day 6) for trend analysis. `.groupby().agg()` computes statistics, enabling quantum algorithm inputs.
  - **Exercises**:
    1. Convert `date` to datetime with `pd.to_datetime`.
    2. Group by week, compute mean `close_btc` and `close_eth`.
    3. Group by coin, compute max `volume_btc`.
    4. Save results to `weekly_crypto_agg.csv`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Merging and pivot tables structure multi-source crypto data. Merging aligns datasets (e.g., BTC and ETH prices), while pivot tables summarize trends for quantum processing.
  - **Exercises**:
    1. Merge two DataFrames (BTC prices, ETH volumes) on `date` (per PDF Day 2).
    2. Create a pivot table with `coin` as index, `date` as columns, `close` as values.
    3. Plot pivot table as a heatmap with Matplotlib.
    4. Save merged data to `merged_crypto.csv`.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Aggregated crypto data (e.g., weekly trends) defines structured inputs for quantum algorithms. Pandas prepares binary or normalized data for Grover’s or QAOA.
  - **Exercises**:
    1. Create a binary dataset (`1` for `close_btc` > median, `0` otherwise).
    2. Save as `binary_crypto.csv` for Grover’s.
    3. Run Grover’s on a small subset, analyze results with Pandas.
    4. Plot binary data distribution.
- **Resources**:
  - [Pandas GroupBy](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html)
  - [Qiskit Grover’s Tutorial](https://qiskit.org/learn/course/algorithm-design/grovers-algorithm)

## Week 4: Quantum Machine Learning and Crypto Visualization
**Objective**: Introduce quantum machine learning (QSVM) and visualize crypto data.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: QSVM uses quantum kernels to map crypto features (e.g., `close_btc`, `volume_eth`) into high-dimensional spaces, potentially improving classification of trends.
  - **Exercises**:
    1. Install PennyLane (`pip install pennylane`).
    2. Run QSVM on a 2-feature crypto dataset (e.g., `close_btc`, `volume_eth`).
    3. Simulate with PennyLane’s default simulator.
    4. Print classification accuracy.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: Variational circuits optimize parameters for QML tasks (e.g., classifying crypto price movements). They combine quantum and classical computation, leveraging NISQ hardware.
  - **Exercises**:
    1. Build a 2-qubit variational circuit (H, RY gates) in Qiskit.
    2. Optimize with COBYLA, plot cost convergence.
    3. Add an extra layer, rerun.
    4. Explain (2 sentences) variational circuits in QML.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: Visualization highlights crypto trends (e.g., price changes, per PDF Day 5). Pandas and Matplotlib create line plots, histograms, and scatter plots for EDA.
  - **Exercises**:
    1. Plot `close_btc` as a line plot (per PDF).
    2. Create a scatter plot of `close_btc` vs. `volume_eth`.
    3. Add x-axis grid and labels (as you’ve requested).
    4. Save plots as `btc_trends.png`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Custom visualizations (e.g., log scales, histograms) reveal distributions and anomalies. Time-series plots track crypto price movements for quantum inputs.
  - **Exercises**:
    1. Create a histogram of `volume_eth` with 20 bins.
    2. Plot `close_btc` with logarithmic y-scale.
    3. Combine line and scatter plots for `close_eth`.
    4. Save as `eth_visuals.png`.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Normalized crypto data ensures QML compatibility. Visualizing quantum results validates model performance against classical methods.
  - **Exercises**:
    1. Normalize `close_btc` and `volume_eth` to [0, 1].
    2. Feed into QSVM for trend classification (up/down).
    3. Compare QSVM vs. classical SVM (scikit-learn) accuracy.
    4. Plot accuracies in a bar chart.
- **Resources**:
  - [Pandas Visualization](https://pandas.pydata.org/docs/user_guide/visualization.html)
  - [PennyLane QML](https://pennylane.ai/qml/)

## Week 5: Advanced Quantum Algorithms and Crypto Time-Series
**Objective**: Explore advanced quantum algorithms and time-series analysis.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: Quantum Phase Estimation (QPE) estimates eigenvalues, useful for financial modeling (e.g., crypto volatility). It underpins algorithms like Shor’s.
  - **Exercises**:
    1. Implement QPE for a 2-qubit Pauli-Z unitary in Qiskit.
    2. Simulate with Aer, print phase estimate.
    3. Change unitary to Pauli-X, rerun.
    4. Explain (2 sentences) QPE’s role in crypto analysis.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: Shor’s algorithm factorizes integers exponentially faster, impacting cryptography (e.g., securing crypto wallets). It uses QPE and quantum Fourier transform.
  - **Exercises**:
    1. Run Qiskit’s Shor’s algorithm to factorize 15.
    2. Simulate with Aer, print factors.
    3. Increase shots to 2000, check stability.
    4. Draw circuit.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: Time-series operations (e.g., resampling, rolling means, per PDF Day 6) analyze crypto trends. Resampling aggregates data to weekly or daily intervals for quantum inputs.
  - **Exercises**:
    1. Set `date` as datetime index (per PDF).
    2. Resample `close_btc` to weekly averages with `.resample('W').mean()`.
    3. Compute 5-day rolling mean for `close_eth`.
    4. Save to `weekly_crypto.csv`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Technical indicators (e.g., percentage changes, RSI) quantify crypto market dynamics. Percentage changes (per PDF Day 5) identify significant movements.
  - **Exercises**:
    1. Compute percentage change for `close_bnb` with `.pct_change() * 100`.
    2. Filter days where `close_eth` drops >3% (per PDF).
    3. Calculate 14-day RSI for `close_btc`.
    4. Plot RSI and percentage changes.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Time-series features (e.g., percentage changes) can feed quantum algorithms. Pandas prepares normalized or binary data for QPE or Shor’s.
  - **Exercises**:
    1. Create a binary dataset (`1` for `close_btc` > 5% change).
    2. Save as `significant_changes.csv` for QPE.
    3. Run QPE on a toy problem, analyze with Pandas.
    4. Plot phase estimates.
- **Resources**:
  - [Pandas Time-Series](https://pandas.pydata.org/docs/user_guide/timeseries.html)
  - [Qiskit Shor’s Tutorial](https://qiskit.org/learn/course/algorithm-design/shors-algorithm)

## Week 6: Quantum Optimization and Sentiment Integration
**Objective**: Master QAOA and VQE, integrate sentiment data with crypto.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: QAOA optimizes combinatorial problems (e.g., crypto portfolio allocation). Its variational approach suits NISQ devices for practical applications.
  - **Exercises**:
    1. Define a 5-node Max-Cut problem for QAOA.
    2. Run with p=1, simulate with Aer.
    3. Increase p to 3, compare cuts.
    4. Plot cut value histogram.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: VQE finds ground states of Hamiltonians, useful for financial optimization (e.g., risk analysis). It combines quantum circuits with classical optimizers.
  - **Exercises**:
    1. Define a 2-qubit Hamiltonian for VQE.
    2. Run with variational circuit (H, RY gates).
    3. Simulate, plot convergence.
    4. Add noise with Aer’s noise model, rerun.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: Sentiment data (per PDF Day 7) enhances crypto analysis. Merging sentiment scores with price data enables quantum classification tasks.
  - **Exercises**:
    1. Create a synthetic sentiment DataFrame (per PDF: `date`, `sentiment_btc` [-1, 1]).
    2. Merge with `crypto_market_data.csv` on `date`.
    3. Compute mean sentiment by week.
    4. Save to `crypto_sentiment.csv`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Filtering and aggregating sentiment data identifies market moods. High/low sentiment days can be inputs for quantum algorithms.
  - **Exercises**:
    1. Filter days with `sentiment_btc` > 0.5.
    2. Compute correlation between `sentiment_btc` and `close_btc`.
    3. Plot correlation as a scatter plot.
    4. Save filtered data to `positive_sentiment.csv`.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: Sentiment and price data can define quantum optimization problems (e.g., portfolio balancing). Pandas preprocesses features for QAOA or VQE.
  - **Exercises**:
    1. Normalize `close_btc` and `sentiment_btc` to [0, 1].
    2. Save for QAOA portfolio optimization.
    3. Run QAOA, analyze results with Pandas.
    4. Plot optimization outcomes.
- **Resources**:
  - [Pandas Merging](https://pandas.pydata.org/docs/user_guide/merging.html)
  - [Qiskit VQE](https://qiskit.org/learn/course/algorithm-design/variational-quantum-eigensolver)

## Week 7: Hybrid Quantum-Classical Models and EDA
**Objective**: Build hybrid models and perform crypto EDA.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: Hybrid quantum-classical models integrate quantum circuits with classical ML. QSVM uses quantum kernels for enhanced crypto trend classification.
  - **Exercises**:
    1. Build a hybrid QSVM for `close_btc`, `sentiment_btc`.
    2. Simulate with Aer, print accuracy.
    3. Use ZZFeatureMap, rerun.
    4. Compare runtimes.
- **Day 2 (Quantum, 1 hr)**:
  - **Theory**: TensorFlow Quantum (TFQ) enables QML with TensorFlow, supporting hybrid circuits for crypto price prediction.
  - **Exercises**:
    1. Install TFQ (`pip install tensorflow-quantum`).
    2. Run a TFQ circuit for binary classification.
    3. Simulate with PennyLane’s TFQ backend.
    4. Plot classification boundaries.
- **Day 3 (Pandas, 1 hr)**:
  - **Theory**: EDA (per PDF Days 1–4) uncovers crypto patterns via stats, correlations, and visualizations. Correlation matrices quantify feature relationships.
  - **Exercises**:
    1. Compute summary stats with `.describe()` for `close_btc`, `volume_eth`.
    2. Calculate correlations between `close_btc`, `close_eth`, `sentiment_btc`.
    3. Plot correlation matrix as heatmap.
    4. Save to `eda_results.csv`.
- **Day 4 (Pandas, 1 hr)**:
  - **Theory**: Outlier detection and visualization (per PDF Day 4) ensure data quality. Boxplots and scatter plots highlight anomalies for quantum preprocessing.
  - **Exercises**:
    1. Detect outliers in `volume_eth` with IQR.
    2. Replace with median, verify with boxplot.
    3. Plot `volume_eth` vs. `close_btc` scatter.
    4. Save cleaned data to `cleaned_eda.csv`.
- **Day 5 (Integration, 1 hr)**:
  - **Theory**: EDA prepares features for hybrid quantum models. Comparing quantum and classical performance validates advantages.
  - **Exercises**:
    1. Preprocess crypto data (normalize, remove outliers).
    2. Classify trends with hybrid QSVM.
    3. Compare with classical SVM.
    4. Plot accuracies in a bar chart.
- **Resources**:
  - [Kaggle Datasets](https://www.kaggle.com/datasets)
  - [TensorFlow Quantum](https://www.tensorflow.org/quantum)

## Week 8: Capstone Project and Next Steps
**Objective**: Synthesize skills in a hybrid crypto project and plan future learning.
- **Day 1 (Quantum, 1 hr)**:
  - **Theory**: Quantum algorithms (Grover’s, QSVM, QAOA, VQE) offer data science applications. Real quantum hardware (IBM) tests practical performance.
  - **Exercises**:
    1. Run QSVM on IBM’s quantum hardware.
    2. Simulate with Aer, compare results.
    3. Print runtime and accuracy.
    4. Draw circuit.
- **Day 2 (Pandas, 1 hr)**:
  - **Theory**: Preprocessing (cleaning, normalization, indicators) ensures crypto data quality for quantum algorithms. EDA and sentiment integration enhance insights.
  - **Exercises**:
    1. Clean `crypto_market_data.csv` (NaN, outliers).
    2. Compute indicators (7-day MA, RSI, per PDF Day 6).
    3. Merge with sentiment data, normalize features.
    4. Save to `capstone_data.csv`.
- **Day 3 (Project, 1.5 hr)**:
  - **Theory**: Hybrid pipelines combine Pandas preprocessing with quantum algorithms. Example: QSVM for crypto trend classification using price and sentiment.
  - **Exercises**:
    1. Preprocess data (normalize `close_btc`, `sentiment_btc`).
    2. Build QSVM for trend classification.
    3. Run on simulator, save results.
    4. Start capstone Jupyter Notebook.
- **Day 4 (Project, 1.5 hr)**:
  - **Theory**: Comparing quantum and classical models quantifies advantages. Visualizations communicate results effectively.
  - **Exercises**:
    1. Run classical SVM on same data.
    2. Compare QSVM vs. SVM accuracies.
    3. Plot results (bar chart, trend predictions).
    4. Complete capstone Notebook with summary.
- **Day 5 (Wrap-Up, 1 hr)**:
  - **Theory**: Quantum computing’s NISQ era offers practical applications, with fault-tolerant systems on the horizon. Communities (e.g., X) drive learning.
  - **Exercises**:
    1. Submit capstone Notebook.
    2. Write a 5-sentence reflection on quantum vs. classical methods.
    3. Explore Qiskit’s error correction tutorials.
    4. Follow X’s @QuantumInsider.
- **Resources**:
  - [IBM Quantum Lab](https://quantum-computing.ibm.com/)
  - X: Follow @qmunitytech.

## Tips for Success
- **Practice**: Run exercises in Jupyter Notebook, save to GitHub.
- **Debugging**: Use `.info()` for Pandas, `plot_circuit_layout` for Qiskit.
- **Community**: Check X posts from @GoogleAI for quantum tips.
- **Schedule**: 1–1.5 hours daily (Mon–Fri), use weekends for review.
- **Dataset**: Use `crypto_market_data.csv` (per PDF).

## Additional Notes
- Adjust daily hours if needed (e.g., 45 min for faster pace).
- Revisit `.bfill()` or IQR methods for Pandas errors (per your prior work).
- IBM Quantum’s free tier supports all quantum tasks.
- Fixed PDF errors: Replaced `df circulation()` with `.describe()`, `df committee` with `df_clean`, `df["btc diminished"` with `df["btc_pct_change"]`.