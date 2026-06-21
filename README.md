# DSP-FIR-Lowpass-Filter
---

## Introduction

This project implements a **Digital Signal Processing (DSP) FIR Low Pass Filter (LPF)** using **Verilog HDL** on FPGA. The design filters out high-frequency noise from an input signal while preserving the low-frequency component.The project uses the **CORDIC (Coordinate Rotation Digital Computer)** algorithm to generate sine wave test signals at different frequencies. A noisy composite signal is created by combining a low-frequency signal (2 MHz) and a high-frequency noise signal (30 MHz). The FIR filter processes this signal and removes the unwanted high-frequency component.This project demonstrates practical FPGA-based digital filtering used in communication systems, audio processing, biomedical signal processing, and sensor noise reduction.

---

## Tools Used

* **Verilog HDL** — Digital hardware design
* AMD **Vivado Design Suite** — Simulation and synthesis
* **CORDIC IP Core** — Sine wave generation
* **FIR Filter Architecture** — Digital filtering
* **Waveform Viewer** — Signal analysis
* **FPGA Board (optional)** — Hardware implementation

---

## Features

* 9-Tap FIR Low Pass Filter
* Removes high frequency noise effectively
* Uses fixed-point arithmetic
* Real-time digital signal filtering
* CORDIC-generated sine wave test signals
* Verilog-based modular implementation
* Synthesizable on FPGA
* Easy scalable architecture for higher-order filters

---

## Project Structure

```text
FIR_LPF_Project/
│── src/
│   ├── fir.v              # FIR Filter top module
│   ├── cordic.v           # CORDIC sine generator
│   ├── signal_mixer.v     # Combines signals to create noisy input
│
│── tb/
│   ├── fir_tb.v           # Testbench
│
│── sim/
│   ├── waveform1.png      # Signal generation waveform
│   ├── waveform2.png      # FIR output waveform
│
│── README.md
```

---

## Working Principle

### Step 1: Signal Generation

Two sine waves are generated using CORDIC:

* **2 MHz sine wave** → Desired signal
* **30 MHz sine wave** → Noise signal

From your simulation:

* `sin_2MHz`
* `sin_30MHz`

---

### Step 2: Signal Mixing

Both signals are added together:

Noisy Signal:

[
x(n) = sin(2MHz) + sin(30MHz)
]

This creates a mixed signal containing both low-frequency information and high-frequency noise.

Waveform observed:

* `noisy_signal`

---

### Step 3: FIR Filtering

The FIR LPF uses weighted coefficients:

[
y(n) = h(k)x(n-k)
]

where:

* `h(k)` = filter coefficients
* `x(n-k)` = delayed input samples

The FIR filter allows low-frequency components to pass while attenuating high-frequency noise.

---

### Step 4: Output Signal

After filtering:

* 2 MHz component remains
* 30 MHz noise gets reduced

Output:

* `filtered_signal`

---

## Simulation Results

### Waveform Analysis

### 1. Input Signal (2 MHz)

Observed waveform shows smooth low-frequency sinusoidal behavior.
<img width="1375" height="713" alt="Screenshot 2026-06-18 102608" src="https://github.com/user-attachments/assets/c6616696-3ff9-4283-ba1d-17e9fcc41410" />

**Analysis:**

* Stable periodic waveform
* Represents desired signal

---

### 2. Noise Signal (30 MHz)
<img width="1375" height="713" alt="Screenshot 2026-06-18 102608" src="https://github.com/user-attachments/assets/ccb03ec4-8b11-4bf5-a7f9-0b9571dd13a4" />

High-frequency oscillations are clearly visible.

**Analysis:**

* Rapid transitions
* Represents unwanted noise

---

### 3. Noisy Composite Signal

The noisy signal combines both frequencies.

Observed behavior:

* High-frequency ripples superimposed on low-frequency sine wave

**Analysis:**

* Demonstrates practical noisy environment
* Input for FIR filtering

---

### 4. Filtered Output

From your waveform:

* The output becomes smoother
* High-frequency components are attenuated
* Low-frequency waveform shape is preserved

**Result Interpretation:**

Before filtering:

* Signal contains sharp oscillations

After filtering:

* Signal becomes smoother
* Noise reduction achieved successfully

This proves the FIR LPF works correctly.

---

## Future Scope

* Increase filter order for better cutoff precision
* Implement adaptive FIR filters
* Use AXI Stream interface for AMD Zynq integration
* Hardware deployment on FPGA board
* Real-time ADC signal filtering
* Integration with DMA and DDR memory
* SD card logging for filtered data
* Audio signal processing applications
* Biomedical ECG/EEG filtering

---

## Applications

* Wireless Communication
* Audio Noise Reduction
* Radar Systems
* Biomedical Signal Processing
* Sensor Data Filtering
* Embedded DSP Systems
* Software Defined Radio (SDR)

---

## Conclusion

This project successfully demonstrates the implementation of a FIR Low Pass Filter using Verilog on FPGA. By generating noisy mixed-frequency signals and filtering them digitally, the system validates practical DSP concepts in hardware.

The simulation results confirm efficient suppression of high-frequency noise while maintaining the desired low-frequency signal.

This project serves as a strong foundation for advanced FPGA-based DSP systems.

---

Just paste this into your `README.md`. It’s structured well for GitHub and recruiter review.
