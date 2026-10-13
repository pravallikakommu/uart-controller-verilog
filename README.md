# UART Transceiver in Verilog

![Verilog](https://img.shields.io/badge/Language-Verilog-blue)
![Quartus](https://img.shields.io/badge/Intel-Quartus_Prime-0071C5)
![Simulation](https://img.shields.io/badge/Simulation-Testbench-success)
![License](https://img.shields.io/badge/License-MIT-green)

A modular **UART (Universal Asynchronous Receiver/Transmitter)** implementation in Verilog HDL featuring configurable baud-rate generation, transmitter and receiver modules, and comprehensive testbenches.

This project was developed as part of a digital design and FPGA learning workflow using **Intel Quartus Prime**.

---

# Features

- UART Transmitter
- UART Receiver
- Configurable Baud Rate Generator
- 8-bit Data Transmission
- Start and Stop Bit Detection
- Modular RTL Design
- Loopback Testbench
- Quartus Prime Compatible

---

# Project Structure

```
UART_project/
│
├── rtl/
│   ├── baud_generator.v
│   ├── uart_tx.v
│   └── uart_rx.v
│
├── tb/
│   ├── uart_tx_tb.v
│   └── uart_loopback_tb.v
│
├── docs/
│   └── uart_documentation.png
│
├── UART_project.qpf
├── UART_project.qsf
├── README.md
├── LICENSE
└── .gitignore
```

---

# UART Architecture

The UART design consists of three independent RTL modules:

- **Baud Generator**
  - Generates baud tick pulses from the system clock.

- **UART Transmitter**
  - Serializes 8-bit parallel data.
  - Adds Start and Stop bits.
  - Sends data LSB first.

- **UART Receiver**
  - Detects the Start bit.
  - Samples incoming bits using the baud tick.
  - Reconstructs the original 8-bit data.
  - Indicates when valid data has been received.

---

# Data Frame Format

This implementation follows the standard **8-N-1 UART protocol**.

| Field | Size |
|-------|------|
| Start Bit | 1 |
| Data Bits | 8 |
| Parity | None |
| Stop Bit | 1 |

Transmission Order

```
Idle → Start → D0 → D1 → D2 → D3 → D4 → D5 → D6 → D7 → Stop
```

---

# Documentation

The repository includes a documentation diagram illustrating:

- UART architecture
- Transmission timing
- Reception timing
- Loopback communication

<p align="center">
<img src="docs/uart_documentation.png" width="900">
</p>

---

# Testbenches

Included testbenches:

- UART Transmitter Testbench
- UART Loopback Testbench

The loopback configuration verifies successful communication by connecting:

```
TX ---------------> RX
```

Expected Result:

```
Transmitted Byte == Received Byte
```

---

# How to Simulate

Using **Icarus Verilog**

Compile

```bash
iverilog -o uart_tb rtl/*.v tb/*.v
```

Run

```bash
vvp uart_tb
```

Generate waveform

```bash
gtkwave dump.vcd
```

---

# Tools Used

- Verilog HDL
- Intel Quartus Prime
- Icarus Verilog
- GTKWave

---

# Future Improvements

- Configurable Data Width
- Even/Odd Parity Support
- FIFO Buffers
- Interrupt Support
- AXI/UART Interface
- FPGA Demonstration

---

# License

This project is licensed under the MIT License.

---


