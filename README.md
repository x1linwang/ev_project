# IEOR E4010 Capstone: EV Smart Charging & Grid Operations

**Instructors:** Shipra Agrawal, Eric Balkanski  
**Course:** Artificial Intelligence for OR and FE (Spring 2026)

## 📌 Project Overview
This capstone bridges **Operations Research (OR)** and **Reinforcement Learning (RL)**. You will design intelligent agents to manage Electric Vehicle (EV) charging.
The project uses [EV2Gym](https://github.com/StavrosOrf/EV2Gym), a realistic simulator that models battery degradation, power grid physics, and electricity markets.

**Goal:** Maximize trading profit (Buy Low, Sell High) without crashing the power grid.

---

## 🛠️ Environment Setup (Read Carefully!)
This project requires specific libraries. Please follow the instructions for your Operating System.

### Option A: Windows (Recommended: VS Code + venv)
We recommend using the built-in VS Code tools to avoid path issues.

1.  **Open this folder** in VS Code.
2.  Press `Ctrl + Shift + P` to open the Command Palette.
3.  Type and select: **`Python: Create Environment`**.
4.  Choose **`Venv`**.
5.  Select your Python interpreter (e.g., Python 3.10 or 3.1x).
6.  **Important:** When asked to install dependencies from `requirements.txt`, click **Yes/OK**.
7.  Once finished, open a **New Terminal** (`Ctrl + ~`). You should see `(venv)` at the start of the line.

### Option B: Mac / Linux (Recommended: Conda)
Mac users (especially M1/M2/M3 chips) often face issues with standard python installers. We strongly recommend **Anaconda/Miniconda**.

1.  Open your terminal.
2.  Create the environment:
    ```bash
    conda create -n ev_capstone python=3.10
    conda activate ev_capstone
    ```
3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

---

## 🚀 How to Run the Code

### **Phase 1: The OR Baseline (Optimization)**
*Context: Weeks 3-5* We assume we know future prices perfectly. We use **Gurobi** to find the mathematical maximum profit.
* **Run:** `python phase1_optimization.py`
* **Task:** Modify the `Final_SoC` constraint to require 100% charge. How much profit is lost compared to the 50% requirement?

### **Phase 2: Deep Reinforcement Learning**
*Context: Weeks 7-8* We train a Neural Network (PPO Agent) that *doesn't* know the future. It must learn to trade based on current data.
* **Run:** `python phase2_rl.py`
* **Task:** Training takes ~5-10 minutes. Compare the RL agent's profit to your Gurobi baseline.

### **Phase 3: Safety & Physics-Informed AI**
*Context: Week 11-14* A "greedy" AI might overload the transformer. We add a voltage penalty to the reward function.
* **Run:** `python phase3_safety.py`
* **Task:** Check the console output. Does the agent learn to reduce power when the grid is stressed?

### **Phase 4: Multi-Agent Fleet**
*Context: Weeks 9-10* Simulating a full parking lot with 50 chargers.
* **Run:** `python phase4_fleet.py`
* **Task:** Replace the "random action" in the code with your trained agent from Phase 2.

---

## 📚 Resources
* **EV2Gym Paper:** [arXiv:2404.01849](https://arxiv.org/abs/2404.01849)
* **Documentation:** [Stable-Baselines3](https://stable-baselines3.readthedocs.io/)