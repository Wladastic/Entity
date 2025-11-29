# Entity
### A Resonance-Driven Architecture for Machine Intuition

![Status](https://img.shields.io/badge/Status-Research_Preview-blue) ![License](https://img.shields.io/badge/License-MIT-green)

**Entity** is an experimental neural architecture that abandons the rigid, sequential "assembly line" of the Transformer.

Instead of forcing every token to traverse every layer in a fixed order, Entity treats the neural network as a **Cross-Layer Resonance Field**. In this architecture, depth is dynamic, computation is non-linear, and reasoning ends not when the stack is exhausted, but when the system reaches a low-energy equilibrium.

> "Intuition is not a simulation. It is the rapid collapse of distributed signals into a stable state."

---

## 🛑 Motivation: The Local Compute Bottleneck
This project exists because running modern LLMs on consumer GPUs is inefficient.

Current architectures—even optimized ones like Mixture of Experts (MoE)—are wasteful. They force every single token, regardless of how trivial, to travel through the entire forward pass. On a home GPU, this means you are burning memory bandwidth and FLOPs calculating "the" and "and" with the same heavy machinery used for complex logic.

**Entity is designed for the constrained reality of local hardware.** By allowing the model to "skip" depth and stabilize early, we aim to bring high-level reasoning to smaller GPUs without the bloat of unnecessary computation.

---

## 📄 [Read the Whitepaper](./PAPER.md)
For a deep dive into the thermodynamics of thought, Open Vector theory, and the implementation of the Resonance Core, please read the full architectural proposal.

---

## ⚡ The Architectural Shift

### The Standard Transformer (The Pipeline)
Current LLMs operate like a factory line. High-level instructions must survive a gauntlet of low-level processing, and simple tokens waste compute on deep abstraction layers.

```mermaid
Input -> [L0] -> [L1] -> [L2] ... -> [L99] -> Output
(Rigid, Sequential, High Latency, Wasted Local Compute)
```

### The Entity Architecture (The Field)
Entity exposes all layers simultaneously. Inputs are injected directly where they belong based on abstraction level. Layers communicate laterally and vertically until the **Resonance Core** detects stability.

```mermaid
       [Resonance Core (Energy Monitor)]
                  |
      +-----------+-----------+
      |           |           |
[Input A] --> [Layer 5] <--> [Layer 20] <-- [Input B (Context)]
      ^           ^           ^
      |           |           |
   [Layer 0] <-> [Layer 10] <-> [Layer 30]
```

## 🧠 Key Mechanisms

### 1. Open Vector Fields
There is no "Input Layer." The stack is permeable.
- **Raw tokens** enter shallow layers.
- **System prompts & Logic** are injected directly into deep layers.
- This creates **"Geistesblitz"** moments: instant convergence without sequential traversal.

### 2. The Resonance Core (RC)
A global controller that replaces the fixed forward pass with a **stabilization loop**.
It monitors the **Entropy ($H$)** and **Energy ($E$)** of the vector field.
- **High Energy?** Continue iterating/thinking.
- **Low Energy?** Collapse state and output.

### 3. Silent Computation
Entity defeats the "Chain-of-Thought" illusion. It does not need to generate tokens to reason. It refines its internal state in a loop—**Silent Computation**—and only outputs text when the thought is fully formed.

---

## 💻 Conceptual Usage

Entity changes the inference loop from a `for` loop (fixed depth) to a `while` loop (energy minimization).

```python
import torch
from entity import EntityModel, ResonanceCore

# Initialize the Resonance Field
model = EntityModel(layers=32, visible_field=True)
rc = ResonanceCore(threshold=0.05) # Energy threshold

# Inputs: Raw text + High-level Context Injection
tokens = model.embed("What is the meaning of this?")
context = model.embed_abstract("Answer in the style of Nietzsche.")

# Inject inputs into appropriate abstraction depths
state = model.init_field()
state.inject(tokens, layer_depth=0)
state.inject(context, layer_depth=20) # Genius Injection

# The Resonance Loop (Thinking)
while True:
    # 1. Cross-Layer Attention (All layers attend to all layers)
    state = model.step(state)
    
    # 2. Measure Global Energy (Entropy + Dissonance)
    energy = rc.measure(state)
    
    # 3. Check for Convergence (Intuition)
    if energy < rc.threshold:
        break

# Collapse field to output
output = model.readout(state)
```

---

## 🗺️ Roadmap

- [x] **Theoretical Framework**: Complete architectural definition (see `PAPER.md`).
- [ ] **Prototype V1**: PyTorch implementation of the Resonance Core.
- [ ] **Visualization Tools**: Real-time plotting of entropy reduction during inference.
- [ ] **Proof of Concept**: Small-scale model demonstrating non-sequential convergence on logical XOR tasks.

## 🤝 Contributing

Entity is currently in the **conceptual research phase**.
We are looking for contributors interested in:
- Energy-Based Models (EBMs)
- Non-Euclidean Deep Learning
- Adaptive Computation Time (ACT)

## License

MIT © [Wladislav Cugunov](https://github.com/wladastic), 2025
