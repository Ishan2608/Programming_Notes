# Deep Learning — Units 1 & 2 Study Notes

---

# UNIT 1 — Neural Networks & Backpropagation

---

## 1. Perceptron

The perceptron is the fundamental unit of a neural network — a single artificial neuron. It receives one or more inputs, computes a weighted sum of them, adds a bias, and passes the result through an activation function to produce an output.

```
         x1 ──[w1]───┐
                     │
         x2 ──[w2]──►[Σ(wᵢxᵢ + b)] ──► f(z) ──►  output
                     │
         xn ──[wn]───┘
```

**Formula:**
```
z   = Σ(wᵢ · xᵢ) + b        ←  net input
out = f(z)                    ←  output after activation
```

---

## 2. Activation Functions

The activation function determines the nature of the output. Crucially, the choice of activation function also determines which training algorithm applies.

| Function | Formula | Output Range | Primary Use |
|---|---|---|---|
| Step Function | `f(z) = 1 if z > 0, else 0` | {0, 1} | Classic perceptron training |
| Sigmoid | `σ(z) = 1 / (1 + e^(−z))` | (0, 1) | Binary classification, hidden layers |
| ReLU | `f(z) = max(0, z)` | [0, ∞) | Hidden layers in deep networks |
| Tanh | `f(z) = (eᶻ − e⁻ᶻ)/(eᶻ + e⁻ᶻ)` | (−1, 1) | Hidden layers, alternative to sigmoid |
| Softmax | `pᵢ = e^(zᵢ) / Σ e^(zⱼ)` | (0,1), sums to 1 | Multi-class output layer |

**Sigmoid derivative — memorise this:**
```
σ'(z) = σ(z) · (1 − σ(z)) = ŷ · (1 − ŷ)
```
The derivative of sigmoid at any point equals the output at that point multiplied by one minus that output. This is used directly in backpropagation without re-deriving from scratch.

---

## 3. Perceptron Learning Rule (Step Function)

When a perceptron uses a step function, training follows a simple error-correction rule: if the output is wrong, nudge each weight by an amount proportional to the error and the input that caused it.

```
  Step 1 — Compute net input:
      y_in = Σ(wᵢ · xᵢ) + b

  Step 2 — Apply step activation:
      y_out = 1   if y_in > 0
      y_out = 0   if y_in ≤ 0

  Step 3 — Compute error:
      E = y_desired − y_out          (values: −1, 0, or +1)

  Step 4 — Update (only when E ≠ 0):
      wᵢ_new = wᵢ_old + η · xᵢ · E
      b_new  = b_old  + η · E

      If E = 0: correct prediction — no update performed.
```

**Key considerations:**
- The update uses a **plus** sign. This is not interchangeable with the minus used in gradient descent.
- If `E = 0`, skip the update step entirely — regardless of any other values.
- If `xᵢ = 0`, that weight will not change even if the prediction is wrong, since `η · 0 · E = 0`.
- `y_out` is always exactly 0 or 1, never a decimal.

---

## 4. Logic Gates and Linear Separability

A single perceptron can only solve problems where the classes are **linearly separable** — where a straight line can correctly divide the output classes in the input space.

```
  AND gate — linearly separable          XOR gate — NOT linearly separable

  x2                                     x2
   │                                      │
 1 │    ·  (0,1)      \  ● (1,1)        1 │    ● (0,1)        · (1,1)
   │                   \                  │
   │                    \ ← boundary      │       ✗  no single line works
   │                                      │
 0 │    · (0,0)        · (1,0)          0 │    · (0,0)        ● (1,0)
   │                                      │
   └──────────────────────── x1           └──────────────────────── x1
        0            1                         0            1

  ● = output 1     · = output 0
```

| Gate | Linearly Separable | Single Perceptron | Multi-layer Required |
|---|---|---|---|
| AND | Yes | ✓ Sufficient | Not needed |
| OR | Yes | ✓ Sufficient | Not needed |
| NAND | Yes | ✓ Sufficient | Not needed |
| XOR | **No** | ✗ Fails | **Required** |

---

## 5. Multi-Layer Perceptron (MLP) and Backpropagation

For problems that are not linearly separable (such as XOR), a hidden layer is required. The hidden layer allows the network to form a non-linear decision boundary. Training such a network requires **backpropagation** — propagating the output error backwards through the network to determine how much each weight contributed, then adjusting each weight accordingly.

![Multi-layer perceptron with one hidden layer](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Colored_neural_network.svg/600px-Colored_neural_network.svg.png)
*Source: Wikimedia Commons — Colored neural network (CC BY-SA 3.0)*

### Forward Propagation

```
  Hidden layer:
      z_h1 = w1·x1 + w2·x2 + b_h1        z_h2 = w3·x1 + w4·x2 + b_h2
      a_h1 = σ(z_h1)                       a_h2 = σ(z_h2)

  Output layer:
      z_o = w5·a_h1 + w6·a_h2 + b_o
      ŷ   = σ(z_o)
```

