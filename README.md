Hybrid Data Compression Using Arithmetic Coding and Recurrent Neural Networks
1. Introduction

This project presents a hybrid lossless compression system that combines an LSTM-based Recurrent Neural Network (RNN) with Arithmetic Coding.
Traditional algorithms like Shannon–Fano use static probability models and cannot capture patterns or context.
The proposed system uses adaptive neural probability prediction, significantly improving compression efficiency while maintaining lossless reconstruction.

2. Project Folder Structure
├── ADCT_REPORT.pdf
│      Full project report containing literature review,
│      methodology, experiments, implementation and results.
│
├── Abstract.pdf
│      One-page abstract summarizing the project objectives,
│      methodology, and findings.
│
├── Existing_system Shannon Fano.ipynb
│      Implementation of Shannon–Fano coding (existing method).
│      Includes encoding, decoding, and size comparison.
│
├── Proposed system(Hybrid Compression).ipynb
│      Full implementation of the proposed RNN + Arithmetic
│      Coding hybrid model. Includes:
│          - File upload
│          - RNN training & prediction
│          - Arithmetic encoding/decoding
│          - SHA-256 verification
│          - Compression statistics and UI buttons
│
├── Final review ppt.pptx
│      Final presentation PPT used for project viva.
│
├── Review -1 PPT ADCT.pptx
│      Initial Review-1 presentation.
│
└── README.md
       This file.

3. Features

Lossless compression and decompression

RNN-based adaptive probability prediction

Custom arithmetic encoder and decoder

File upload & download UI in Colab

Automatic SHA-256 hash verification

Comparison with Shannon–Fano

4. Methodology
4.1 Preprocessing

Input file is converted into a sequence of bytes (0–255).

4.2 RNN Probability Modeling

An LSTM processes previous bytes and predicts probability distribution for the next byte.
Logits are converted to probabilities using softmax.

4.3 Arithmetic Encoding

The predicted probabilities shrink the number line interval for each byte, producing highly compact fractional-bit output.

4.4 Arithmetic Decoding

Uses the same RNN predictions to reverse the interval updates and perfectly reconstruct the original file.

4.5 Verification

SHA-256 hash of original and restored file are compared to ensure lossless reconstruction.

5. Results
Shannon–Fano (Existing System)

Original size: 6254 bytes

Compressed size: 3563 bytes

Compression ratio: 0.570×

Reduction: 43%

Lossless reconstruction: Yes

RNN + Arithmetic Coding (Proposed System)

Original size: 6254 bytes

Compressed size: 900 bytes

Compression ratio: 0.144×

Reduction: 85.6%

Lossless reconstruction: Yes

Proposed system achieves around 4× better compression efficiency.

6. How to Run
Google Colab

Open the .ipynb file in Google Colab.

Upload any file using the UI.

7. Technologies Used

Python

PyTorch (LSTM Model)

NumPy

Google Colab

Custom Arithmetic Coding Implementation

8. Future Enhancements

Replace RNN with GRU/Transformer for deeper learning.

Build GUI-based desktop compression tool.

Improve compression speed through model optimization.

Apply hybrid compression to multimedia data (audio, image, video).

9. References

Shannon–Fano Coding Theory

Arithmetic Coding Algorithms

RNN/LSTM Documentation (PyTorch)

Neural Compression Research Papers

Run all cells to train/predict/compress/decompress.

Download compressed and restored files using built-in buttons
