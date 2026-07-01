# 🚗 Autonomous Navigation Agent using Deep Q-Learning (DQN)



## 🧠 Overview
This project is a custom-built Reinforcement Learning (RL) simulation where an AI agent learns to drive a car and navigate a track autonomously. Instead of relying on pre-packaged environments like OpenAI Gym, the entire physics engine, sensor system, and deep learning model were engineered from scratch.

The agent starts completely blind and learns through trial and error (crashing). By utilizing a **Deep Q-Network (DQN)** and the **Bellman Equation**, it gradually discovers how to map its sensor inputs to optimal steering decisions to reach a target.

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Deep Learning Framework:** PyTorch (Neural Network, Tensors, Backpropagation)
* **Environment & Physics:** PyGame (Rigid body movement, Collision detection)
* **Mathematics:** NumPy, Trigonometry (Ray-casting)

## ⚙️ How It Works

### 1. The Environment (MDP)
The environment acts as a Markov Decision Process. It tracks the car's state, applies physics, and returns rewards.
* **Ray-Casting Sensors:** The car features custom-built "LIDAR" sensors. It casts 5 rays at different angles to measure the pixel distance to the nearest wall.
* **State Space:** A 7-dimensional vector consisting of the 5 sensor distances (normalized) and the X/Y coordinate distance to the target goal.
* **Action Space:** Discrete actions: `0` (Turn Left), `1` (Go Straight), `2` (Turn Right).

### 2. The Brain (Deep Q-Network)
A fully connected Feed-Forward Neural Network built in PyTorch.
* **Input Layer:** 7 Neurons (State)
* **Hidden Layer:** 128 Neurons (ReLU Activation)
* **Output Layer:** 3 Neurons (Q-Values for each action)

### 3. The Learning Process
The agent utilizes an **Epsilon-Greedy** strategy to balance exploration (acting randomly to discover the map) and exploitation (using the brain to survive).
* **Rewards:** `+100` for reaching the goal, `-50` for crashing into a wall, and `+0.5` for surviving a frame.
* **Training:** After every move, the network calculates the target Q-value using the Bellman Equation and updates its weights using Mean Squared Error (MSE) loss and the Adam optimizer.

---

## 🚀 Installation & Setup

Ensure you have Python 3.8+ installed. 
clone the repo

2. Create a virtual environment (Recommended)


# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate


3. Install dependencies
pip install -r requirements.txt
4. Run the simulation

Bash
python new_main.py

