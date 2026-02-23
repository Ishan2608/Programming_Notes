# Deep Learning — Unit 1: Foundations of Neural Networks

## Table of Contents

- Chapter 1 — The Biological Neuron & the Artificial Neuron
- Chapter 2 — The McCulloch–Pitts (MCP) Neuron
- Chapter 3 — The Perceptron
- Chapter 4 — Activation Functions
- Chapter 5 — Hebbian Learning
- Chapter 6 — The Perceptron Learning Rule
- Chapter 7 — Logic Gates & Linear Separability
- Chapter 8 — Multi-Layer Perceptron & Backpropagation
- Chapter 9 — The Two Training Methods — A Critical Distinction
- Chapter 10 — Deep Neural Networks
- Numerical 1 — AND Gate Training (Method A)
- Numerical 2 — XOR Gate Training (Method B)
- Appendix — Master Formula Reference


## Chapter 1 — The Biological Neuron & the Artificial Neuron

Artificial neural networks are built on an analogy with biological neurons in the human brain. The analogy is imperfect — biological neurons are far more complex — but understanding the parallel clarifies why artificial networks are structured the way they are, and why certain design decisions (weights, thresholds, activation functions) exist at all.

### 1.1 The Biological Neuron

A biological neuron has four main structural components, each with a distinct functional role.