### Loss Functions

```
  Binary Cross-Entropy (classification):
      L = −[y · log(ŷ) + (1−y) · log(1−ŷ)]

  Mean Squared Error (regression):
      L = (1/2)(y − ŷ)²
```

### Backpropagation Formulas

```
  Output delta:
      δ_o = (ŷ − y) · ŷ · (1 − ŷ)

  Hidden delta (per hidden neuron h, using its weight to the output):
      δ_h = δ_o · w_connecting · a_h · (1 − a_h)

  Weight updates — output layer:
      w5  = w5  − η · δ_o · a_h1
      w6  = w6  − η · δ_o · a_h2
      b_o = b_o − η · δ_o

  Weight updates — hidden layer:
      w1   = w1   − η · δ_h1 · x1
      w2   = w2   − η · δ_h1 · x2
      w3   = w3   − η · δ_h2 · x1
      w4   = w4   − η · δ_h2 · x2
      b_h1 = b_h1 − η · δ_h1
      b_h2 = b_h2 − η · δ_h2
```

---

## 6. The Two Training Methods — Distinguishing Them

Two weight update methods have been introduced across this course. They appear similar on the surface but are fundamentally different algorithms. Applying the wrong method to a given problem produces incorrect results.

| **METHOD A — Perceptron Rule**                            | **METHOD B — Gradient Descent / Backprop**                                           |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Activation:** Step function                             | **Activation:** Sigmoid                                                              |
| **Output:** exactly 0 or 1                                | **Output:** decimal in (0, 1)                                                        |
| **Error:** ( E = y - y_{out} )  (values: −1, 0, +1)       | **Error:** ( \delta = (\hat{y} - y)\cdot \hat{y}\cdot (1-\hat{y}) )  (small decimal) |
| **Update:** ( w = w + \eta \cdot x \cdot E )  (plus sign) | **Update:** ( w = w - \eta \cdot \delta \cdot x )  (minus sign)                      |
| **Network:** Single-layer perceptron                      | **Network:** Multi-layer (MLP)                                                       |
| **Used for:** AND, OR (linear gates)                      | **Used for:** XOR, deep networks                                                     |


**Identifying the correct method from a question:**

| Clue in the question | Method to use |
|---|---|
| "y_out = 1 if y_in > threshold" | Method A |
| Output shown as exactly 0 or 1 | Method A |
| "sigmoid activation" or "σ" mentioned | Method B |
| Network has hidden layers | Method B |
| "backpropagation" or "δ" used | Method B |
| "gradient descent" or "chain rule" | Method B |

**Sign confusion within Method B:**

Both of the first two rows are mathematically equivalent and produce an identical weight change. The convention must stay consistent throughout a single solution.

| Error term | Update rule | Verdict |
|---|---|---|
| `δ = (ŷ − y) · ŷ(1−ŷ)` | `w = w − η · δ · x` | ✓ Correct |
| `δ = (y − ŷ) · ŷ(1−ŷ)` | `w = w + η · δ · x` | ✓ Correct (equivalent) |
| `δ = (ŷ − y) · ŷ(1−ŷ)` | `w = w + η · δ · x` | ✗ Wrong — double negation |
| `δ = (y − ŷ) · ŷ(1−ŷ)` | `w = w − η · δ · x` | ✗ Wrong — double negation |

**On absolute values:** Never take the absolute value of the error in either method. The sign encodes direction. Removing it causes weights to update in the wrong direction.

**Order of operations in Method B:** All deltas (δ_o and every δ_h) must be computed using the pre-update weights. Only after all deltas are in hand should any weight be changed.

---

## 7. Sample Numerical 1 — AND Gate (Method A)

**Problem:** Train a single perceptron to learn the AND gate using the perceptron learning rule.

**AND Gate Truth Table:**

| x1 | x2 | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Initial values:** w1 = 0, w2 = 0, b = 0, η = 0.1, threshold = 0

---

**Epoch 1:**

Input (0, 0), y = 0:
```
  y_in  = 0(0) + 0(0) + 0 = 0
  y_out = 0   [0 ≤ 0 → output 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (0, 1), y = 0:
```
  y_in  = 0(0) + 0(1) + 0 = 0
  y_out = 0   [0 ≤ 0 → output 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 0), y = 0:
```
  y_in  = 0(1) + 0(0) + 0 = 0
  y_out = 0   [0 ≤ 0 → output 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 1), y = 1:
```
  y_in  = 0(1) + 0(1) + 0 = 0
  y_out = 0   [0 ≤ 0 → output 0]
  E     = 1 − 0 = +1  ←  wrong prediction

  w1 = 0 + 0.1(1)(+1) = 0.1
  w2 = 0 + 0.1(1)(+1) = 0.1
  b  = 0 + 0.1(+1)    = 0.1
