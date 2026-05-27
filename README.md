# SPI-design
# 🔗 SPI Slave Interface with Single Port RAM

> FPGA-Based SPI Communication System using Verilog on Xilinx Artix-7

---

# 📘 Project Description

This project implements an **SPI Slave Controller** connected to a **256-byte Single Port RAM** on a Xilinx Artix-7 FPGA.

The design enables serial communication between an SPI master and internal memory through standard SPI signals.

The SPI slave receives commands and data serially, decodes the operation type, then performs memory read/write transactions accordingly.

---

# 🎯 Project Objectives

- Implement SPI slave communication protocol
- Interface SPI with internal RAM
- Support serial read/write operations
- Compare FSM encoding techniques
- Achieve timing-efficient FPGA implementation

---

# 🧩 System Components

## 1️⃣ SPI Slave Controller

Finite State Machine responsible for:

- Receiving serial commands
- Decoding operation type
- Controlling RAM access
- Sending serial output data

### FSM States

| State | Function |
|---|---|
| IDLE | Wait for slave select |
| CHK_CMD | Decode incoming command |
| WRITE | Store incoming data |
| READ_ADD | Capture read address |
| READ_DATA | Transmit RAM data |

---

## 2️⃣ Single Port RAM

| Feature | Value |
|---|---|
| Memory Depth | 256 Locations |
| Data Width | 8-bit |
| Access Type | Single Port |
| Operations | Read / Write |

---

## 3️⃣ Top Module

The top-level module integrates:

- SPI Slave
- RAM Block
- Control Signals
- Data Routing

---

# 📡 SPI Communication

The design communicates using four standard SPI lines:

| Signal | Direction | Description |
|---|---|---|
| MOSI | Input | Master Out Slave In |
| MISO | Output | Master In Slave Out |
| SS_n | Input | Active-low slave select |
| CLK | Input | SPI serial clock |

---

# 🧠 Command Format

The SPI slave processes **10-bit frames**.

The upper two bits define the operation type:

| Command | Operation |
|---|---|
| `00` | Write Address |
| `01` | Write Data |
| `10` | Read Address |
| `11` | Read Data |

---

# ⚙️ FSM Encoding Exploration

Three FSM encoding styles were implemented and analyzed:

| Encoding Type | Description |
|---|---|
| Sequential | Binary encoded FSM |
| Gray | Single-bit transition encoding |
| One-Hot | One active state bit |

The final implementation was selected based on:

- Timing Performance
- Resource Utilization
- Vivado Timing Reports

---

# 🧪 Verification Strategy

## Simulation Features

- Functional verification of SPI transactions
- Address and data integrity checking
- Read/write operation validation
- Waveform inspection
- FSM transition verification

---

## Tested Scenarios

| Test Case | Purpose |
|---|---|
| Write Address | Verify RAM address loading |
| Write Data | Verify memory write operation |
| Read Address | Verify address decoding |
| Read Data | Verify serial data transmission |
| FSM Transition | Validate state changes |
| Invalid Frames | Check robustness |
| Continuous Transfer | Verify sequential operations |

---

# 🛠️ FPGA Design Flow

| Stage | Status |
|---|---|
| RTL Design | ✅ Completed |
| Simulation | ✅ Passed |
| Synthesis | ✅ Successful |
| Implementation | ✅ Timing Met |
| Bitstream Generation | ✅ Generated |
| Linting | ✅ No Errors |

---

# 💻 Tools & Software

- Verilog HDL
- QuestaSim
- Xilinx Vivado
- FPGA Verification Flow

---

# 📂 Repository Structure

```bash
SPI_Slave_Project/
│
├── rtl/
│   ├── SPI_Slave.v
│   ├── Single_Port_RAM.v
│   └── top_module.v
│
├── tb/
│   └── SPI_Slave_tb.v
│
├── sim/
│   └── run.do
│
├── constraints/
│   └── timing.xdc
│
└── README.md
```

---

# 📊 Results Summary

| Metric | Result |
|---|---|
| SPI Communication | ✅ Functional |
| RAM Read/Write | ✅ Verified |
| FSM Operation | ✅ Stable |
| Timing Constraints | ✅ Met |
| Simulation Tests | ✅ Passed |
| Linting Report | ✅ Clean |

---

# 🚀 Key Features

- Fully functional SPI slave controller
- Integrated single-port RAM
- Multiple FSM encoding implementations
- FPGA-ready architecture
- Modular and scalable RTL design
- Clean timing closure on Artix-7 FPGA

---

# ▶️ Simulation Command

```tcl
vsim -do sim/run.do
```

---

# 📚 References

- Xilinx Artix-7 FPGA Documentation
- SPI Protocol Specification

---

# 👨‍💻 Author

### Abdelrahman Youssef

Electronics & Communication Engineering Student

Areas of Interest:

- Digital Design
- FPGA Systems
- Verification
- Embedded Hardware
- Communication Protocols
