# Quantum HQ - GIC Phase 3 Submission - MITRE

Team Name: Quantum HQ

Project Title: Quantum Asphalt: Simulating Binder Aging with Hybrid Quantum-Classical Algorithms

Challenge Track: MITRE



## Setup

This repository provides a modular, reproducible, and extensible hybrid quantum-classical simulation pipeline for modeling chemical aging processes in asphalt binder molecules. The framework is composed of four annotated Jupyter notebooks (corresponding to representative molecules of the SARA fractions: saturates, aromatics, resins, and asphaltenes), alongside precomputed classical data files and all required quantum simulation components.

All quantum simulations leverage IBM’s Qiskit ecosystem, while classical pre-processing depends on electronic structure methods using PySCF and structure optimization via ML potentials. The code has been validated under controlled environments and is designed to be adaptable to real-world molecular geometries and perturbation models.

This code was developed and tested in Python 3.10.18. Compatibility with later versions is not guaranteed due to breaking changes and deprecations in certain dependencies (e.g., PySCF, Qiskit Terra, Qiskit Nature, RDKit).

Recommended Options for Running the Code
1. Cloud-Based Execution
The code can be executed in a cloud-based Jupyter environment such as qBraid or Google Colab. All required packages are compatible with Python 3.10.18 and should install without issue using the provided requirements.txt. This is the most straightforward option and avoids local dependency and environment configuration challenges.

2. Use of Precomputed Classical Files
If you prefer to skip classical electronic structure calculations (which are computationally intensive), you may directly use the .chk, .npz, and .xyz files provided. These files contain molecular geometry and wavefunction data generated using PySCF. This approach allows users to immediately begin quantum simulations without recomputing classical data.

3. Local Execution on Linux Systems
Linux users may run the entire pipeline from classical preprocessing to quantum simulation. Note that classical DFT steps are computationally expensive and may require several hours, especially for larger molecules such as squalene and violanthrone-79.

4. Windows/macOS Systems via WSL
For users on Windows or macOS, we recommend using Windows Subsystem for Linux (WSL) with Ubuntu and setting up a virtual environment. This configuration has been tested successfully using Python 3.10.18 and provides full compatibility with PySCF, RDKit, and related scientific libraries.

Note: The notebooks were developed and executed using WSL + virtualenv. Some classical preprocessing components may not function properly on native Windows or macOS Python installations due to unresolved dependencies.


## qBraid: Step-By-Step Instructions

qBraid Lab provides a cloud-based environment optimized for quantum computing workflows, including seamless integration with IBM Quantum simulators and quantum software stacks like Qiskit. Below are detailed instructions to set up and run the notebooks from this project on qBraid.

1. Create a New Project and Upload Files

In the qBraid dashboard, click "New Project".


Upload:

All Jupyter notebooks (*.ipynb)

Auxiliary data files (*.chk, *.npz, *.xyz) located in the data/ directory

Ensure the directory structure is preserved, or adjust notebook paths accordingly.

2. Set Up the Environment

qBraid provides pre-configured environments with Qiskit and Python installed.

To ensure compatibility, create a new conda environment or use qBraid’s environment customization feature:

Open a terminal within qBraid Lab.

Create and activate a Python 3.10 environment

3. Launch Jupyter Notebooks

From the qBraid Lab interface, open the Jupyter notebook launcher.

Open the desired notebook file.

Run the notebook cells sequentially.

If you want to skip lengthy classical calculations, use the precomputed .chk and .npz files located in the data/ directory.

4. Configure Quantum Backends

The notebooks default to using statevector_simulator for ideal simulations and qasm_simulator for noisy, shot-based simulations.

To run on IBM Quantum hardware simulators via qBraid:

Configure the IBM Quantum API token in qBraid settings.

Select the appropriate backend from the list of available devices.

The code is designed for immediate compatibility with IBM QPU devices, though hardware runs are optional.

[<img src="https://qbraid-static.s3.amazonaws.com/logos/Launch_on_qBraid_black.png" width="150">](https://account.qbraid.com?gitHubUrl=https://github.com/mastermercury18/mitre-gic)
## Expected Inputs/Outputs

Inputs:

Jupyter Notebooks: The primary input files are the annotated Jupyter notebooks (.ipynb) for each molecular component (saturates, aromatics, resins, asphaltenes).

Auxiliary Data Files: These include molecular geometry files (*.xyz), checkpoint files (*.chk), and intermediate data arrays (*.npz) generated during classical DFT and CASSCF calculations.

Configuration Parameters: User-defined parameters within notebooks such as number of VQE iterations, Trotter time steps, and perturbation types (oxidation, crosslinking, etc.).

Outputs:

Quantum Simulation Results: Energy estimates, time-evolution data for HOMO-LUMO gaps, dipole moments, and bond mode populations.

Perturbation Analysis: Ranked contributions of molecular orbitals and atomic centers to aging-related perturbations.

Plots and Graphs: Visualizations of short-term Suzuki-Trotter evolutions and long-term Lindblad master equation aging trends.

Data Files: Intermediate and final output files storing relevant metrics and states, useful for further analysis or reproducibility.
## Known Limitations and Assumptions

Computational Resource Requirements: Classical pre-processing, especially DFT and CASSCF calculations, can be computationally intensive and time-consuming (ranging from hours to multiple days depending on molecular complexity).

Package Compatibility: The code is developed and tested specifically with Python 3.10.18 and particular versions of Qiskit and OpenFermion. Newer versions may introduce incompatibilities.

Simulated Perturbations: The aging perturbations are modeled using simulated operators rather than experimentally derived reduced density matrices (RDMs), trading accuracy for computational efficiency and flexibility.

Near-Term Hardware Constraints: Simulations are optimized for near-term quantum hardware with limited qubit counts (8 qubits) and relatively shallow circuits, which may limit scalability for larger molecular systems.

Environmental Effects Approximation: Realistic aging effects modeled via the Lindblad master equation and curve fitting are approximations that capture dissipation and decoherence, but do not fully represent all possible environmental interactions.