```

**After Epoch 1:** w1 = 0.1, w2 = 0.1, b = 0.1

---

**Epoch 2:**

Input (0, 0), y = 0:
```
  y_in  = 0.1(0) + 0.1(0) + 0.1 = 0.1
  y_out = 1   [0.1 > 0 → output 1]
  E     = 0 − 1 = −1  ←  wrong prediction

  w1 = 0.1 + 0.1(0)(−1) = 0.1   [x1 = 0, no change]
  w2 = 0.1 + 0.1(0)(−1) = 0.1   [x2 = 0, no change]
  b  = 0.1 + 0.1(−1)    = 0.0
```

Input (0, 1), y = 0:
```
  y_in  = 0.1(0) + 0.1(1) + 0.0 = 0.1
  y_out = 1   [0.1 > 0 → output 1]
  E     = 0 − 1 = −1  ←  wrong prediction

  w1 = 0.1 + 0.1(0)(−1) = 0.1   [x1 = 0, no change]
  w2 = 0.1 + 0.1(1)(−1) = 0.0
  b  = 0.0 + 0.1(−1)    = −0.1
```

Input (1, 0), y = 0:
```
  y_in  = 0.1(1) + 0.0(0) − 0.1 = 0.0
  y_out = 0   [0.0 ≤ 0 → output 0]
  E     = 0 − 0 = 0  →  No update.
```

Input (1, 1), y = 1:
```
  y_in  = 0.1(1) + 0.0(1) − 0.1 = 0.0
  y_out = 0   [0.0 ≤ 0 → output 0]
  E     = 1 − 0 = +1  ←  wrong prediction

  w1 = 0.1 + 0.1(1)(+1) = 0.2
  w2 = 0.0 + 0.1(1)(+1) = 0.1
  b  = −0.1 + 0.1(+1)   = 0.0
```

**After Epoch 2:** w1 = 0.2, w2 = 0.1, b = 0.0

Training continues until all four inputs produce E = 0 in a single epoch. Because AND is linearly separable, convergence is guaranteed.

---

## 8. Sample Numerical 2 — XOR Gate (Method B)

**Problem:** A two-layer network (2 inputs → 2 hidden neurons → 1 output, sigmoid throughout) is trained on XOR. Perform one forward pass and one backward pass for input (1, 0), y = 1.

**Why Method B applies:** XOR is not linearly separable. A hidden layer with sigmoid activation is required, which mandates gradient descent and backpropagation. Method A with a step function cannot represent this problem.

**XOR Truth Table:**

| x1 | x2 | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**Initial weights:**

| Weight | Value | Connection |
|---|---|---|
| w1 | 0.5 | x1 → h1 |
| w2 | 0.3 | x2 → h1 |
| w3 | 0.4 | x1 → h2 |
| w4 | 0.6 | x2 → h2 |
| b_h1, b_h2 | 0.0 | hidden biases |
| w5 | 0.7 | h1 → output |
| w6 | 0.2 | h2 → output |
| b_o | 0.0 | output bias |
| η | 0.5 | learning rate |

**Input:** x1 = 1, x2 = 0, y = 1

---

### Forward Pass

```
  Hidden layer:
      z_h1 = 0.5(1) + 0.3(0) + 0.0 = 0.5
      a_h1 = σ(0.5) = 1/(1 + e^−0.5) ≈ 0.6225

      z_h2 = 0.4(1) + 0.6(0) + 0.0 = 0.4
      a_h2 = σ(0.4) = 1/(1 + e^−0.4) ≈ 0.5987

  Output layer:
      z_o = 0.7(0.6225) + 0.2(0.5987) + 0.0
          = 0.4358 + 0.1197 = 0.5555

      ŷ = σ(0.5555) = 1/(1 + e^−0.5555) ≈ 0.6354
```

Prediction ŷ = 0.6354, true label y = 1 — error exists, update required.

---

### Backward Pass

```
  Step 1 — Output delta:
      δ_o = (ŷ − y) · ŷ · (1 − ŷ)
          = (0.6354 − 1) · 0.6354 · 0.3646
          = (−0.3646) · 0.2317
          ≈ −0.0845

  Step 2 — Hidden deltas (computed before any weight is updated):
      δ_h1 = δ_o · w5 · a_h1 · (1 − a_h1)
           = (−0.0845) · 0.7 · 0.6225 · 0.3775 ≈ −0.0139

      δ_h2 = δ_o · w6 · a_h2 · (1 − a_h2)
           = (−0.0845) · 0.2 · 0.5987 · 0.4013 ≈ −0.0041

  Step 3 — Update output layer:
      w5  = 0.7  − 0.5(−0.0845)(0.6225) = 0.7263
      w6  = 0.2  − 0.5(−0.0845)(0.5987) = 0.2253
      b_o = 0.0  − 0.5(−0.0845)         = 0.0423

  Step 4 — Update hidden layer:
      w1   = 0.5 − 0.5(−0.0139)(1) = 0.5070
      w2   = 0.3 − 0.5(−0.0139)(0) = 0.3000   [x2 = 0, no change]
      w3   = 0.4 − 0.5(−0.0041)(1) = 0.4021
      w4   = 0.6 − 0.5(−0.0041)(0) = 0.6000   [x2 = 0, no change]
      b_h1 = 0.0 − 0.5(−0.0139)   = 0.0070
      b_h2 = 0.0 − 0.5(−0.0041)   = 0.0021
