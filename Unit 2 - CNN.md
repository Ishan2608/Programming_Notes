# Deep Learning — Unit 2: Convolutional Neural Networks

## Table of Contents

- Chapter 11 — Motivation for CNNs
- Chapter 12 — The Convolution Operation
- Chapter 13 — Pooling
- Chapter 14 — The Standard CNN Pipeline
- Chapter 15 — Parameter Counting
- Chapter 16 — Famous CNN Architectures
- Chapter 17 — Predefined Image Filters
- Numerical 3 — Parameter Counting
- Numerical 4 — Full CNN Pipeline
- Appendix — Master Formula Reference


## Chapter 11 — Motivation for CNNs

Applying a fully connected network to image data creates two fundamental problems.

**Problem 1 — Parameter explosion:** A 224×224×3 image has 150,528 input values. A single fully connected layer of just 1,000 neurons requires approximately 150 million parameters — and that is only the first layer.

**Problem 2 — No spatial awareness:** Flattening an image into a 1D vector discards all positional relationships. The network treats pixel (0,0) and pixel (100,100) as having no inherent spatial relationship to each other.

CNNs solve both by using **convolution** — a small filter slides across the image applying the same learned weights at every position. This is called **weight sharing**, and it preserves spatial structure while drastically reducing parameter count.

```
  MLP on 224×224×3 image, 1000 neurons  →  ~150,000,000 parameters (first layer alone)
  CNN with 32 filters of 3×3            →   32 × (3×3×3 + 1) = 896 parameters
```


## Chapter 12 — The Convolution Operation

A filter (kernel) of fixed size is positioned at each location in the input. The element-wise products between the filter and the underlying image patch are summed to yield one output value. The filter then slides to the next position.

```
  Image patch:            Filter:               Result:

  ┌───────┬───────┐       ┌───────┬───────┐
  │   1   │   2   │       │   1   │   0   │     (1×1) + (2×0)
  ├───────┼───────┤   ×   ├───────┼───────┤   = (0×0) + (1×1)   =  2
  │   0   │   1   │       │   0   │   1   │
  └───────┴───────┘       └───────┴───────┘
```

**Formula:**

```
  Output[i, j] = Σ_m Σ_n ( Input[i+m, j+n] × Filter[m, n] ) + bias
```

### 12.1 Output Size Formulas

```
  Convolution:    Output_size = floor( (N − F + 2P) / S ) + 1
  Pooling:        Output_size = floor( (N − F) / S ) + 1

      N = input dimension     F = filter size     P = padding     S = stride
```

### 12.2 Terminology Reference

| Term | Definition |
|---|---|
| Filter / Kernel | Small matrix of learnable weights slid across the input |
| Stride | Number of positions the filter moves per step |
| Padding | Zeros added around the input border to control output size |
| Feature Map | The 2D output produced by applying one filter across the full input |
| Depth / Channels | Number of filters; equals the depth of the output feature map volume |
| Receptive Field | The region of the input that influences a given output position |


## Chapter 13 — Pooling

Pooling reduces the spatial dimensions of a feature map by replacing each region with a single summary value. This reduces computation, provides translational invariance, and helps control overfitting.

```
  Input feature map (4×4)              Max Pool 2×2, stride=2  →  Output (2×2)

  ┌───────┬───────┬───────┬───────┐    ┌──────────────────────┐   ┌───────┬───────┐
  │   1   │   3   │   2   │   4   │    │ max(1,3,5,6) = 6     │   │   6   │   4   │
  ├───────┼───────┼───────┼───────┤    │ max(2,4,1,3) = 4     │   ├───────┼───────┤
  │   5   │   6   │   1   │   3   │    │ max(2,8,4,7) = 8     │   │   8   │   9   │
  ├───────┼───────┼───────┼───────┤    │ max(3,5,6,9) = 9     │   └───────┴───────┘
  │   2   │   8   │   3   │   5   │    └──────────────────────┘
  ├───────┼───────┼───────┼───────┤
  │   4   │   7   │   6   │   9   │
  └───────┴───────┴───────┴───────┘
```

| Type | Operation | Learnable Parameters |
|---|---|---|
| Max Pooling | Maximum value in each region | 0 |
| Average Pooling | Average of each region | 0 |
| Global Max Pooling | Single maximum across entire feature map → 1×1 output | 0 |
| Global Average Pooling | Single average across entire feature map → 1×1 output | 0 |

Pooling layers have no learnable parameters.


## Chapter 14 — The Standard CNN Pipeline

