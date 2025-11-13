# 🚀 Hybrid Data Compression Using Arithmetic Coding & Recurrent Neural Networks (RNN)

> **A hybrid lossless compression framework that integrates LSTM-based neural probability modeling with Arithmetic Coding to achieve significantly higher compression efficiency compared to the traditional Shannon–Fano algorithm.**

This repository contains all implementation files, notebooks, reports, and presentations for the ADCT (Advanced Data Compression Techniques) course project.

---

## ⭐ Project Highlights

### 🔥 Why a Hybrid Model?

Traditional compression methods like **Shannon–Fano** use static probabilities, assigning codes based only on global symbol frequency. This is inefficient for data where patterns are contextual.

This project overcomes these limitations by using an **RNN (LSTM)** to predict adaptive, context-based probabilities for each symbol. These highly accurate, dynamic probabilities are then fed into an **Arithmetic Coder**, which can achieve near-optimal, fractional-bit compression.

### 📉 Results at a Glance

The hybrid approach achieves approximately **4 times better compression** than the baseline Shannon–Fano algorithm on the test data.

| Method | Original Size | Compressed Size | Compression Ratio | Size Reduction |
| :--- | :--- | :--- | :--- | :--- |
| **Shannon–Fano** | 6254 bytes | 3563 bytes | 0.570× | 43.0% |
| **RNN + Arithmetic (Proposed)** | 6254 bytes | **900 bytes** | **0.144×** | **85.6%** |

---

## 🧠 System Overview

1.  **Input & Preprocessing**: The input file is read as raw bytes and converted into a tensor for the neural network.

2.  **RNN Probability Modeling**: An LSTM network processes the byte sequence, learns byte-level dependencies, and predicts the probability distribution for the *next* byte.

3.  **Softmax Conversion**: The raw output (logits) from the RNN is converted into a valid probability distribution using the Softmax function:
    $$P(x) = \frac{e^{z(x)}}{\sum_{k} e^{z(k)}}$$

4.  **Arithmetic Encoding**: The Arithmetic Encoder uses the adaptive probabilities from the RNN to progressively shrink a numerical interval for the entire file, resulting in a single, highly compact compressed output.

5.  **Arithmetic Decoding**: The decoder uses an identical, synchronized RNN model to recompute the *exact same* probability predictions during decompression, allowing it to perfectly reconstruct the original file from the compressed data.

6.  **Verification**: **SHA-256** hashes of the original and restored files are compared to confirm the compression is 100% lossless.

---

## 📂 Repository Contents

```bash
.
├── ADCT_REPORT.pdf
│      (Complete project documentation with methodology,
│       architecture, implementation and experimental results)
│
├── Abstract.pdf
│      (One-page summary of the project)
│
├── Existing_system Shannon Fano.ipynb
│      (Implementation of Shannon–Fano for comparison)
│
├── Proposed system(Hybrid Compression).ipynb
│      (Full hybrid system: RNN + Arithmetic Coding + UI)
│
├── Final review ppt.pptx
│      (Final presentation slides)
│
├── Review -1 PPT ADCT.pptx
│      (Review-1 presentation slides)
│
└── README.md
       (This file)

⚙️ Features
✔️ Complete Lossless Compression: Guarantees perfect reconstruction of the original file.

✔️ Neural Probability Model: Uses an LSTM-based RNN for adaptive, context-aware probability prediction.

✔️ Custom Coder: Includes full implementations of the Arithmetic Encoder and Decoder from scratch.

✔️ Interactive UI: Features a Google Colab file upload and download interface.

✔️ Comparative Analysis: Directly compares results against a baseline Shannon–Fano implementation.

✔️ Verification: Integrated SHA-256 hashing to verify lossless reconstruction.

🛠️ Setup & Running
▶️ Run in Google Colab (Recommended)
Open Proposed system(Hybrid Compression).ipynb in Google Colab.

Upload any file (e.g., .txt, .py) when prompted by the file upload cell.

Run all cells in order.

The output will display compression statistics and provide UI buttons to download the compressed file and the restored (decompressed) file.

▶️ Run Locally
1. Ensure you have Python and Jupyter Notebook installed.

2. Install the required dependencies:

pip install torch numpy

3. Launch Jupyter Notebook:

Launch Jupyter Notebook:

4. Open and run the Proposed system(Hybrid Compression).ipynb notebook.

📊 Results & Comparison
Example Output (from Colab)
Original Size: 6254 bytes
Compressed Size: 900 bytes
Compression Ratio: 0.144×

SHA-256 (original): c3a2...b91f
SHA-256 (restored): c3a2...b91f

Reconstruction: Verified lossless

📈 Advantages
Learns Structure: The RNN model can learn long-term dependencies and complex structures in the data, unlike static models.

Accurate Probabilities: Produces highly accurate, context-specific probabilities, which is the key to high compression.

Near-Optimal: Arithmetic coding achieves compression ratios very close to the theoretical limit (entropy) defined by the probability model.

Universal: Works well on various file types, especially those with repetitive or complex patterns (like text, code, or structured data).

🚧 Future Enhancements
Model Architecture: Replace the RNN/LSTM with more modern architectures like GRU or a Transformer-based model for potentially better probability modeling.

Speed & Optimization: Improve training speed and implement batched inference for faster encoding/decoding.

Standalone Tool: Build a standalone desktop application (e.g., using PyQT or Tkinter) for easier use.

Data Types: Extend the framework to specialize in other data types, such as images, audio, or video.

Model Quantization: Apply model compression (e.g., quantization) for deployment on low-resource or mobile devices.

📚 References
Shannon–Fano Coding Theory

Arithmetic Coding Theory

Recurrent Neural Networks (RNNs) & LSTMs

PyTorch Documentation
