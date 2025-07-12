# Neural Autoregressive Model with Gaussian Mixture

Hi! In this notebook, I implemented a **neural autoregressive model** (the foundational technology behind models like ChatGPT!) using **Gaussian mixture distributions** for each conditional probability. Below is a concise overview of the key concepts. A detailed video tutorial will be released soon!

## Key Concepts

### 1. Autoregressive Model  
An autoregressive model is a generative model that factorizes the joint probability distribution of a sequence into a product of conditional probabilities:  

$$
p(x_1, x_2, \dots, x_n) = p(x_1) \cdot p(x_2|x_1) \cdot p(x_3|x_2,x_1) \cdots p(x_n|x_{n-1}, \dots, x_1)
$$

The goal is to learn each conditional distribution, enabling **sequential generation** of new data by sampling from these distributions.

### 2. Loss Function  
The model is trained using the **negative log-likelihood (NLL)** loss, which measures how well the predicted distributions match the true data distribution. Each conditional probability is approximated using a neural network.

### 3. Gaussian Mixture for Improved Accuracy  
To enhance modeling flexibility, each conditional distribution is represented as a **mixture of Gaussians** (in this implementation, 3 components). This allows the model to capture **multi-modal** dependencies in the data.  

### 4. Sampling Process  
Sampling is performed **autoregressively**:  
1. Start with an initial value (or noise).  
2. For each subsequent step, sample from the learned conditional distribution.  
   - First, select a Gaussian component **uniformly** from the mixture.  
   - Then, sample from the chosen component to generate the next value.  
3. Repeat until the full sequence is generated.  

## Important Notes  

- This implementation is a **direct application of autoregressive theory**, where separate classifiers are trained for each input dimension (e.g., per pixel in an image). While this approach is **not scalable** for high-dimensional data, it serves as an intuitive introduction to the core concepts.  
- Modern variants (e.g., **masked autoregressive models**) use a single neural network with masking techniques to approximate the joint distribution efficiently. This is how models like **ChatGPT** scale to massive datasets!  
- Think of this as the **starting point**—a clear, theoretical foundation before diving into large-scale implementations.  

---

### Get Involved!
🌟 If you find this project helpful, **please give it a star** on GitHub! This helps others discover it and supports open science.  

❓ Have questions or suggestions? Feel free to:  
- Open an issue on GitHub.  
- Email me at [Aref.shahbakhsh1998@gmail.com](mailto:Aref.shahbakhsh1998@gmail.com).  

Let’s make learning accessible to everyone! 🚀  