```
  ┌───────────────────────┐
  │      Input Image      │
  └──────────┬────────────┘
             │
             ▼
  ┌───────────────────────┐
  │      Conv Layer       │  ←  filter slides over image, produces feature maps
  └──────────┬────────────┘
             │
             ▼
  ┌───────────────────────┐
  │         ReLU          │  ←  f(x) = max(0, x)  — zeros all negative activations
  └──────────┬────────────┘
             │
             ▼
  ┌───────────────────────┐
  │      Pool Layer       │  ←  shrinks spatial dimensions, retains strong signals
  └──────────┬────────────┘
             │
        (repeat this
         block as needed)
             │
             ▼
  ┌───────────────────────┐
  │        Flatten        │  ←  [H × W × C]  ──►  [H·W·C]  one-dimensional vector
  └──────────┬────────────┘
             │
             ▼
  ┌───────────────────────┐
  │      FC (Dense)       │  ←  standard MLP — combines all extracted features
  └──────────┬────────────┘
             │
             ▼
  ┌───────────────────────┐
  │        Output         │  ←  Softmax (multi-class)  or  Sigmoid (binary)
  └───────────────────────┘
```


## Chapter 15 — Parameter Counting

### Convolutional Layer

```
  Parameters = ( F_h × F_w × C_in + 1 ) × C_out

      F_h, F_w  =  filter height and width
      C_in      =  number of input channels (input depth)
      C_out     =  number of filters (output depth)
      +1        =  one bias term per filter
```

### Pooling Layer

```
  Parameters = 0       ←  pooling has no learnable parameters
```

### Fully Connected (Dense) Layer

```
  Parameters = ( Inputs × Neurons ) + Neurons
```


## Chapter 16 — Famous CNN Architectures

### LeNet-5 (1998)

The first successful CNN, designed for handwritten digit recognition on the MNIST dataset. It demonstrated that convolutional feature learning outperforms hand-engineered features.

```
  Input        Conv1         Pool1        Conv2        Pool2       FC Layers         Out
  32×32×1     28×28×6      14×14×6     10×10×16      5×5×16
     │             │              │            │             │             │            │
     └──[5×5,6f] ──► └──[Avg 2×2] ──► └──[5×5,16f] ──► └──[Avg 2×2] ──► └──[Flatten]──►[FC:120]──►[FC:84]──►[10]
```

| Property | Detail |
|---|---|
| Parameters | ~60,000 |
| Activation | Tanh / Sigmoid |
| Significance | First CNN deployed in production — used for bank cheque reading |

### AlexNet (2012)

Won ImageNet 2012 by a large margin, triggering the modern deep learning era. Its key contribution was proving that deep CNNs trained on GPUs dramatically outperform hand-engineered systems.

```
  In            Conv1           Pool1        Conv2         Pool2
  224×224×3    55×55×96       27×27×96    27×27×256     13×13×256
     │               │               │           │              │
     └──[11×11,96f,  ──►└──[Max 3×3,  ──►└──[5×5,  ──►└──[Max 3×3,  ──►
            s=4]            s=2]           256f]         s=2]

      Conv3          Conv4          Conv5         Pool3          FC Layers             Out
     13×13×384     13×13×384     13×13×256      6×6×256
         │               │               │             │                │               │
    ─────►└──[3×3,384f] ──►└──[3×3,256f] ──►└──[Max 3×3, ──►└──[FC:4096] ──►[FC:4096]──►[1000]
                                                  s=2]                                  Softmax
```

| Property | Detail |
|---|---|
| Parameters | ~60 million |
| Activation | **ReLU** — first large-scale use; eliminated vanishing gradients in shallow layers |
| Key innovations | ReLU, Dropout regularisation, GPU training, Data augmentation |

### VGGNet (2014)

Demonstrated through systematic experimentation that depth using only small 3×3 filters consistently outperforms shallower networks with larger filters.

```
  In          Block 1        Block 2         Block 3           Block 4           Block 5
  224×224×3  224×224×64    112×112×128      56×56×256         28×28×512         14×14×512
     │             │               │                │                 │                 │
     └──[C3,C3] ──►└──[P]──[C3,C3]──►└──[P]──[C3,C3,C3]──►└──[P]──[C3,C3,C3]──►└──[P]──[C3,C3,C3]──►[P]
                   MaxPool           MaxPool                   MaxPool                MaxPool          MaxPool

  C3 = Conv 3×3       After Block 5: 7×7×512
                              │
                              └──►[FC:4096]──►[FC:4096]──►[FC:1000]──►Softmax
```

