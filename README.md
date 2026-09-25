# Traffic Modelling & Comparison

## 📖 Project Overview
This project is a mathematical modeling simulation of 1-dimensional traffic flow. It was designed to study how vehicles interact on an open road based on the distance and speed of the vehicle directly ahead of them. 

Instead of relying on a single approach, this repository **combines and compares different mathematical methods** to evaluate their realism and behavior.

## Mathematical Models Implemented

### 1. Optimal Velocity (OV) Model (First-Order)
The baseline of this project is a deterministic first-order model. The speed of vehicle $n$ at time $t$ is strictly determined by the distance $\alpha$ to the leading vehicle $n+1$:
* Below a critical distance (`alpha_Critique`), the vehicle stops completely.
* Above it, the vehicle accelerates exponentially up to a defined `Vitesse_Max`.
* **Drawback observed:** This model can cause unrealistic infinite accelerations or abrupt stops because it does not consider the *speed* of the leading vehicle.

### 2. Intelligent Driver Model (IDM) (Second-Order)
To improve the simulation, we integrated the IDM. This is a second-order model that calculates *acceleration* rather than absolute speed. It takes into account:
* The spatial gap ($\alpha$)
* The **velocity difference** ($\Delta v$) between the follower and the leader.
* A safe time headway ($T$) and comfortable deceleration limits.
* **Advantage:** Drivers brake proactively if the leading car is slower, preventing unrealistic crashes.

### 3. Stochastic Noise Injection
Human drivers are not robots. To bridge the gap between pure mathematics and real-world behavior, a Gaussian noise (`bruit_std`) is injected into the velocity/acceleration calculations. This randomness mimics delayed human reaction times and inattention.

## Installation & Usage

### Prerequisites
- Python 3.x
- `numpy`
- `matplotlib`

```bash
pip install numpy matplotlib
