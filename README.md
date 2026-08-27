# 5-Stage RISC-V Pipelined Processor

A Verilog implementation of a RISC-V processor, including both a **single-cycle** design and a **5-stage pipelined** design with hazard detection/handling. Branch prediction is not yet implemented (branches are currently resolved without prediction, e.g. stall/flush on resolution).

## Pipeline Stages

The pipelined design follows the classic 5-stage RISC-V pipeline:

1. **Fetch (IF)** — `fetch_cycle.v`
2. **Decode (ID)** — `decode_cycle.v`
3. **Execute (EX)** — `execute_cycle.v`
4. **Memory (MEM)** — `memory_cycle.v`
5. **Writeback (WB)** — `writeback_cycle.v`

Each `*_cycle.v` module wraps the logic and pipeline registers for that stage, integrated together in `top.v`.

## Features

- **Single-cycle implementation** — a baseline, non-pipelined datapath for correctness reference.
- **5-stage pipelined implementation** — IF/ID/EX/MEM/WB with pipeline registers (`flipflop.v`).
- **Hazard handling** (`hazard.v`) — detects and resolves data hazards (via stalling and/or forwarding) and control hazards from branches/jumps.
- **Modular datapath components** — separate, reusable modules for the ALU, register file, memories, immediate extension, and muxes.

## Not Yet Implemented

- Branch prediction (branches are currently handled without a predictor).

## Simulation

The design is simulated using a Verilog simulator
