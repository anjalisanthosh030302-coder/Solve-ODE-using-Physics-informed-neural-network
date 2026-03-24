# Solve-ODE-using-Physics-informed-neural-network
Physics-Informed Neural Network (PINN) implementation in PyTorch for solving ordinary differential equations using automatic differentiation and physics-based loss functions.

# 🧠 Physics-Informed Neural Network (PINN) for Solving ODE

This project demonstrates how to solve an Ordinary Differential Equation (ODE) using a **Physics-Informed Neural Network (PINN)** built with **PyTorch**.

Unlike traditional numerical solvers, this approach uses a neural network that **learns the solution while respecting the governing physical law (the differential equation itself).**

---

# 📌 Problem Statement

We aim to solve the following first-order ODE:

˙
y =−2xy,

### ✅ Exact Solution

[
y(x) = e^{-x^2}
]

This known solution is used only for **validation**, not for training.

---

# 🧠 What is a Physics-Informed Neural Network?

A **Physics-Informed Neural Network (PINN)** is a neural network trained to satisfy:

1. **Data constraints** (if available)
2. **Physical laws** (ODEs/PDEs)

---

## 🔍 Key Idea

Instead of learning from labeled data:

* The model learns by minimizing how much it **violates the equation**

👉 This is done using a **physics-based loss function**

---

## 🔹 Training the Model

We train using:

### Phase 1: Adam Optimizer

* Fast convergence
* Handles noisy gradients

### Phase 2: LBFGS Optimizer

* High precision optimization
* Improves final accuracy

---

## 🔹  Prediction

After training:

* Model predicts (y(x)) for any (x)
* Compared with exact solution

---

# 📊 Understanding the Results

---

## ✅ Good Performance Region

* Inside training domain → accurate predictions

---

## ❌ Common Issue: Extrapolation

* Outside training domain → poor accuracy

### Why?

* Model only learns physics where trained
* Neural networks are poor extrapolators

---

## ⚠️ Observed Issue in This Project

* Curve deviates for large (x)
* Fails to capture exponential decay

---

# 🛠️ Improvements Applied

---




## 🔧 4. Adaptive Sampling

More training points where:

* Error is high
* Model struggles (e.g., (x > 2))

---


# 🧠 Key Concepts Explained

---

## 🔹 Collocation Points

Points where the differential equation is enforced.

---

## 🔹 Residual

Difference between:

* Left side of equation
* Right side of equation

---

## 🔹 Automatic Differentiation

Technique to compute derivatives:

* Exact (not numerical)
* Efficient for deep learning

---

## 🔹 Boundary / Initial Condition

Constraints that define the unique solution.

---

## 🔹 Extrapolation vs Interpolation

| Type          | Meaning                 |
| ------------- | ----------------------- |
| Interpolation | Inside training domain  |
| Extrapolation | Outside training domain |

👉 PINNs excel at interpolation, struggle with extrapolation.

---

# ▶️ How to Run

```bash
pip install torch numpy matplotlib
python pinn_ode.py
```

---

# 📈 Output

* Graph comparing:

  * Exact solution
  * PINN prediction

* Log-scale visualization for better comparison

---

# 🔥 Applications of PINNs

* Fluid dynamics
* Heat transfer
* Structural mechanics
* Quantum physics
* Financial modeling

---

# 📚 References

* Raissi et al., *Physics-Informed Neural Networks*
* Lagaris et al., *Neural Networks for Differential Equations*

---

# 👩‍💻 Author

Anjali P | AI/ML Enthusiast

---

# ⭐ Support

If you found this helpful:

* ⭐ Star this repository
* 🍴 Fork and experiment
* 📢 Share with others