```

One complete training step for one input is done. This process repeats for all remaining truth table rows, then cycles across many epochs until the loss converges.

---

## 9. Deep Neural Networks (DNN)

A Deep Neural Network is a multi-layer perceptron with more than one hidden layer. "Deep" refers to the number of layers, not the number of neurons per layer.

```
  Input     Hidden 1    Hidden 2    Hidden 3    Output
    │       (6 nodes)  (500 nodes)  (50 nodes)    │
    ●─────►  ●  ─────►  ●  ─────►  ●  ─────►    ●
    ●─────►  ●  ─────►  ●  ─────►  ●  ─────►    ●
    ●─────►  ●  ─────►  ●  ─────►  ●
    ●─────►  ●  ─────►  ●  ─────►  ●
    ●─────►  ●  ─────►  ●
    ●─────►  ●

  ◄── Expansion ──────────────────► ◄── Compression ──────►
      (explore many feature combinations)  (retain what predicts output)
```

**Hierarchical feature learning:**

| Layer depth | What is learned | Example (student grade prediction) |
|---|---|---|
| Early layers | Simple, individual patterns | "Attendance is high" |
| Middle layers | Feature combinations | "High marks + low attendance → uncertain" |
| Deep layers | Abstract concepts | "This is an at-risk student" |

**Types of deep networks:**

| Type | Best suited for |
|---|---|
| DNN / MLP (Fully Connected) | Tabular / structured data |
| CNN | Images, video |
| RNN / LSTM / GRU | Sequences, time series, NLP |
| GAN | Synthetic data generation |
| Autoencoder | Dimensionality reduction, anomaly detection |

---

---

# UNIT 2 — Convolutional Neural Networks (CNNs)

---

## 1. Motivation for CNNs

A fully connected network applied to image data faces two fundamental problems:

1. **Parameter explosion:** A 224×224×3 image has 150,528 inputs. One layer of 1,000 neurons requires ~150 million parameters in that layer alone.
2. **No spatial awareness:** Flattening an image into a vector discards all neighbourhood relationships between pixels.

CNNs address both by using **convolution** — a small filter slides across the image applying the same weights at every position. This is called weight sharing.

```
  MLP on 224×224×3 image, 1000 neurons  →  ~150,000,000 parameters per layer
  CNN with 32 filters of 3×3            →   32 × (3×3×3 + 1) = 896 parameters
```

---

## 2. Convolution Operation

A filter of fixed size is placed at each location in the image. Element-wise products between the filter and the image patch beneath it are summed to yield one output value. The filter then slides to the next position.

```
  Image patch:          Filter:             Result:

  ┌─────┬─────┐        ┌─────┬─────┐
  │  1  │  2  │        │  1  │  0  │      (1×1)+(2×0)
  ├─────┼─────┤   ×    ├─────┼─────┤   =  (0×0)+(1×1)  =  2
  │  0  │  1  │        │  0  │  1  │
  └─────┴─────┘        └─────┴─────┘
```

**Formula:**
```
  Output[i, j] = Σ_m Σ_n ( Input[i+m, j+n] × Filter[m, n] ) + bias
```

### Output Size Formulas

```
  Convolution:    Output_size = floor( (N − F + 2P) / S ) + 1
  Pooling:        Output_size = floor( (N − F) / S ) + 1

      N = input size     F = filter size     P = padding     S = stride
```

### Terminology

| Term | Definition |
|---|---|
| Filter / Kernel | Small matrix of learnable weights slid across the input |
| Stride | Number of positions the filter moves each step |
| Padding | Zeros added around the border to control output size |
| Feature Map | Output produced by sliding one filter across the full input |
| Depth / Channels | Number of filters applied; equals number of output feature maps |
| Receptive Field | Region of the input that influences a given output neuron |

---

## 3. Pooling

Pooling reduces spatial dimensions by summarising each small region with a single value, reducing computation and adding translation invariance.

```
  Feature map (4×4)                     After Max Pool 2×2, stride 2  →  Output (2×2)

  ┌──────┬──────┬──────┬──────┐          top-left  max(1,3,5,6) = 6    ┌──────┬──────┐
  │   1  │   3  │   2  │   4  │          top-right max(2,4,1,3) = 4    │   6  │   4  │
  ├──────┼──────┼──────┼──────┤          bot-left  max(2,8,4,7) = 8    ├──────┼──────┤
  │   5  │   6  │   1  │   3  │          bot-right max(3,5,6,9) = 9    │   8  │   9  │
  ├──────┼──────┼──────┼──────┤                                        └──────┴──────┘
  │   2  │   8  │   3  │   5  │
  ├──────┼──────┼──────┼──────┤
  │   4  │   7  │   6  │   9  │
  └──────┴──────┴──────┴──────┘
