Hybrid Data Compression Using Arithmetic Coding and Recurrent Neural Networks
Overview

This project implements a hybrid lossless data compression system that combines Recurrent Neural Networks (RNN) with Arithmetic Coding to achieve higher compression efficiency compared to traditional entropy-based techniques such as Shannon–Fano coding.
The proposed system uses an LSTM-based RNN to generate adaptive, context-aware probability distributions for each byte in the input file. These probabilities are then encoded using arithmetic coding, enabling sub-bit level compression.
The project demonstrates a significant improvement in compression ratio while maintaining accurate lossless reconstruction verified through SHA-256 hashing.

Features

Fully lossless compression and decompression.

RNN-based next-byte probability prediction.

Adaptive probability modeling using LSTM.

Custom arithmetic encoder and decoder implemented in Python.

Comparison with Shannon–Fano compression.

Interactive Google Colab interface with file upload and download support.

End-to-end compression statistics including compressed size, ratio, and SHA-256 verification.

Project Structure

├── ADCT_REPORT.pdf                     # Full project report
├── Abstract.pdf                        # Project abstract
├── Existing_system Shannon Fano.ipynb  # Shannon–Fano implementation
├── Proposed system(Hybrid Compression).ipynb  # RNN + Arithmetic Coding implementation
├── Final review ppt.pptx               # Final presentation slides
├── Review -1 PPT ADCT.pptx             # Review-1 PPT
└── README.md                           # (This file)

Methodology
1. Preprocessing

Input file is uploaded and converted to a sequence of bytes (0–255).

2. RNN Probability Modeling

An LSTM model is trained to predict the next-byte probabilities based on previous bytes.

Logits from the model are converted to probability distributions using softmax.

3. Arithmetic Encoding

The predicted probabilities are used to update the arithmetic coding interval.

A compressed binary file (compressed.bin) is generated.

A readable .txt version is also produced for analysis.

4. Arithmetic Decoding

Uses the same RNN model and saved probability sequence.

Reconstructs the original bytes exactly.

5. Verification

Compressed vs. Restored SHA-256 hashes are compared.

Perfect match confirms fully lossless compression.

Comparison with Existing System
Shannon–Fano (Existing Method)

Original Size: 6254 bytes

Compressed Size: 3563 bytes

Compression Ratio: 0.570×

Reduction: 43%

Lossless: Yes (SHA-256 match)

Proposed RNN + Arithmetic Coding

Original Size: 6254 bytes

Compressed Size: 900 bytes

Compression Ratio: 0.144×

Reduction: 85.6%

Lossless: Yes (SHA-256 match)

The proposed system achieves approximately four times better compression efficiency than Shannon–Fano.

How to Run the Project

Google Colab (Recommended)

Open the .ipynb file in Google Colab.

Upload any file using the file upload prompt.

Run all cells to:

Train the RNN

Generate probabilities

Perform arithmetic coding

Compress and decompress the file

Download compressed and restored files from the generated UI buttons.

Technologies Used

Python

PyTorch (LSTM Model)

NumPy

Google Colab

Arithmetic Coding Algorithm

Results

Successfully demonstrated that adaptive neural probability modeling dramatically improves compression.

Proposed system reduced file size by 85.6% while maintaining perfect losslessness.

Outperformed Shannon–Fano in efficiency and adaptability.

Future Enhancements

Replace RNN with Transformer or GRU for improved pattern learning.

Train on larger datasets for more accurate probabilities.

Extend to multimedia compression (audio, image, video).

Build a GUI-based desktop compression tool.

Explore model compression for deployment on low-resource devices.

References

Shannon–Fano Coding Theory

Arithmetic Coding Fundamentals

Neural Network-Based Compression Research

PyTorch Documentation
