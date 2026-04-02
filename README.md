# 🚀 8-Point FFT Processor in Verilog

## 📌 Overview
This project implements an **8-point Radix-2 Decimation-In-Time (DIT) Fast Fourier Transform (FFT)** in Verilog. The design demonstrates an efficient hardware realization of FFT using a structured multi-stage butterfly architecture, with scalability toward higher-point FFTs (e.g., 16/64-point).

---

## ⚙️ Features
- Radix-2 DIT FFT architecture  
- 3-stage butterfly computation (log₂8 = 3)  
- Complex input handling (real & imaginary)  
- Twiddle factor-based computation  
- Modular and synthesizable Verilog design  
- Scalable architecture for higher FFT sizes  

---

## 🧠 Architecture
The FFT is implemented using **three computation stages**, each consisting of butterfly units:

- **Stage 1:** 2-point butterflies  
- **Stage 2:** 4-point butterflies  
- **Stage 3:** 8-point butterflies  

The design uses **bit-reversed input ordering** for correct data alignment.

---

## 🔄 Butterfly Operation
Each butterfly unit performs:

```
X[k] = E[k] + Wn^k · O[k]
X[k + N/2] = E[k] − Wn^k · O[k]
```

Where:  
- `Wn^k = e^(−j2πk/N)` (twiddle factor)  
- `E[k], O[k]` are even and odd indexed inputs  

---

## 🛠️ Implementation Details
- **Language:** Verilog HDL  
- **FFT Size:** 8-point  
- **Algorithm:** Radix-2 DIT  
- **Design Style:** Modular (butterfly + stage-wise design)  
- **Arithmetic:** Fixed-point / Integer (customizable)  

---

## 📂 Project Structure
```
├── fft_top.v
├── butterfly.v
├── twiddle_rom.v
├── stage1.v
├── stage2.v
├── stage3.v
├── testbench.v
```

---

## ▶️ Simulation
Compile and run using any Verilog simulator:

Example (Icarus Verilog):
```
iverilog -o fft testbench.v fft_top.v
vvp fft
```

View waveform using GTKWave or any supported viewer.

---

## 📊 Results
- FFT output verified against MATLAB/C++ reference implementation  
- Correct frequency-domain transformation observed  
- Functional validation across multiple input test cases  

---

## 🔧 Future Work
- Extend to **64-point FFT architecture**  
- Introduce pipelined FFT design  
- Optimize fixed-point precision  
- FPGA implementation and timing analysis  

---

## 🎯 Key Learning Outcomes
- Hardware implementation of FFT algorithms  
- Butterfly architecture and data flow understanding  
- Fixed-point arithmetic in DSP systems  
- Scalable FFT design methodology  

---

## 📜 License
This project is open-source and available under the MIT License.
