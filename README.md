

# Synchronous FIFO with SystemVerilog Assertions

## Overview

A parameterized **Synchronous FIFO** designed in Verilog and verified using **SystemVerilog Assertions (SVA)**.

The project verifies FIFO functionality including reset, data integrity, full/empty conditions, and read/write pointer behavior.

## Features

* Parameterized FIFO width and depth
* Synchronous read/write operations
* Full and empty flag generation
* Read/write pointer management
* Randomized testbench stimulus
* Assertion-based verification using SVA
* Data integrity checking

## Architecture

```text
        +-------------------+
        |   Synchronous FIFO|
        |                   |
Data -->| Memory            |--> Data Out
        |                   |
Write ->| Write Pointer     |
Read  ->| Read Pointer      |
        |                   |
        | Full / Empty      |
        +-------------------+
                 |
                Clock
```

## Configuration

Current configuration:

```text
Data Width : 4 bits
FIFO Depth : 16 entries
Clock      : 100 MHz
```

The FIFO is parameterized:

```verilog
parameter WIDTH = 4;
parameter DEPTH_LEN = 4;
```

## SystemVerilog Assertions

The design includes assertions to verify:

1. **Reset behavior** – pointers reset and FIFO becomes empty.
2. **Data integrity** – written data matches the corresponding read data.
3. **No write when full** – write pointer remains unchanged.
4. **No read when empty** – read pointer remains unchanged.
5. **Write pointer increment** – increments by one on a valid write.
6. **Read pointer increment** – increments by one on a valid read.

Important SVA features used:

```text
property
sequence
$past
$stable
first_match
disable iff
```

## Testbench

The testbench performs:

```text
Reset
  ↓
Write Random Data
  ↓
Read Data
  ↓
SVA Verification
  ↓
Pass / Assertion Failure
```

Random data is generated using `$urandom`.

## Project Structure

```text
Synchronous-FIFO/
│
├── syncFIFO_v2.v    # FIFO RTL + SVA
└── test_v2.v        # Testbench
```

## Tools

* Verilog / SystemVerilog
* SystemVerilog Assertions
* Vivado / Simulator
* RTL Simulation

## Objective

To demonstrate **RTL FIFO design and assertion-based verification** using SystemVerilog.
