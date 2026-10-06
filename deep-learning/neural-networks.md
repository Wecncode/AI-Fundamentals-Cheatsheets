# Neural Networks & Deep Learning Foundations

## 1. Network Architecture

*   **Perceptron:** The fundamental unit. Computes a weighted sum of inputs and passes it through an activation function.
    $$z = \sum_{i=1}^{n} w_i x_i + b$$
    $$a = f(z)$$
*   **Feedforward Neural Network (FNN):** Multiple layers of perceptrons (Dense layers). Data flows strictly forward.
*   **Backpropagation:** The algorithm used to calculate the gradient of the loss function with respect to the weights, utilizing the chain rule from calculus.

## 2. Common Activation Functions

| Function | Formula | Range | Use Case |
|---|---|---|---|
| **Sigmoid** | $\sigma(z) = \frac{1}{1 + e^{-z}}$ | $(0, 1)$ | Binary classification output layers. |
| **Tanh** | $\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}$ | $(-1, 1)$ | Hidden layers (zero-centered). |
| **ReLU** | $f(z) = \max(0, z)$ | $[0, \infty)$ | Default for hidden layers; mitigates vanishing gradient. |
| **Softmax** | $f(z_i) = \frac{e^{z_i}}{\sum_{j} e^{z_j}}$ | $(0, 1)$ | Multi-class classification output layers (outputs sum to 1). |

## 3. Optimizers

*   **Stochastic Gradient Descent (SGD):** Updates weights using a single training example or small batch.
    $$w = w - \alpha \frac{\partial L}{\partial w}$$ *(where alpha is the learning rate)*
*   **Adam (Adaptive Moment Estimation):** Combines the advantages of AdaGrad and RMSProp. Adapts learning rates for each parameter based on first and second moments of the gradients. Industry standard for most DL tasks.

## 4. Mitigating Overfitting

*   **Dropout:** Randomly sets a fraction of input units to 0 at each update during training.
*   **Early Stopping:** Halting training when validation loss stops improving.
*   **L1/L2 Regularization:** Adding a penalty term to the loss function based on weight magnitudes.

*©️ Created by Wecncode Developer Community!*