| Property | Detail |
|---|---|
| Versions | VGG-16 (13 conv + 3 FC), VGG-19 (16 conv + 3 FC) |
| Parameters | ~138 million |
| Key insight | Two stacked 3×3 layers = same receptive field as one 5×5, with fewer parameters and more non-linearity |

### GoogLeNet / Inception (2014)

Rather than selecting one filter size, the Inception module applies multiple filter sizes in parallel and concatenates their outputs. The network learns which responses are most informative for a given task.

```
  Inception Module:

                      ┌──────────────────────────────────────────────────────────┐
                      │  1×1 Conv ─────────────────────────────────────────────► │
                      │                                                          │
  Input ─────────────►│  1×1 Conv ──► 3×3 Conv ──────────────────────────────►   │ ──► Concat ──► Output
                      │                                                          │
                      │  1×1 Conv ──► 5×5 Conv ──────────────────────────────►   │
                      │                                                          │
                      │  MaxPool 3×3 ──► 1×1 Conv ────────────────────────────►  │
                      └──────────────────────────────────────────────────────────┘

  Note: 1×1 Conv before 3×3/5×5 reduces depth first — dramatically reduces cost
```

```
  Full GoogLeNet (simplified):

  In ──►[Stem] ──►[Inc×2] ──►[Pool] ──►[Inc×5] ──►[Pool] ──►[Inc×2] ──►[AvgPool] ──►[Dropout] ──►[FC:1000]
         Conv+Pool   blocks    3×3      blocks     3×3      blocks
```

| Property | Detail |
|---|---|
| Layers | 22 weight layers |
| Parameters | ~5 million — far fewer than VGG despite greater depth |
| Key innovation | Inception module; 1×1 convolutions for channel-wise dimension reduction |

### ResNet (2015)

Very deep networks suffer from **vanishing gradients** — error signals shrink as they travel backwards through many layers, eventually stalling weight updates. ResNet introduces **skip connections** that allow gradients to bypass layers entirely.

```
  Residual Block:

  Input x
     │
     ├────────────────────────────────────────────┐
     │                                            │  ←  skip / identity connection
     ▼                                            │
  ┌──────────────────────┐                        │
  │      Conv 3×3        │                        │
  │      BatchNorm       │                        │
  │      ReLU            │                        │
  │      Conv 3×3        │                        │
  │      BatchNorm       │                        │
  └──────────┬───────────┘                        │
             │                                    │
             ▼                                    │
           F(x)   +  ◄────────────────────────── x
             │
           ReLU
             │
             ▼
           H(x) = F(x) + x
```

The block learns only the **residual** `F(x) = H(x) − x`. If no transformation is needed, the block drives F(x) → 0 and the input passes through unchanged — this is what makes very deep networks stable to train.

```
  ResNet-50 (simplified):

  In          Conv1       Pool      Layer 1      Layer 2       Layer 3       Layer 4       Out
  224×224×3  112×112×64  56×56×64  56×56×256   28×28×512   14×14×1024     7×7×2048
     │             │           │        │             │             │             │           │
     └──[7×7,64] ──►└──[MaxPool]──►└──[×3] ──►└──[×4] ───────►└──[×6] ───────►└──[×3] ───────►└──[AvgPool]──►[FC:1000]
                                   residual      residual       residual       residual
                                   blocks        blocks         blocks         blocks
```

| Property | Detail |
|---|---|
| Versions | ResNet-50, ResNet-101, ResNet-152 |
| Parameters (ResNet-50) | ~25 million |
| Key innovation | Skip connections — solved vanishing gradient at extreme depth |
| Achievement | First model to surpass human-level accuracy on ImageNet |

### Architecture Comparison Summary

```
  Architecture    Year    Layers    Parameters    Primary Innovation
  ───────────────────────────────────────────────────────────────────
  LeNet-5         1998       7         ~60K        First working CNN
  AlexNet         2012       8         ~60M        ReLU, Dropout, GPU training
  VGGNet          2014    16–19       ~138M        Depth with uniform 3×3 filters
  GoogLeNet       2014      22          ~5M        Inception module, 1×1 conv
  ResNet          2015    50–152       ~25M        Skip connections, extreme depth
```


## Chapter 17 — Predefined Image Filters

Convolutional filters can be designed manually to perform known image processing operations, or learned automatically from data. The following are standard predefined filters used in image processing and in the early layers of CNNs.

## Edge Detection

**Sobel X — Detects vertical edges**

$$
\begin{bmatrix}
-1 & 0 & +1 \\
-2 & 0 & +2 \\
-1 & 0 & +1
\end{bmatrix}
$$