![Labelled Neuron](https://upload.wikimedia.org/wikipedia/commons/4/44/Complete_neuron_cell_diagram_en.svg)

| Biological Component | Role |
|---|---|
| **Dendrites** | Receive incoming signals from other neurons via synaptic connections |
| **Synapse** | The junction between neurons; controls the signal strength passed between them |
| **Cell Body (Soma)** | Accumulates all incoming signals; decides whether to fire |
| **Threshold** | The minimum accumulated signal required for the neuron to fire |
| **Axon** | Transmits the output signal to connected neurons downstream |

### 1.2 The Artificial Neuron

The artificial neuron models each biological component as a mathematical operation.

![Artificial Neuron](https://upload.wikimedia.org/wikipedia/commons/6/60/ArtificialNeuronModel_english.png)

| Biological Component | Artificial Equivalent              | Mathematical Role                               |
|----------------------|------------------------------------|-------------------------------------------------|
| Dendrites            | Inputs (x₁, x₂, ..., xₙ)           | Raw data entering the neuron                    |
| Synapse strength     | Weights (w₁, w₂, ..., wₙ)          | Scale each input's contribution                 |
| Cell Body            | Summation: z = Σ(wᵢxᵢ) + b         | Aggregate all weighted inputs                   |
| Threshold / firing   | Activation function f(z)           | Decide whether and how strongly to "fire"       |
| Axon output          | Output ŷ                           | Pass result to the next layer                   |

### 1.3 Comparing Biological and Artificial Neurons

| Property            | Biological Neuron                              | Artificial Neuron                          |
|---------------------|------------------------------------------------|--------------------------------------------|
| **Signal type**     | Electrochemical pulses (spikes)                | Scalar real numbers                        |
| **Processing speed**| ~100 operations/second/neuron                  | Billions/second on GPU                     |
| **Count in system** | ~86 billion (human brain)                      | Thousands to millions (practical)          |
| **Learning mechanism** | Synaptic plasticity — physical/chemical changes | Weight adjustment via algorithms       |
| **Energy use**      | ~20 watts (entire brain)                       | Hundreds–thousands of watts (GPU)          |
| **Fault tolerance** | High — brain adapts to neuron loss             | Low — architectural errors are critical    |
| **Parallelism**     | Massively parallel by nature                   | Simulated parallelism via hardware         |
| **Memory storage**  | Distributed across synaptic connections        | Stored in weight matrices                  |
| **Interpretability**| Poorly understood                              | Partially interpretable (weights, gradients)|

ANNs are mathematical abstractions *inspired* by biology, not biological simulations. The analogy builds intuition but should not be extended too literally.


## Chapter 2 — The McCulloch–Pitts (MCP) Neuron

The McCulloch–Pitts model (1943), proposed by neurophysiologist Warren McCulloch and logician Walter Pitts, was the first formal mathematical model of a neuron. It predates the perceptron by 15 years and established the computational vocabulary — inputs, threshold, binary output — that all later models are built upon.

### 2.1 Structure and Operation

The MCP neuron operates on **binary inputs** (0 or 1) and produces a **binary output** (0 or 1). There are no learnable weights — all inputs contribute equally. Two input types exist: excitatory (add to the sum) and inhibitory (block output entirely if active).

```
  Excitatory inputs                              Inhibitory inputs
  (each contributes +1 to sum)                   (if any = 1, output forced to 0)

   x₁ ────────────┐
   x₂ ────────────►   Σ(excitatory xᵢ)   ──►   f(S, θ)   ──►   output
   x₃ ────────────┘           ↑
                           threshold θ
                           (set manually)
```

**Decision rule:**

```
  Step 1 — Check inhibition:
      If any inhibitory input = 1  →  output = 0  (stop here)

  Step 2 — Sum excitatory inputs:
      S = x₁ + x₂ + ... + xₙ

  Step 3 — Apply threshold:
      output = 1   if S ≥ θ
      output = 0   if S < θ
```

### 2.2 Properties

| Property          | Detail                                                        |
|-------------------|---------------------------------------------------------------|
| Inputs            | Binary only: 0 or 1                                           |
| Weights           | None — all excitatory inputs contribute equally               |
| Threshold         | Fixed manually; not learned from data                         |
| Inhibitory inputs | Absolute veto — one active inhibitory input blocks all output |
| Output            | Binary: 0 or 1                                                |
| Learning          | None — the MCP model cannot be trained                        |

### 2.3 Implementing Logic Gates with MCP

By choosing appropriate thresholds, the MCP neuron implements basic Boolean logic.

| Gate | Inputs | Firing condition | Threshold θ |
|---|---|---|---|
| AND | x₁, x₂ | Both must equal 1 | θ = 2 |
| OR | x₁, x₂ | At least one must equal 1 | θ = 1 |
| NOT x₁ | x₁ (inhibitory) | Fire only when x₁ = 0 | θ = 1 with x₁ inhibitory |

**Worked example — AND gate with MCP, θ = 2:**

| x₁ | x₂ | S = x₁ + x₂ | S ≥ 2? | Output |
|---|---|---|---|---|
| 0 | 0 | 0 | No | 0 |
| 0 | 1 | 1 | No | 0 |
| 1 | 0 | 1 | No | 0 |
| 1 | 1 | 2 | Yes | **1** |

### 2.4 Limitations of MCP

1. **No learning** — the threshold is set manually; the model cannot improve from data.
2. **Binary inputs only** — real-world data is rarely binary.
3. **No weights** — all inputs contribute equally, which is unrealistic.
4. **Cannot solve XOR** — limited to linearly separable functions.
5. **Absolute inhibition** — biologically over-simplified; real inhibitory signals are graded.

These limitations directly motivated the development of the trainable Perceptron.


## Chapter 3 — The Perceptron

The Perceptron (Frank Rosenblatt, 1958) extended the MCP model by introducing **learnable real-valued weights**, making it the first model that could be trained from data. It remains the fundamental building block of all neural networks.

### 3.1 Structure

```
   x₁ ──[w₁]──┐
               │
   x₂ ──[w₂]──►   Σ(wᵢxᵢ + b)   ──►   f(z)   ──►   output
               │
   xₙ ──[wₙ]──┘

  z   = Σ(wᵢ · xᵢ) + b        ←  net input
  out = f(z)                    ←  output after activation
```

### 3.2 MCP vs. Perceptron — Direct Comparison

| Feature | MCP Neuron (1943) | Perceptron (1958) |
|---|---|---|
| Weights | None (equal contribution) | Real-valued, learnable |
| Bias | None (fixed threshold θ) | Learnable bias b |
| Inputs | Binary (0 or 1) | Real-valued |
| Threshold | Set manually | Implicit in learned bias |
| Learning | Not possible | Yes — perceptron learning rule |
| Output | Binary | Binary (step) or continuous (sigmoid) |


## Chapter 4 — Activation Functions

The activation function determines the nature of the output and, critically, which training algorithm applies. Using a step function implies Method A (perceptron rule). Using sigmoid implies Method B (gradient descent). This distinction is covered fully in Chapter 9.

| Function | Formula | Output Range | Primary Use |
|---|---|---|---|
| Step Function | `f(z) = 1 if z > 0, else 0` | {0, 1} | Perceptron learning rule |
| Sigmoid | `σ(z) = 1 / (1 + e^(−z))` | (0, 1) | Binary classification, hidden layers |
| ReLU | `f(z) = max(0, z)` | [0, ∞) | Hidden layers in deep networks |
| Tanh | `f(z) = (eᶻ − e⁻ᶻ)/(eᶻ + e⁻ᶻ)` | (−1, 1) | Hidden layers, alternative to sigmoid |
| Softmax | `pᵢ = e^(zᵢ) / Σ e^(zⱼ)` | (0,1), sums to 1 | Multi-class output layer |

**Sigmoid derivative — memorise this:**

```
  σ'(z) = σ(z) · (1 − σ(z)) = ŷ · (1 − ŷ)
```

The derivative of sigmoid at any point equals the output multiplied by one minus that output. This appears directly in backpropagation and does not need to be re-derived during a problem.


## Chapter 5 — Hebbian Learning

Hebbian learning (Donald Hebb, 1949) is one of the oldest and most influential theories in neural computation. It is a form of **unsupervised learning** — requiring no labelled data and no error signal. Its central principle is:

> *"Neurons that fire together, wire together."*

If a neuron and its input are simultaneously active, the connection between them is strengthened. If they rarely co-activate, it weakens.

### 5.1 The Hebbian Learning Rule

```
  Weight update:
      Δwᵢ = η · xᵢ · y

  Updated weight:
      wᵢ_new = wᵢ_old + η · xᵢ · y

  Where:
      η   =  learning rate
      xᵢ  =  input at connection i
      y   =  actual output of the neuron (not the desired output)
```

There is **no error term**. The update depends only on whether input and output are simultaneously active, not on whether the output was correct.

### 5.2 Worked Example

**Given:** w₁ = 0.2, w₂ = 0.5, η = 0.1, input: x₁ = 1, x₂ = 0

**Step 1 — Compute output:**

```
  y = w₁·x₁ + w₂·x₂ = 0.2(1) + 0.5(0) = 0.2
```

**Step 2 — Apply Hebbian updates:**

```
  Δw₁ = η · x₁ · y = 0.1 × 1 × 0.2 = 0.02
  Δw₂ = η · x₂ · y = 0.1 × 0 × 0.2 = 0.00   ←  x₂ = 0, connection not active

  w₁_new = 0.2 + 0.02 = 0.22
  w₂_new = 0.5 + 0.00 = 0.50   ←  unchanged
```

The connection from x₁ strengthened because x₁ and y were both active. The connection from x₂ was unchanged because x₂ was inactive — it did not fire together with the output.

### 5.3 Hebbian vs. Perceptron Rule

Both rules look structurally similar but represent entirely different philosophies.

| Property | Hebbian Learning | Perceptron Rule |
|---|---|---|
| Error signal | **None** | E = y_desired − y_out |
| Supervision | **Unsupervised** | Supervised |
| Update condition | Every pattern, every step | Only on wrong predictions |
| Update formula | `Δw = η · x · y` | `Δw = η · x · (y_desired − y_out)` |
| Goal | Strengthen co-active connections | Correct misclassifications |

The perceptron rule uses `(y_desired − y_out)` — the error. Hebbian uses `y` — the actual output. One term difference, fundamental conceptual difference.

### 5.4 Limitations of Basic Hebbian Learning

1. **Unbounded growth** — without a dampening mechanism, weights grow without limit on repeated patterns.
2. **No error correction** — the rule has no concept of "wrong" and cannot fix a bad prediction.
3. **Instability** — repeated exposure to the same input causes weights to diverge.

**Oja's Rule** addresses these by introducing a normalising decay term:

```
  Δwᵢ = η · y · (xᵢ − y · wᵢ)

  The term (−y · wᵢ) prevents unbounded weight growth.
```

### 5.5 Where Hebbian Principles Appear Today

| Area | Hebbian Principle Used |
|---|---|
| Hopfield Networks | Associative memory through co-activation |
| Self-Organising Maps (SOMs) | Unsupervised competitive learning |
| Weight initialisation strategies | Correlated inputs initialised with stronger connections |
| Neuromorphic computing | Spike-Timing Dependent Plasticity (STDP) |


## Chapter 6 — The Perceptron Learning Rule

When a perceptron uses a step activation function, it is trained via a supervised error-correction rule. If the output is wrong, nudge each weight by an amount proportional to the error and the input that caused it.

### 6.1 Algorithm

```
  Step 1 — Compute net input:
      y_in = Σ(wᵢ · xᵢ) + b

  Step 2 — Apply step activation:
      y_out = 1   if y_in > 0
      y_out = 0   if y_in ≤ 0

  Step 3 — Compute error:
      E = y_desired − y_out          ←  values: −1, 0, or +1

  Step 4 — Update only when E ≠ 0:
      wᵢ_new = wᵢ_old + η · xᵢ · E
      b_new  = b_old  + η · E

      If E = 0: correct prediction — no update.
```

### 6.2 Key Considerations

- The update uses a **plus** sign. This is not interchangeable with the minus sign in gradient descent.
- If `E = 0`, skip the update step entirely — correct predictions require no change.
- If `xᵢ = 0`, that weight does not change even on a wrong prediction, since `η · 0 · E = 0`.
- `y_out` is always exactly 0 or 1, never a decimal in this method.


## Chapter 7 — Logic Gates & Linear Separability

A single perceptron can only solve problems where the classes are **linearly separable** — where a straight line (in 2D) or hyperplane (in higher dimensions) can correctly divide the output classes in input space.

```
  AND gate — linearly separable             XOR gate — NOT linearly separable

   x₂                                        x₂
    │                \                         │
  1 │    ·  (0,1)     \  ● (1,1)             1 │    ● (0,1)        · (1,1)
    │                  \                       │
    │                   \← decision boundary   │       ✗  no single line separates these
    │                                          │
  0 │    · (0,0)       · (1,0)               0 │    · (0,0)        ● (1,0)
    │                                          │
    └──────────────────────── x₁               └──────────────────────── x₁
         0             1                            0             1

  ● = output 1     · = output 0
```

| Gate | Linearly Separable | Single Perceptron | Multi-layer Required |
|---|---|---|---|
| AND | Yes | ✓ Sufficient | Not needed |
| OR | Yes | ✓ Sufficient | Not needed |
| NAND | Yes | ✓ Sufficient | Not needed |
| XOR | **No** | ✗ Fails | **Required** |

Minsky and Papert's 1969 proof that a single perceptron cannot learn XOR nearly halted neural network research for a decade. The revival came only with multi-layer networks and backpropagation in the 1980s.


## Chapter 8 — Multi-Layer Perceptron & Backpropagation

For problems that are not linearly separable, a hidden layer introduces a non-linear boundary that enables the network to learn more complex patterns. Training such a network requires **backpropagation** — computing the output error and propagating it backwards to determine each weight's contribution, then adjusting accordingly.

![Multi-layer perceptron — input, hidden, and output layers](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Colored_neural_network.svg/600px-Colored_neural_network.svg.png)
*Source: Wikimedia Commons — Colored neural network (CC BY-SA 3.0)*

### 8.1 Forward Propagation

```
  Hidden layer:
      z_h1 = w₁·x₁ + w₂·x₂ + b_h1        z_h2 = w₃·x₁ + w₄·x₂ + b_h2
      a_h1 = σ(z_h1)                        a_h2 = σ(z_h2)

  Output layer:
      z_o = w₅·a_h1 + w₆·a_h2 + b_o
      ŷ   = σ(z_o)
```

### 8.2 Loss Functions

```
  Binary Cross-Entropy (classification):
      L = −[y · log(ŷ) + (1−y) · log(1−ŷ)]

  Mean Squared Error (regression):
      L = (1/2)(y − ŷ)²
```

### 8.3 Backpropagation Formulas

```
  Output delta:
      δ_o = (ŷ − y) · ŷ · (1 − ŷ)

  Hidden delta (for each hidden neuron, using its connecting weight to the output):
      δ_h = δ_o · w_connecting · a_h · (1 − a_h)

  Weight updates — output layer:
      w₅  = w₅  − η · δ_o · a_h1
      w₆  = w₆  − η · δ_o · a_h2
      b_o = b_o − η · δ_o

  Weight updates — hidden layer:
      w₁   = w₁   − η · δ_h1 · x₁
      w₂   = w₂   − η · δ_h1 · x₂
      w₃   = w₃   − η · δ_h2 · x₁
      w₄   = w₄   − η · δ_h2 · x₂
      b_h1 = b_h1 − η · δ_h1
      b_h2 = b_h2 − η · δ_h2
```


## Chapter 9 — The Two Training Methods — A Critical Distinction

Three learning rules have now been covered: Hebbian learning, the Perceptron Rule, and Gradient Descent with Backpropagation. The two most commonly confused — and most consequential to get right on examinations — are the Perceptron Rule (Method A) and Backpropagation (Method B).

### 9.1 Side-by-Side Comparison

| METHOD A — Perceptron Rule                     | METHOD B — Gradient Descent / Backprop          |
|------------------------------------------------|--------------------------------------------------|
| **Activation** : Step function                 | **Activation** : Sigmoid                         |
| **Output**     : Exactly 0 or 1                | **Output**     : Decimal in (0, 1)               |
| **Error**      : E = y − y_out                 | **Error**      : δ = (ŷ − y) · ŷ · (1 − ŷ)       |
|                 values: −1, 0, or +1          |                 small decimal                    |
| **Update**     : w = w + η · x · E             | **Update**     : w = w − η · δ · x               |
|                 ▲ PLUS sign                   |                 ▲ MINUS sign                     |
| **Network**    : Single-layer perceptron       | **Network**    : Multi-layer (MLP)               |
| **Used for**   : AND, OR (linear gates)        | **Used for**   : XOR, deep networks              |

### 9.2 All Three Rules at a Glance

| Rule | Update Formula | Uses Error? | Supervised? |
|---|---|---|---|
| Hebbian | `Δw = η · x · y` | No | No |
| Perceptron (A) | `Δw = η · x · (y_desired − y_out)` | Yes (binary E) | Yes |
| Backprop (B) | `Δw = −η · δ · x` | Yes (gradient δ) | Yes |

### 9.3 How to Identify the Correct Method

| Clue in the question | Method |
|---|---|
| No labels given, "co-activation," or "fire together" | Hebbian |
| Step function, binary y_out, or E = y − y_out | Method A (Perceptron Rule) |
| Sigmoid, hidden layers, δ, or "backpropagation" | Method B (Gradient Descent) |

### 9.4 Sign Confusion Within Method B

Both of the first two rows are mathematically equivalent — they produce identical weight changes. The convention must remain consistent throughout a single solution. Never mix them.

| Error term | Update rule | Verdict |
|---|---|---|
| `δ = (ŷ − y) · ŷ(1−ŷ)` | `w = w − η · δ · x` | ✓ Correct |
| `δ = (y − ŷ) · ŷ(1−ŷ)` | `w = w + η · δ · x` | ✓ Correct (equivalent) |
| `δ = (ŷ − y) · ŷ(1−ŷ)` | `w = w + η · δ · x` | ✗ Wrong — double negation |
| `δ = (y − ŷ) · ŷ(1−ŷ)` | `w = w − η · δ · x` | ✗ Wrong — double negation |

Never take the absolute value of the error in any method. The sign encodes direction; removing it causes weights to update incorrectly.

In Method B, compute all deltas (δ_o and every δ_h) using the pre-update weights. Only after all deltas are ready should any weight be changed.


## Chapter 10 — Deep Neural Networks

A Deep Neural Network is a multi-layer perceptron with more than one hidden layer. "Deep" refers to the number of layers, not the number of neurons per layer.

### 10.1 Architecture

```
  Input        Hidden 1      Hidden 2      Hidden 3     Output
  Layer        (6 nodes)   (500 nodes)    (50 nodes)    Layer
    │
    ●──────────► ●────────────► ●──────────► ●──────────► ●
    ●──────────► ●────────────► ●──────────► ●──────────► ●
    ●──────────► ●────────────► ●──────────► ●
    ●──────────► ●────────────► ●──────────► ●
    ●──────────► ●────────────► ●
    ●──────────► ●

  ◄─── Expansion ────────────────────────► ◄── Compression ──►
       (explore many feature combos)           (retain what matters)
```

### 10.2 Hierarchical Feature Learning

Each layer learns increasingly abstract representations of the input data.

| Layer depth | What is learned | Example — student performance prediction |
|---|---|---|
| Early layers | Simple, individual patterns | "Attendance is high" |
| Middle layers | Combinations of features | "High marks + low attendance → uncertain" |
| Deep layers | Abstract, predictive concepts | "This student is at risk" |

### 10.3 Expand-then-Compress Pattern

Many successful DNN architectures follow a pattern of expanding then compressing layer size (e.g., 6 → 100 → 500 → 200 → 50). Expansion forces the network to explore many possible ways of combining features. Compression distils the most predictive representations and discards redundancy.

### 10.4 Types of Deep Networks

| Type | Full Name | Best Suited For |
|---|---|---|
| DNN / MLP | Fully Connected Network | Tabular / structured data |
| CNN | Convolutional Neural Network | Images, video |
| RNN | Recurrent Neural Network | Sequential data, time series |
| LSTM / GRU | Long Short-Term Memory / Gated Recurrent Unit | Long sequences, NLP |
| GAN | Generative Adversarial Network | Synthetic data generation |
| Autoencoder | — | Dimensionality reduction, anomaly detection |


## Numerical 1 — AND Gate Training (Method A)

**Problem:** Train a single perceptron to learn the AND gate using the perceptron learning rule.

**Why Method A:** The output is binary (0 or 1) and the problem is linearly separable. Step function is appropriate. No sigmoid, no hidden layers, no backpropagation.

**AND Gate Truth Table:**

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Initial values:** w₁ = 0, w₂ = 0, b = 0, η = 0.1, threshold = 0

**Epoch 1:**

Input (0, 0), y = 0:
```
  y_in  = 0(0) + 0(0) + 0 = 0
  y_out = 0   [0 ≤ 0 → step gives 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (0, 1), y = 0:
```
  y_in  = 0(0) + 0(1) + 0 = 0
  y_out = 0   [0 ≤ 0 → step gives 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 0), y = 0:
```
  y_in  = 0(1) + 0(0) + 0 = 0
  y_out = 0   [0 ≤ 0 → step gives 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 1), y = 1:
```
  y_in  = 0(1) + 0(1) + 0 = 0
  y_out = 0   [0 ≤ 0 → step gives 0]
  E     = 1 − 0 = +1  ←  wrong prediction

  w₁ = 0 + 0.1(1)(+1) = 0.1
  w₂ = 0 + 0.1(1)(+1) = 0.1
  b  = 0 + 0.1(+1)    = 0.1
```

**State after Epoch 1:** w₁ = 0.1,  w₂ = 0.1,  b = 0.1

**Epoch 2:**

Input (0, 0), y = 0:
```
  y_in  = 0.1(0) + 0.1(0) + 0.1 = 0.1
  y_out = 1   [0.1 > 0 → step gives 1]
  E     = 0 − 1 = −1  ←  wrong prediction

  w₁ = 0.1 + 0.1(0)(−1) = 0.1   [x₁ = 0 → no change]
  w₂ = 0.1 + 0.1(0)(−1) = 0.1   [x₂ = 0 → no change]
  b  = 0.1 + 0.1(−1)    = 0.0
```

Input (0, 1), y = 0:
```
  y_in  = 0.1(0) + 0.1(1) + 0.0 = 0.1
  y_out = 1   [0.1 > 0 → step gives 1]
  E     = 0 − 1 = −1  ←  wrong prediction

  w₁ = 0.1 + 0.1(0)(−1) = 0.1   [x₁ = 0 → no change]
  w₂ = 0.1 + 0.1(1)(−1) = 0.0
  b  = 0.0 + 0.1(−1)    = −0.1
```

Input (1, 0), y = 0:
```
  y_in  = 0.1(1) + 0.0(0) − 0.1 = 0.0
  y_out = 0   [0.0 ≤ 0 → step gives 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 1), y = 1:
```
  y_in  = 0.1(1) + 0.0(1) − 0.1 = 0.0
  y_out = 0   [0.0 ≤ 0 → step gives 0]
  E     = 1 − 0 = +1  ←  wrong prediction

  w₁ = 0.1 + 0.1(1)(+1) = 0.2
  w₂ = 0.0 + 0.1(1)(+1) = 0.1
  b  = −0.1 + 0.1(+1)   = 0.0
```

**State after Epoch 2:** w₁ = 0.2,  w₂ = 0.1,  b = 0.0

Training continues until all four inputs produce E = 0 in a single epoch. Because AND is linearly separable, the perceptron convergence theorem guarantees this will happen in a finite number of epochs.


## Numerical 2 — XOR Gate Training (Method B)

**Problem:** A two-layer network (2 inputs → 2 hidden neurons → 1 output, sigmoid throughout) is trained on XOR. Perform one complete forward pass and one backward pass for input (1, 0), y = 1.

**Why Method B:** XOR is not linearly separable. A hidden layer with sigmoid activation is required. Method A with a step function cannot solve XOR.

**XOR Truth Table:**

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**Initial weights:**

| Weight | Value | Connection |
|---|---|---|
| w₁ | 0.5 | x₁ → h₁ |
| w₂ | 0.3 | x₂ → h₁ |
| w₃ | 0.4 | x₁ → h₂ |
| w₄ | 0.6 | x₂ → h₂ |
| b_h1, b_h2 | 0.0 | hidden biases |
| w₅ | 0.7 | h₁ → output |
| w₆ | 0.2 | h₂ → output |
| b_o | 0.0 | output bias |
| η | 0.5 | learning rate |

**Input:** x₁ = 1, x₂ = 0, y = 1

**Forward Pass:**

```
  Hidden layer:
      z_h1 = 0.5(1) + 0.3(0) + 0.0 = 0.5
      a_h1 = σ(0.5) = 1 / (1 + e^−0.5) ≈ 0.6225

      z_h2 = 0.4(1) + 0.6(0) + 0.0 = 0.4
      a_h2 = σ(0.4) = 1 / (1 + e^−0.4) ≈ 0.5987

  Output layer:
      z_o = 0.7(0.6225) + 0.2(0.5987) + 0.0
          = 0.4358 + 0.1197 = 0.5555

      ŷ = σ(0.5555) = 1 / (1 + e^−0.5555) ≈ 0.6354
```

Prediction ŷ = 0.6354, true label y = 1 — error exists, update required.

**Backward Pass:**

```
  Step 1 — Output delta:
      δ_o = (ŷ − y) · ŷ · (1 − ŷ)
          = (0.6354 − 1) · 0.6354 · 0.3646
          = (−0.3646) · 0.2317
          ≈ −0.0845

  Step 2 — Hidden deltas (computed before any weight is updated):
      δ_h1 = δ_o · w₅ · a_h1 · (1 − a_h1)
           = (−0.0845) · 0.7 · 0.6225 · 0.3775  ≈  −0.0139

      δ_h2 = δ_o · w₆ · a_h2 · (1 − a_h2)
           = (−0.0845) · 0.2 · 0.5987 · 0.4013  ≈  −0.0041

  Step 3 — Update output layer:
      w₅  = 0.7  − 0.5(−0.0845)(0.6225) = 0.7263
      w₆  = 0.2  − 0.5(−0.0845)(0.5987) = 0.2253
      b_o = 0.0  − 0.5(−0.0845)         = 0.0423

  Step 4 — Update hidden layer:
      w₁   = 0.5 − 0.5(−0.0139)(1) = 0.5070
      w₂   = 0.3 − 0.5(−0.0139)(0) = 0.3000   [x₂ = 0 → no change]
      w₃   = 0.4 − 0.5(−0.0041)(1) = 0.4021
      w₄   = 0.6 − 0.5(−0.0041)(0) = 0.6000   [x₂ = 0 → no change]
      b_h1 = 0.0 − 0.5(−0.0139)    = 0.0070
      b_h2 = 0.0 − 0.5(−0.0041)    = 0.0021
```

One complete training step for one input is done. This repeats for all remaining truth table rows, then cycles across many epochs until loss converges.


## Appendix — Master Formula Reference

```
  ════════════════════════════════════════════════════════════════════
    MCP NEURON
  ════════════════════════════════════════════════════════════════════
    Output  =  1   if  Σ(excitatory xᵢ) ≥ θ  AND  no inhibitory input active
            =  0   otherwise

  ════════════════════════════════════════════════════════════════════
    ACTIVATION FUNCTIONS
  ════════════════════════════════════════════════════════════════════
    Sigmoid              σ(z) = 1 / (1 + e^(−z))
    Sigmoid derivative   ŷ · (1 − ŷ)
    ReLU                 max(0, x)

  ════════════════════════════════════════════════════════════════════
    HEBBIAN LEARNING
  ════════════════════════════════════════════════════════════════════
    Update              Δwᵢ = η · xᵢ · y
    New weight          wᵢ  = wᵢ + η · xᵢ · y
    Oja's Rule          Δwᵢ = η · y · (xᵢ − y · wᵢ)

  ════════════════════════════════════════════════════════════════════
    METHOD A — PERCEPTRON RULE
  ════════════════════════════════════════════════════════════════════
    Net input           y_in  = Σ(wᵢ · xᵢ) + b
    Activation          y_out = 1  if y_in > 0  else  0
    Error               E     = y_desired − y_out
    Weight update       wᵢ    = wᵢ + η · xᵢ · E          ← PLUS
    Bias update         b     = b  + η · E

  ════════════════════════════════════════════════════════════════════
    METHOD B — GRADIENT DESCENT / BACKPROPAGATION
  ════════════════════════════════════════════════════════════════════
    Forward             z = Wx + b;    a = σ(z)
    Output δ            δ_o = (ŷ − y) · ŷ · (1 − ŷ)
    Hidden δ            δ_h = δ_o · w_connecting · a_h · (1 − a_h)
    Weight update       w   = w − η · δ · (input to that weight)   ← MINUS
    Bias update         b   = b − η · δ
```