```

| Type | Operation | Parameters |
|---|---|---|
| Max Pooling | Maximum of each region | 0 |
| Average Pooling | Average of each region | 0 |
| Global Max Pooling | Single maximum across entire map → 1×1 | 0 |
| Global Average Pooling | Single average across entire map → 1×1 | 0 |

Pooling layers have **no learnable parameters**.

---

## 4. Standard CNN Pipeline

```
  ┌─────────────────┐
  │   Input Image   │
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │   Conv Layer    │  ←  filter slides over image, produces feature maps
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │      ReLU       │  ←  f(x) = max(0, x)  — zeros out negatives
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │   Pool Layer    │  ←  shrinks spatial size, retains strong signals
  └────────┬────────┘
           │
      (repeat block
       as needed)
           │
           ▼
  ┌─────────────────┐
  │     Flatten     │  ←  [H × W × C]  →  [H·W·C]  1-D vector
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │   FC (Dense)    │  ←  standard MLP — combines all learned features
  └────────┬────────┘
           │
           ▼
  ┌─────────────────┐
  │     Output      │  ←  Softmax (multi-class) or Sigmoid (binary)
  └─────────────────┘
```

---

## 5. Parameter Counting

### Convolutional Layer
```
  Parameters = ( F_h × F_w × C_in + 1 ) × C_out

      F_h, F_w  =  filter height and width
      C_in      =  input depth (number of channels)
      C_out     =  number of filters (output depth)
      +1        =  one bias per filter
```

### Pooling Layer
```
  Parameters = 0       ←  no learnable parameters
```

### Fully Connected Layer
```
  Parameters = ( Inputs × Neurons ) + Neurons
```

---

## 6. Famous CNN Architectures

---

### LeNet-5 (1998)

The first successful CNN, built for handwritten digit recognition on MNIST.

```
  Input       Conv1       Pool1       Conv2       Pool2        FC Layers       Out
  32×32×1    28×28×6    14×14×6    10×10×16     5×5×16
     │           │           │           │           │              │            │
     └──[5×5,   ─►└──[Avg   ─►└──[5×5,  ─►└──[Avg   ─►└──[Flatten]──►[FC:120]──►[FC:84]──►[10]
         6f]        2×2]        16f]        2×2]
```

| Property | Detail |
|---|---|
| Parameters | ~60,000 |
| Activation | Tanh / Sigmoid |
| Significance | First CNN deployed in production (bank cheque reading) |

---

### AlexNet (2012)

Won ImageNet 2012 by a large margin. Launched the modern deep learning era.

```
  In          Conv1         Pool1      Conv2        Pool2
  224×224×3  55×55×96     27×27×96   27×27×256   13×13×256
     │            │             │          │            │
     └─[11×11,   ─►└─[Max 3×3, ─►└─[5×5,  ─►└─[Max 3×3,─►
         96f,s=4]      s=2]         256f]       s=2]

     Conv3       Conv4       Conv5       Pool3         FC Layers          Out
    13×13×384  13×13×384  13×13×256    6×6×256
        │           │           │           │               │              │
   ─────►└─[3×3,   ─►└─[3×3,   ─►└─[Max    ─►└─[FC:4096]──►[FC:4096]──►[1000]
              384f]      256f]     3×3,s=2]                              Softmax
```

| Property | Detail |
|---|---|
| Parameters | ~60 million |
| Activation | **ReLU** — first large-scale use; eliminated vanishing gradients in shallow layers |
| Key innovations | ReLU, Dropout regularisation, GPU training, Data augmentation |

---

### VGGNet (2014)

Demonstrated that stacking many small 3×3 filters systematically outperforms larger filters in fewer layers.

```
  In          Block 1      Block 2       Block 3         Block 4         Block 5
  224×224×3  224×224×64  112×112×128   56×56×256       28×28×512       14×14×512
     │            │             │              │               │               │
     └─[C3,C3]───►└─[P]─[C3,C3]─►└─[P]─[C3,C3,C3]─►└─[P]─[C3,C3,C3]─►└─[P]─[C3,C3,C3]─►[P]
                  MaxPool         MaxPool                MaxPool               MaxPool       MaxPool

  C3 = Conv 3×3       After Block 5: 7×7×512
                           │
                           └──►[FC:4096]──►[FC:4096]──►[FC:1000]──►Softmax
