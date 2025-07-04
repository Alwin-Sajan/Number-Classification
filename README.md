# Number Classification using TensorFlow

This project is designed to classify handwritten digits (0-9) using a neural network built with TensorFlow and Keras. The model is trained using a dataset of images, where each image represents a digit. The goal is to predict the correct digit from the image.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Model Explanation](#model-explanation)
- [Training the Model](#training-the-model)
- [Contributing](#contributing)

## Requirements

To run this project, you need the following libraries:

- TensorFlow
- Keras
- NumPy
- Matplotlib

You can install these dependencies using pip:

```bash
pip install tensorflow numpy matplotlib
```

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Alwin-Sajan/Number-Classification.git
   cd Number-Classification
   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Prepare your dataset (such as MNIST). You can load the MNIST dataset directly from Keras using the following code:

   ```python
   from tensorflow.keras.datasets import mnist

   (X_train, y_train), (X_test, y_test) = mnist.load_data()
   ```

2. Flatten the images (28x28 to 784):

   ```python
   X_train_flattened = X_train.reshape(len(X_train), 28 * 28)
   X_test_flattened = X_test.reshape(len(X_test), 28 * 28)
   ```

3. Normalize the data (pixel values from 0 to 255 are scaled to 0 to 1):

   ```python
   X_train_flattened = X_train_flattened / 255.0
   X_test_flattened = X_test_flattened / 255.0
   ```

4. Now, you can run the training process:

   ```python
   model.fit(X_train_flattened, y_train, epochs=5)
   ```

5. Evaluate the model:

   ```python
   model.evaluate(X_test_flattened, y_test)
   ```

## Model Explanation

The model is a simple **fully connected neural network** (a dense layer) that classifies images into one of 10 categories (digits 0-9). The network architecture consists of:

- **Input Layer:** The input shape is `(784,)` because each image is flattened from its original 28x28 dimensions.
- **Hidden Layer:** A single dense layer with 10 units and the `sigmoid` activation function.
- **Output Layer:** The model outputs probabilities for each of the 10 classes using the `softmax` function (implicitly from `sparse_categorical_crossentropy`).

## Training the Model

We train the model using the following parameters:

- **Optimizer:** `Adam` (a popular optimizer for neural networks).
- **Loss Function:** `sparse_categorical_crossentropy` (appropriate for multi-class classification).
- **Metrics:** Accuracy.

```python
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

model.fit(X_train_flattened, y_train, epochs=5)
```

You can experiment with more complex architectures, such as adding more layers or changing activation functions to improve performance.

## Contributing

Feel free to fork the repository, submit pull requests, or report issues. Contributions are always welcome!
