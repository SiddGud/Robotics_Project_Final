# Control of a 2-Link Manipulator: Systems Thinking 2025

This repository contains a complete implementation for the modeling, simulation, and control of a 2-link robotic manipulator. The project focuses on deriving nonlinear dynamics and implementing various control strategies to achieve precise configuration tracking.

---

## 🚀 Project Overview
The objective is to drive a 2-link manipulator from an initial state of $q(0) = [0.2, 0.15]^T$ rad to a desired target configuration of $q_{desired} = [0, 0]^T$ rad. The system is modeled using the Lagrangian formulation to account for mass, inertia, and gravitational effects.



---

## 💻 The Critical Role of MATLAB & Simulink
This project relies on the MATLAB ecosystem to bridge the gap between complex theoretical physics and practical robotic control.

### 1. MATLAB: The Mathematical Backbone
MATLAB is utilized as the primary computational engine for:
* **Dynamic Derivation:** Using symbolic tools to handle complex partial derivatives and the Euler-Lagrange equations.
* **Numerical Solving:** Leveraging high-performance solvers like `ode45` to solve the first-order nonlinear differential equations derived from the system dynamics.
* **State-Space Transformation:** Converting second-order dynamics into a first-order state vector for digital simulation.

### 2. Simulink: Visualizing Systems Thinking
Simulink is essential for modeling the "Systems Thinking" aspect of this project by providing a visual, modular representation of the control loop.
* **Modular Dynamics:** The **State Space Matrix** block encapsulates the physical robot, including the Inertia ($M$), Coriolis ($C$), and Gravity ($G$) matrices.
* **Closed-Loop Feedback:** It provides a clear visualization of how error signals drive the controllers to generate motor torques ($\tau$).
* **Integration Blocks:** Simulink's $1/s$ blocks physically represent the integration of angular accelerations into velocities and positions, allowing us to see the robot's motion in real-time.



---

## 🛠 Controller Analysis & Tuning
We implement and analyze three fundamental control strategies—**PI, PD, and PID**—under different tuning philosophies:

| Tuning Philosophy | Goal | Result |
| :--- | :--- | :--- |
| **Aggressive** | Maximum Speed | Fastest settling time but suffers from significant overshoot. |
| **Balanced** | Optimal Compromise | Fast, stable, and eliminates steady-state error with PID. |
| **Conservative** | Maximum Stability | Smooth, precise movement with zero overshoot but the slowest response. |

### Performance Observations
* **PI Controller:** Found to be fundamentally unsuitable due to a lack of a derivative (damping) term, leading to severe oscillations and instability.
* **PD Controller:** A fast and stable option but limited by its inability to eliminate steady-state error.
* **PID Controller:** The superior and most versatile solution, combining aggressive response, damping, and perfect error correction.

---

## 📋 System Parameters
* **Link 1:** $m_1 = 5$ kg, $l_1 = 0.25$ m.
* **Link 2:** $m_2 = 3$ kg, $l_2 = 0.15$ m.
* **Gravity:** $g = 9.81$ m/s².

---

## 📂 Repository Structure
* `/codes`: MATLAB scripts and Simulink `.slx` models.
* `/plots`: Properly labeled trajectories, errors, and torques.
* `Report.pdf`: Comprehensive analysis and mathematical derivations.

**Author:** Siddhant Gudwani