```

| Property | Detail |
|---|---|
| Versions | VGG-16 (13 conv + 3 FC layers), VGG-19 (16 conv + 3 FC layers) |
| Parameters | ~138 million |
| Key insight | Two stacked 3×3 layers cover the same receptive field as one 5×5 with fewer parameters and more non-linearity |

---

### GoogLeNet / Inception (2014)

Rather than choosing one filter size, the Inception module applies multiple sizes in parallel and concatenates their outputs. The network learns which responses are most useful.

```
  Inception Module:

                    ┌─────────────────────────────────────────────────────┐
                    │  1×1 Conv ──────────────────────────────────────►   │
                    │                                                     │
  Input ───────────►│  1×1 Conv ──► 3×3 Conv ────────────────────────►    ├──► Concat ──► Output
                    │                                                     │
                    │  1×1 Conv ──► 5×5 Conv ────────────────────────►    │
                    │                                                     │
                    │  MaxPool 3×3 ──► 1×1 Conv ─────────────────────►    │
                    └─────────────────────────────────────────────────────┘

  Note: 1×1 Conv before 3×3 / 5×5 reduces depth first (much cheaper computation)
```

```
  Full GoogLeNet (simplified):

  In ──►[Stem]──►[Inc×2]──►[Pool]──►[Inc×5]──►[Pool]──►[Inc×2]──►[AvgPool]──►[Dropout]──►[FC:1000]
         Conv+Pool  blocks   3×3      blocks    3×3      blocks
```

| Property | Detail |
|---|---|
| Layers | 22 weight layers |
| Parameters | ~5 million (far fewer than VGG at 22 layers) |
| Key innovation | Inception module; 1×1 convolutions for channel-wise dimension reduction |

---

### ResNet (2015)

Very deep networks suffer from **vanishing gradients** — error signals shrink as they travel back through many layers, eventually causing weight updates to stall. ResNet solves this with **skip connections** that allow gradients to bypass one or more layers entirely.

```
  Residual Block:

  Input x
     │
     ├───────────────────────────────────────┐
     │                                       │  ← skip / identity connection
     ▼                                       │
  ┌─────────────────────┐                    │
  │     Conv 3×3        │                    │
  │     BatchNorm       │                    │
  │     ReLU            │                    │
  │     Conv 3×3        │                    │
  │     BatchNorm       │                    │
  └──────────┬──────────┘                    │
             │                               │
             ▼                               │
           F(x)   +  ◄──────────────────────── x
             │
           ReLU
             │
             ▼
           H(x) = F(x) + x
```

The block learns only the residual `F(x) = H(x) − x`, not the full mapping. If no transformation is needed, the block drives `F(x) → 0` and the input passes through unchanged.

```
  ResNet-50 (simplified):

  In          Conv1       Pool      Layer 1      Layer 2      Layer 3      Layer 4      Out
  224×224×3  112×112×64  56×56×64  56×56×256   28×28×512  14×14×1024    7×7×2048
     │            │           │        │            │            │            │           │
     └─[7×7,64]──►└─[MaxPool]──►└─[×3]──►└─[×4]─────►└─[×6]─────►└─[×3]─────►└─[AvgPool]──►[FC:1000]
                                  resid.   resid.      resid.      resid.
                                  blocks   blocks      blocks      blocks
```

| Property | Detail |
|---|---|
| Versions | ResNet-50, ResNet-101, ResNet-152 |
| Parameters (ResNet-50) | ~25 million |
| Key innovation | Skip connections — solved vanishing gradient at extreme depth |
| Achievement | First model to surpass human-level accuracy on ImageNet |

---

### Architecture Comparison

| **Architecture** | **Year** | **Layers** | **Parameters** | **Primary Innovation**          |
| ---------------- | -------- | ---------- | -------------- | ------------------------------- |
| LeNet-5          | 1998     | 7          | ~60K           | First working CNN               |
| AlexNet          | 2012     | 8          | ~60M           | ReLU, Dropout, GPU training     |
| VGGNet           | 2014     | 16–19      | ~138M          | Depth with uniform 3×3 filters  |
| GoogLeNet        | 2014     | 22         | ~5M            | Inception module, 1×1 conv      |
| ResNet           | 2015     | 50–152     | ~25M           | Skip connections, extreme depth |


---

## 7. Predefined Filters (Image Processing)

### Edge Detection

| Filter | Detects | Kernel (3×3) |
|---|---|---|
| Sobel X | Vertical edges | `[−1, 0, +1 / −2, 0, +2 / −1, 0, +1]` |
| Sobel Y | Horizontal edges | `[−1, −2, −1 / 0, 0, 0 / +1, +2, +1]` |
| Laplacian | All-direction edges | `[0, 1, 0 / 1, −4, 1 / 0, 1, 0]` |
| Canny | Clean, thin edges | Multi-step: Gaussian blur → Gradient magnitude → Non-max suppression → Thresholding |

### Blur / Smoothing

| Filter | Operation | Kernel (3×3) |
|---|---|---|
| Box / Average | Replace each pixel with mean of neighbourhood | All values = 1/9 |
| Gaussian | Replace with centre-weighted mean | `(1/16)[1,2,1 / 2,4,2 / 1,2,1]` |

### Sharpening

| Filter | Operation | Kernel (3×3) |
|---|---|---|
| Sharpen | Enhance edges, increase local contrast | `[0, −1, 0 / −1, 5, −1 / 0, −1, 0]` |

---

## 8. Padding — Reference

| Type | Padding value | Output size | Use case |
|---|---|---|---|
| Valid | P = 0 | Smaller than input | Default; no border treatment |
| Same | P = (F−1)/2 | Equal to input | Preserve spatial dimensions across layers |

---

## 9. Sample Numerical 3 — Parameter Counting

**Given architecture:**

| Layer | Type | Configuration |
|---|---|---|
| 1 | Conv | 32 filters, 3×3, input = 28×28×1 |
| 2 | MaxPool | 2×2, stride = 2 |
| 3 | Conv | 64 filters, 3×3 |
| 4 | MaxPool | 2×2, stride = 2 |
| 5 | Flatten | — |
| 6 | Dense | 128 neurons |
| 7 | Dense Output | 10 neurons |

Assumptions: no padding, stride = 1 for conv layers unless stated.

---

**Layer 1 — Conv (32 filters, 3×3, input depth = 1):**
```
  Parameters   = (3 × 3 × 1 + 1) × 32 = 10 × 32 = 320
  Output size  = (28 − 3)/1 + 1 = 26
  Output volume: 26 × 26 × 32
