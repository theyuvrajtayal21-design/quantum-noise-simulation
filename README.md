Quantum Noise Simulation
Comparative Analysis of Single-Qubit Noise Channels Using Python

An educational numerical simulation comparing how three idealized quantum noise channels affect a single qubit. The experiment prepares the |+⟩ state and measures fidelity, l1 coherence, and probability of measuring |0⟩ after applying depolarizing, phase-damping, and amplitude-damping channels.
Scope: This is a single-qubit mathematical simulation, not an experiment on quantum hardware. Equal numerical channel parameters do not necessarily represent equivalent physical noise strengths.

Research question
How do different noise mechanisms affect the same initial qubit, and why is fidelity alone insufficient to characterize their effects?
Initial state and quantum channels
The initial state is |+⟩ = (|0⟩ + |1⟩)/√2, with density matrix:
ρ₀ = 1/2 × [[1, 1],
            [1, 1]]
Channel	Implementation	Physical interpretation
Depolarizing	ρ' = (1 − p)ρ + pI/2	Mixes the state toward the maximally mixed state
Phase damping	K₀ = diag(1, √(1−γ)), K₁ = diag(0, √γ)	Reduces off-diagonal coherence without changing populations
Amplitude damping	K₀ = diag(1, √(1−γ)), K₁ = [[0, √γ], [0, 0]]	Models relaxation from `


For the damping channels, the output is calculated as ρ' = Σᵢ Kᵢ ρ Kᵢ†. The phase-damping convention used here scales off-diagonal terms by √(1−γ); alternative conventions may use different parameterizations.
Methodology
1. Prepare the |+⟩ state and calculate ρ₀ = |+⟩⟨+|.
2. Apply each noise channel to the same initial state at 51 evenly spaced parameter values between 0 and 1.
3. Calculate fidelity F = ⟨+|ρ'|+⟩, l1 coherence C = |ρ'₀₁| + |ρ'₁₀|, and measurement probability P(0) = ρ'₀₀.
4. Plot the metrics and export 153 numerical records (3 channels × 51 parameter values).
5. Check Hermiticity, unit trace, and positive semidefiniteness at six parameter values per channel, and compare fidelity with analytical predictions at parameter 0.6.
Results
At a noise parameter of 0.6:
Noise channel	Fidelity	l1 coherence	P(0)
Depolarizing	0.7000	0.4000	0.5000
Phase damping	0.8162	0.6325	0.5000
Amplitude damping	0.8162	0.6325	0.8000


Main finding: For the selected initial state and parameterization, phase damping and amplitude damping have identical fidelity and coherence but different measurement probabilities. Identical fidelity does not imply identical output states.
Fidelity comparison

Coherence comparison

Probability of measuring |0⟩

Additional depolarizing-noise analysis

Reproduce the simulation
Notebook: [Seminar_.ipynb](Seminar_.ipynb)
Numerical dataset: [quantum_noise_results.csv](quantum_noise_results.csv)
1. Open the notebook in Google Colab or Jupyter Notebook.
2. Install dependencies if necessary: pip install numpy matplotlib pandas notebook.
3. Run all cells from top to bottom to construct the states, apply noise, generate graphs, validate outputs, and export the CSV.
4. Compare the regenerated results with the committed CSV and figures.
The implementation uses NumPy matrix operations; Qiskit and quantum hardware are not required.
Validation and limitations
The notebook reports passing checks for Hermiticity, trace normalization, and nonnegative eigenvalues (within numerical tolerance), as well as analytical fidelity checks at parameter 0.6. These support internal mathematical consistency, not hardware realism.

The experiment uses one initial state, a single qubit, and idealized channels without experimental calibration. Possible extensions include other input states, multi-qubit systems, additional metrics, and calibrated hardware-inspired noise.
Repository files
- Seminar_.ipynb — simulation, plotting, validation, and CSV export
- quantum_noise_results.csv — experimental measurements
- quantum_noise_fidelity_comparison.png — fidelity graph
- quantum_noise_coherence_comparison.png — coherence graph
- quantum_noise_p0_comparison.png — measurement-probability graph
- depolarizing_noise_analysis.png — supplementary graph
Academic context
Prepared by Yuvraj Tayal for a quantum noise simulation seminar at ITM University Gwalior.