How it works:
- Computes horizontal intensity gradient (difference between left and right pixels).
- Positive values respond to bright-to-dark transitions in the x-direction.
- Middle row has higher weight (±2) to emphasize central pixels and reduce noise sensitivity.
- Output magnitude corresponds to edge strength.

**Sobel Y — Detects horizontal edges**

$$
\begin{bmatrix}
-1 & -2 & -1 \\
0 & 0 & 0 \\
+1 & +2 & +1
\end{bmatrix}
$$

How it works:
- Computes vertical intensity gradient (difference between top and bottom pixels).
- Detects transitions along the y-direction.
- Central column weighting improves robustness to noise.
- Often combined with Sobel X to compute gradient magnitude: G = sqrt(Gx^2 + Gy^2)

**Laplacian — Detects edges in all directions**

$$
\begin{bmatrix}
0 & 1 & 0 \\
1 & -4 & 1 \\
0 & 1 & 0
\end{bmatrix}
$$

How it works:
- Approximates the second spatial derivative (rate of change of gradient).
- Highlights regions where intensity changes rapidly in any direction.
- Center negative value subtracts surrounding average → emphasizes discontinuities.
- Sensitive to noise, so often preceded by Gaussian smoothing.


**Canny — Clean, thin edges**

Multi-stage algorithm:
- Gaussian blur reduces noise.
- Gradient computation identifies edge strength and direction.
- Non-maximum suppression thins edges.
- Double threshold + hysteresis removes weak false edges.


## Blur / Smoothing

**Box / Average — Replace each pixel with the mean of its neighbourhood**

$$
\frac{1}{9}
\begin{bmatrix}
1 & 1 & 1 \\
1 & 1 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$

How it works:
- Computes simple local average of surrounding pixels.
- Reduces high-frequency noise.
- Causes noticeable blurring because all neighbors have equal importance.
- Fast but produces less natural smoothing than Gaussian.


**Gaussian — Centre-weighted smoothing**

$$
\frac{1}{16}
\begin{bmatrix}
1 & 2 & 1 \\
2 & 4 & 2 \\
1 & 2 & 1
\end{bmatrix}
$$

How it works:
- Approximates a Gaussian distribution.
- Central pixel has highest influence → preserves structure better than box blur.
- Smooths noise while maintaining edges more naturally.
- Common preprocessing step before edge detection.


## Sharpening

**Sharpen — Enhances edges and increases local contrast**

$$
\begin{bmatrix}
0 & -1 & 0 \\
-1 & 5 & -1 \\
0 & -1 & 0
\end{bmatrix}
$$

How it works:
- Center value (>1) amplifies the original pixel intensity.
- Negative neighbors subtract surrounding blur.
- Equivalent to: original image + edge information.
- Increases perceived detail and contrast.

## Numerical 3 — Parameter Counting

**Problem:** Count the total number of trainable parameters in the following architecture.

**Architecture:**

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

**Layer 1 — Conv (32 filters, 3×3, input depth = 1):**

```
  Parameters   = (3 × 3 × 1 + 1) × 32 = 10 × 32 = 320
  Output size  = (28 − 3) / 1 + 1 = 26
  Output volume: 26 × 26 × 32
```

**Layer 2 — MaxPool (2×2, stride 2):**

```
  Parameters   = 0
  Output size  = (26 − 2) / 2 + 1 = 13
  Output volume: 13 × 13 × 32
```

**Layer 3 — Conv (64 filters, 3×3, input depth = 32):**

```
  Parameters   = (3 × 3 × 32 + 1) × 64 = 289 × 64 = 18,496
  Output size  = (13 − 3) / 1 + 1 = 11
  Output volume: 11 × 11 × 64
```

**Layer 4 — MaxPool (2×2, stride 2):**

```
  Parameters   = 0
  Output size  = floor((11 − 2) / 2) + 1 = 5
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

The flatten-to-dense transition (Layer 5 → Layer 6) accounts for over 90% of all parameters. This illustrates why convolutional layers are far more parameter-efficient than fully connected layers for image data.


## Numerical 4 — Full CNN Pipeline

**Problem:** Given the input image and filter below, compute the output after convolution with padding, ReLU activation, and max pooling.

```
  Input X (4×4):                      Filter W (2×2):

  ┌───────┬───────┬───────┬───────┐    ┌───────┬───────┐
  │   1   │   2   │   0   │   1   │    │   2   │   3   │
  ├───────┼───────┼───────┼───────┤    ├───────┼───────┤
  │   3   │   1   │   2   │   2   │    │   1   │   1   │
  ├───────┼───────┼───────┼───────┤    └───────┴───────┘
  │   0   │   1   │   1   │   3   │
  ├───────┼───────┼───────┼───────┤    Padding P = 1,  Stride S = 1
  │   2   │   2   │   0   │   1   │    Activation: ReLU
  └───────┴───────┴───────┴───────┘    Max Pool: 2×2, Pool Stride = 2
