# A Study on Quantum Neural Networks for Image Classification

This repository contains the experiments and report for a study of Quantum Neural Networks (QNNs), with a focus on Variational Quantum Circuits (VQCs) applied to small image classification benchmarks. The work compares VQC models against classical baselines (Naive Bayes, SVM) and neural networks (simple and deeper ANN) on reduced MNIST and Fashion-MNIST variants plus a synthetic dataset.

The technique report is in `qnn_technique_report.pdf` and is the primary reference for the theory, methodology, and discussion.

**Key takeaways (from the report)**
- VQC models are competitive on small benchmarks but still trail strong classical and deep learning baselines in practical accuracy.
- With comparable model complexity, VQCs can match or exceed simple ANN baselines.
- The results point to VQCs as a promising approximation method, but not yet a practical replacement for classical models on these tasks.

**Project layout**
- `qnn_technique_report.pdf`: Full report (theory, experiments, results, references).
- `dataset/`: Prepared datasets in `.npy` format (train/test splits) plus a dataset preparation notebook.
- `notebook/`: Training and evaluation notebooks for classical ML, ANN, and QNN variants.
- `output/`: Plots and result tables. See `output/results/` for accuracy curves, timing, and summary CSVs.

**Datasets**
All experiments use low-dimensional inputs to fit near-term quantum circuits.
- `MNIST-2`: two-class subset (digits 3 and 6), downscaled to `2x2` (4 features).
- `Fashion-MNIST-2`: two-class subset (dress, shirt, T-shirt/top), `2x2`.
- `Fashion-MNIST-3`: three-class subset (dress, shirt, T-shirt/top), `2x2`.
- `Syn-Dataset-4`: synthetic two-class dataset with 4 features.

Dataset statistics and preprocessing details are in the report. The train/test split used in the experiments is 90% / 10%.

**Models evaluated**
- Classical ML: Naive Bayes, SVM.
- ANN: `SimpleANN` (single linear layer), `ComplexANN` (multi-layer MLP).
- QNN: `SimpleVQC`, `ComplexVQC` based on `ZZFeatureMap` + `EfficientSU2` ansatz (Qiskit).

**Results**
Summary plots are in `output/results/`:
- `training_accuracy.png`, `testing_accuracy.png`
- `accuracy.csv`, `speed.csv`

The report provides the interpretation of these results and a discussion of current limitations.

**How to run**
The project is notebook-driven. Typical flow:
1. `dataset/dataset preparation.ipynb`
2. `notebook/Training traditional ML.ipynb`
3. `notebook/Training ANN.ipynb`
4. `notebook/Training QNN on simulator.ipynb`
5. `notebook/Training QNN on real dataset.ipynb`
6. `output/plot_result.ipynb`

**Environment**
Notebooks assume Python 3 and the following libraries (representative, see notebooks for exact usage):
- `numpy`, `pandas`, `matplotlib`, `seaborn`
- `scikit-learn`
- `torch`, `torchvision`
- `qiskit`, `qiskit-machine-learning`, `qiskit-algorithms`

If you want to reproduce IBM Quantum runtime experiments, you will also need the IBM Qiskit runtime/provider packages and appropriate credentials.

**Contact:**
Van Tien Nguyen (vantn.prof@gmail.com).
