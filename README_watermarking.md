# Watermarking Project — M1 EUR Security - Limoges' University

This project aims to implement a robust **watermarking algorithm** for **1D audio signals** and **2D color images**, using **spread spectrum techniques**. The main goal is to study the tradeoff between **robustness** and **transparency** in the watermarking process.

##  Objectives

- Embed a secret signature (e.g., user ID) into a cover signal using a private key.
- Detect the watermark using a decoding process.
- Analyze robustness against attacks (low-pass/high-pass filters, image compression, etc.)
- Extend the watermarking to images using the YCrCb color space.

---

##  Methodology

### 1. Watermarking by Spread Spectrum (1D)

- Convert a character to a signature of 8 bits in {−1, +1}.
- Upsample the signature by a factor `cr`.
- Generate a pseudo-random Gaussian modulation sequence `p` using a private key.
- Modulate the signature using `w[k] = α · b[k] · p[k]`.
- Embed the watermark in the signal: `s_m[n] = s[n] + w[n]`.

### 2. Decoding Process

- Demodulate the watermarked signal with `p[k]` and reconstruct the signature using:
  
  ```
  sd[n] = (1/cr) ∑ p[k] · sm[k]
  sign(sd[n]) ≈ a[n]
  ```

### 3. Robustness Evaluation

- Analyze performance against:
  - Low-pass filtering (e.g., fc = 0.3, 0.1)
  - High-pass filtering (e.g., fc = 0.2, 0.4)

### 4. Watermarking Color Images (2D)

- Convert image to **YCrCb** space.
- Choose a component (Y, Cr, or Cb) to apply the watermark.
- Use a 4x4 signature matrix (from two characters).
- Apply 2D spread spectrum watermarking with upsampling and modulation.

---

##  Technologies Used

- Python 3
- NumPy
- Matplotlib
- SciPy
- OpenCV (for image processing)
- FFT (for spectral analysis)
- WAV files for audio processing

---




## 👩‍💻 Author

Project realized as part of the **Security M1 EUR** program  by Imane ELACERI