```

**Layer 2 — MaxPool (2×2, stride 2):**
```
  Parameters   = 0
  Output size  = (26 − 2)/2 + 1 = 13
  Output volume: 13 × 13 × 32
```

**Layer 3 — Conv (64 filters, 3×3, input depth = 32):**
```
  Parameters   = (3 × 3 × 32 + 1) × 64 = 289 × 64 = 18,496
  Output size  = (13 − 3)/1 + 1 = 11
  Output volume: 11 × 11 × 64
```

**Layer 4 — MaxPool (2×2, stride 2):**
```
  Parameters   = 0
  Output size  = floor((11 − 2)/2) + 1 = 5
  Output volume: 5 × 5 × 64
```

**Layer 5 — Flatten:**
```
  Parameters   = 0
  Output       = 5 × 5 × 64 = 1,600 values
```

**Layer 6 — Dense (128 neurons):**
```
  Parameters   = (1,600 × 128) + 128 = 204,928
```

**Layer 7 — Output Dense (10 neurons):**
```
  Parameters   = (128 × 10) + 10 = 1,290
```

**Total:**
```
  320 + 0 + 18,496 + 0 + 0 + 204,928 + 1,290 = 225,034
```

The flatten-to-dense transition accounts for over 90% of all parameters, illustrating why convolutional layers are far more parameter-efficient than fully connected layers for image data.

---

## 10. Sample Numerical 4 — Full CNN Pipeline

**Given:**
```
  Input X (4×4):               Filter W (2×2):

  ┌────┬────┬────┬────┐         ┌────┬────┐
  │  1 │  2 │  0 │  1 │         │  2 │  3 │
  ├────┼────┼────┼────┤         ├────┼────┤
  │  3 │  1 │  2 │  2 │         │  1 │  1 │
  ├────┼────┼────┼────┤         └────┴────┘
  │  0 │  1 │  1 │  3 │
  ├────┼────┼────┼────┤         Padding P = 1
  │  2 │  2 │  0 │  1 │         Stride  S = 1
  └────┴────┴────┴────┘         ReLU activation
                                 MaxPool 2×2, Pool Stride = 2
```

---

**Step 1 — Convolution output size:**
```
  Output_size = (4 − 2 + 2×1)/1 + 1 = 5     →     feature map = 5×5
```

**Step 2 — Padded image (6×6):**
```
  ┌────┬────┬────┬────┬────┬────┐
  │  0 │  0 │  0 │  0 │  0 │  0 │
  ├────┼────┼────┼────┼────┼────┤
  │  0 │  1 │  2 │  0 │  1 │  0 │
  ├────┼────┼────┼────┼────┼────┤
  │  0 │  3 │  1 │  2 │  2 │  0 │
  ├────┼────┼────┼────┼────┼────┤
  │  0 │  0 │  1 │  1 │  3 │  0 │
  ├────┼────┼────┼────┼────┼────┤
  │  0 │  2 │  2 │  0 │  1 │  0 │
  ├────┼────┼────┼────┼────┼────┤
  │  0 │  0 │  0 │  0 │  0 │  0 │
  └────┴────┴────┴────┴────┴────┘
```

**Step 3 — Convolution** (filter W slid over padded image, stride = 1):

Sample positions — first row of output:
```
  Pos(1,1): patch [0,0 / 0,1]  →  (0×2)+(0×3)+(0×1)+(1×1) = 1
  Pos(1,2): patch [0,0 / 1,2]  →  (0×2)+(0×3)+(1×1)+(2×1) = 3
  Pos(1,3): patch [0,0 / 2,0]  →  (0×2)+(0×3)+(2×1)+(0×1) = 2
  Pos(1,4): patch [0,0 / 0,1]  →  (0×2)+(0×3)+(0×1)+(1×1) = 1
  Pos(1,5): patch [0,0 / 1,0]  →  (0×2)+(0×3)+(1×1)+(0×1) = 1
