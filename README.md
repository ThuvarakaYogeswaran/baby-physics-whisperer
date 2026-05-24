# 🌫️ Baby Physics Whisperer

[![GitHub](https://img.shields.io/badge/GitHub-ThuvarakaYogeswaran-blue?logo=github)](https://github.com/ThuvarakaYogeswaran)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)](https://pytorch.org)

### *An AI that learns 2D fluid dynamics through pure observation — no equations, no pre-training, just watching and adapting.*

---

## 🎯 What is this?

**Baby Physics Whisperer** is a neural network that learns physics the way a baby does: by watching, predicting, and learning from mistakes.

The AI starts **completely blank** (random weights). It watches smoke diffuse in a 2D room. It predicts where the smoke will go next. When it's wrong, it learns. When physics changes (wind reverses), it adapts — all in real-time.

**The name says it all:**
- 👶 **Baby** = Starts with zero knowledge (tabula rasa)
- 🔬 **Physics** = Learns cause-and-effect, not just patterns  
- 🗣️ **Whisperer** = Decodes hidden variables (wind, diffusion, obstacles)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔄 **Online Learning** | Updates model weights after EVERY frame |
| 🌬️ **Adaptive** | Re-learns physics when environment changes |
| 🎮 **Interactive** | Click to add smoke, sliders control wind |
| 🧠 **Residual CNN** | Predicts changes (Δ) instead of absolute values |
| 💻 **CPU-only** | Runs on any laptop (no GPU required) |

---

## 📊 Results

| Metric | Before Training | After Training | Improvement |
|--------|----------------|----------------|-------------|
| Prediction Error (MSE) | 0.100 | 0.016 | **84%** ↓ |
| Adaptation Time | N/A | <50 steps | Real-time |

### Learning Curve

![Learning Curve](https://github.com/ThuvarakaYogeswaran/baby-physics-whisperer/commit/807762f71799e7b1fb2cfd4fda3ae78b25320ecd)

*Error drops from 0.100 to 0.016 — 84% improvement!*


### 🎮 How to Use the Demo
Once the demo window opens:

Action	Effect
Click anywhere on the smoke	Add a puff of smoke at that location
Drag Wind X slider	Change horizontal wind direction
Drag Wind Y slider	Change vertical wind direction
Click "Add Smoke Puff" button	Add smoke at the center
Click "Reset" button	Clear all smoke and restart
The left panel shows the actual physics simulation.
The right panel shows the AI prediction.

Watch as the AI learns to match the left panel!

### 🔬 How It Works
1. The Simulator (Physics Engine)
The simulator uses a 2D finite difference method to model:

Diffusion - Smoke spreads naturally (like smell in air)

Advection - Wind pushes smoke in a direction

Obstacles - Walls block smoke movement

Dissipation - Smoke fades over time

2. The Neural Network
python
class PhysicsLearner(nn.Module):
    def forward(self, x):
        # Key insight: Predict the CHANGE, not absolute values
        return x + self.net(x)  # Residual connection
Why this works: Smoke mostly stays the same from frame to frame. Predicting the small change is much easier than predicting the entire frame.

3. The Learning Loop
python
for step in range(500):
    # AI predicts next frame
    prediction = model(current_smoke)
    
    # Simulator shows reality
    reality = simulator.step()
    
    # Calculate error
    loss = MSE(prediction, reality)
    
    # AI learns from mistake
    loss.backward()
    optimizer.step()

### 🛠️ Tech Stack
Component	Technology
Deep Learning	PyTorch 2.0+
Physics Simulation	NumPy (finite difference)
Visualization	Matplotlib
Testing	PyTest
Configuration	YAML

### 📊 Performance Benchmarks
Metric	Value
Training time	~2 minutes (500 steps on CPU)
Inference speed	~50 FPS (real-time)
Memory usage	<500MB RAM
Model size	~2MB (weights only)
Grid resolution	64x64 pixels

### 🤝 Connect with Me
GitHub: ThuvarakaYogeswaran

LinkedIn: Thuvaraka Yogeswaran


### 🙏 Acknowledgments
Inspired by MIT's "Tadpole" project (2025)

Google's "DreamerV3" for world model concepts

PyTorch team for the excellent framework

Open-source PDE solver references

### ⭐ Show Your Support
If you found this project useful:

⭐ Star the repository on GitHub

🔗 Share it on LinkedIn/Twitter

🐛 Report issues or suggest improvements

### 📞 Contact
For questions or collaborations:

Open an issue on GitHub

Connect with me on LinkedIn