```

**Step 1 — Convolution output size:**

```
  Output_size = (4 − 2 + 2×1) / 1 + 1 = 5 → feature map = 5×5
```

**Step 2 — Padded image (6×6):**

```
  ┌───────┬───────┬───────┬───────┬───────┬───────┐
  │   0   │   0   │   0   │   0   │   0   │   0   │
  ├───────┼───────┼───────┼───────┼───────┼───────┤
  │   0   │   1   │   2   │   0   │   1   │   0   │
  ├───────┼───────┼───────┼───────┼───────┼───────┤
  │   0   │   3   │   1   │   2   │   2   │   0   │
  ├───────┼───────┼───────┼───────┼───────┼───────┤
  │   0   │   0   │   1   │   1   │   3   │   0   │
  ├───────┼───────┼───────┼───────┼───────┼───────┤
  │   0   │   2   │   2   │   0   │   1   │   0   │
  ├───────┼───────┼───────┼───────┼───────┼───────┤
  │   0   │   0   │   0   │   0   │   0   │   0   │
  └───────┴───────┴───────┴───────┴───────┴───────┘
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

**Full feature map (5×5):**

```
  ┌───────┬───────┬───────┬───────┬───────┐
  │   1   │   3   │   2   │   1   │   1   │
  ├───────┼───────┼───────┼───────┼───────┤
  │   6   │  12   │   7   │   7   │   4   │
  ├───────┼───────┼───────┼───────┼───────┤
  │   9   │  10   │  10   │  14   │   7   │
  ├───────┼───────┼───────┼───────┼───────┤
  │   2   │   7   │   7   │  12   │   7   │
  ├───────┼───────┼───────┼───────┼───────┤
  │   6   │  10   │   4   │   1   │   2   │
  └───────┴───────┴───────┴───────┴───────┘
```

**Step 4 — Apply ReLU:**

All values are ≥ 0, so the map is unchanged. Any negative value would be replaced with 0.

**Step 5 — Max Pooling (2×2, stride = 2):**

```
  Pool output size = floor((5 − 2) / 2) + 1 = 2     →     output = 2×2

  Block (rows 1–2, cols 1–2):  max( 1,  3,  6, 12) = 12
  Block (rows 1–2, cols 3–4):  max( 2,  1,  7,  7) =  7
  Block (rows 3–4, cols 1–2):  max( 9, 10,  2,  7) = 10
  Block (rows 3–4, cols 3–4):  max(10, 14,  7, 12) = 14
```

**Final output (2×2):**

```
  ┌───────┬───────┐
  │  12   │   7   │
  ├───────┼───────┤
  │  10   │  14   │
  └───────┴───────┘
```

**Full pipeline summary:**

```
  4×4 ──[Pad P=1]──► 6×6 ──[Conv 2×2, S=1]──► 5×5 ──[ReLU]──► 5×5 ──[MaxPool 2×2, S=2]──► 2×2
```


## Appendix — Master Formula Reference

```
  ════════════════════════════════════════════════════════════════════
    CNN — SIZING FORMULAS
  ════════════════════════════════════════════════════════════════════
    Convolution output  floor( (N − F + 2P) / S ) + 1
    Pooling output      floor( (N − F) / S ) + 1

        N = input size    F = filter size    P = padding    S = stride

  ════════════════════════════════════════════════════════════════════
    CNN — PARAMETER COUNTING
  ════════════════════════════════════════════════════════════════════
    Conv layer          ( F × F × C_in + 1 ) × C_out
    Pool layer          0
    Dense layer         ( Inputs × Neurons ) + Neurons

  ════════════════════════════════════════════════════════════════════
    PADDING
  ════════════════════════════════════════════════════════════════════
    Valid padding       P = 0               output < input
    Same padding        P = (F − 1) / 2     output = input

  ════════════════════════════════════════════════════════════════════
    ARCHITECTURE QUICK REFERENCE
  ════════════════════════════════════════════════════════════════════
    LeNet-5     1998   7 layers    ~60K     First working CNN
    AlexNet     2012   8 layers    ~60M     ReLU, Dropout, GPU
    VGGNet      2014   16–19       ~138M    Uniform 3×3 filters
    GoogLeNet   2014   22 layers   ~5M      Inception module
    ResNet      2015   50–152      ~25M     Skip connections
```