```

**Full feature map (5×5) after all positions:**
```
  ┌─────┬─────┬─────┬─────┬─────┐
  │   1 │   3 │   2 │   1 │   1 │
  ├─────┼─────┼─────┼─────┼─────┤
  │   6 │  12 │   7 │   7 │   4 │
  ├─────┼─────┼─────┼─────┼─────┤
  │   9 │  10 │  10 │  14 │   7 │
  ├─────┼─────┼─────┼─────┼─────┤
  │   2 │   7 │   7 │  12 │   7 │
  ├─────┼─────┼─────┼─────┼─────┤
  │   6 │  10 │   4 │   1 │   2 │
  └─────┴─────┴─────┴─────┴─────┘
```

**Step 4 — Apply ReLU:**

All values ≥ 0, so the map is unchanged. Any negative value would be replaced with 0.

**Step 5 — Max Pooling (2×2, stride = 2):**
```
  Pool output size = floor((5 − 2)/2) + 1 = 2     →     output = 2×2

  Block (rows 1–2, cols 1–2):  max( 1,  3,  6, 12) = 12
  Block (rows 1–2, cols 3–4):  max( 2,  1,  7,  7) =  7
  Block (rows 3–4, cols 1–2):  max( 9, 10,  2,  7) = 10
  Block (rows 3–4, cols 3–4):  max(10, 14,  7, 12) = 14
```

**Final output (2×2):**
```
  ┌─────┬─────┐
  │  12 │   7 │
  ├─────┼─────┤
  │  10 │  14 │
  └─────┴─────┘
```

**Pipeline summary:**
```
  4×4 ──[Pad P=1]──► 6×6 ──[Conv 2×2, S=1]──► 5×5 ──[ReLU]──► 5×5 ──[MaxPool 2×2, S=2]──► 2×2
```

---

## 11. Master Formula Reference

### Activation Functions

```text
Sigmoid (Logistic)
  σ(z) = 1 / (1 + e^(−z))

Sigmoid Derivative
  dσ/dz = σ(z) · (1 − σ(z))
        = ŷ · (1 − ŷ)

ReLU
  ReLU(x) = max(0, x)

ReLU Derivative
  d/dx = 1 if x > 0 else 0
```

---

### Method A — Perceptron Learning Rule (Single Layer)

```text
Net Input
  y_in = Σ (w_i · x_i) + b

Activation (Step Function)
  y_out = 1   if y_in > 0
          0   otherwise

Error
  E = y − y_out
  (values typically −1, 0, +1)

Weight Update
  w_i(new) = w_i(old) + η · x_i · E

Bias Update
  b(new) = b(old) + η · E
```

Notes:

* Uses discrete output.
* No differentiability required.
* Works only for linearly separable problems.

---

### Method B — Gradient Descent / Backpropagation (MLP)

```text
Forward Pass
  z = W x + b
  a = σ(z)

Output Layer Error (Sigmoid + MSE)
  δ_o = (ŷ − y) · ŷ · (1 − ŷ)

Hidden Layer Error
  δ_h = (Σ δ_next · w_connecting) · a_h · (1 − a_h)

Weight Update
  w(new) = w(old) − η · δ · (input_to_weight)

Bias Update
  b(new) = b(old) − η · δ
```

Notes:

* Requires differentiable activation.
* Supports multi-layer networks.
* Uses gradient descent optimization.

---

### CNN Output Size (Spatial Dimensions)

```text
Convolution Layer
  Output = floor( (N − F + 2P) / S ) + 1

Pooling Layer
  Output = floor( (N − F) / S ) + 1
```

Where:

```text
N = Input size
F = Filter (kernel) size
P = Padding
S = Stride
```

For rectangular inputs:

```text
H_out = floor((H − F + 2P) / S) + 1
W_out = floor((W − F + 2P) / S) + 1
```

---

### CNN Parameter Count

```text
Convolution Layer
  Parameters = (F × F × C_in + 1) × C_out

  where:
    F     = filter size
    C_in  = input channels
    C_out = number of filters
    +1    = bias per filter

Pooling Layer
  Parameters = 0

Dense (Fully Connected) Layer
  Parameters = (Inputs × Neurons) + Neurons
```

---

### Learning Rate Update Intuition

```text
Perceptron   → PLUS direction
  w = w + η · error · input

Backprop     → MINUS gradient direction
  w = w − η · gradient
```

---

### Common Loss Functions (Useful Addition)

```text
Mean Squared Error (MSE)
  L = ½ (y − ŷ)²

Binary Cross Entropy (BCE)
  L = −[ y log(ŷ) + (1 − y) log(1 − ŷ) ]
```
