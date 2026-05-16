<div align="center">

  <img src="https://capsule-render.vercel.app/api?type=waving&color=0bCEAF&height=200&section=header&text=8-Bit%20Gate-Level%20Microprocessor&fontSize=50&fontAlignY=35&animation=twinkling&fontColor=ffffff" />

  <p align="center">
    <b>A fully functional 8-bit CPU built entirely from scratch using only fundamental logic gates (AND, OR, NOT, XOR). <br> Zero pre-fabricated ICs. 100% hand-wired boolean logic.</b>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/Architecture-8--Bit-0bCEAF?style=for-the-badge" alt="Architecture" />
    <img src="https://img.shields.io/badge/Design_Level-Gate_Level-E34F26?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Simulator-[NI MULTISIM]-00599C?style=for-the-badge" />
  </p>
</div>

<br/>

> **The Philosophy:** To truly understand how a computer computes, you must strip away the abstractions. This project abandons standard microcontrollers and pre-built arithmetic logic units (ALUs). Every register, multiplexer, and control signal in this architecture is constructed from raw logic gates, meticulously wired together in software.

## 🧠 Core Architecture

This microprocessor follows a custom **[Von Neumann / Harvard - Choose One]** architecture. It features a custom Instruction Set Architecture (ISA), a hardwired Control Unit, and a gate-level ALU.

```mermaid
graph TD
    subgraph CPU ["8-Bit Microprocessor Core"]
        CU[Control Unit] --> |Control Signals| ALU
        CU --> |Load/Enable| REG
        
        subgraph REG ["Registers"]
            PC[Program Counter]
            IR[Instruction Register]
            A[Accumulator]
            B[B Register]
        end
        
        subgraph ALU_Block ["Arithmetic Logic Unit (Gate-Level)"]
            ALU((ALU))
        end
        
        A --> ALU
        B --> ALU
        ALU --> |Result| A
    end

    subgraph Memory_System ["Memory"]
        RAM[(RAM - 256 Bytes)]
    end

    PC --> |Address Bus| RAM
    RAM --> |Data Bus| IR
    ALU --> |Data Bus| RAM
    
    style CPU fill:#0D1117,stroke:#0bCEAF,stroke-width:2px,color:#fff
    style ALU_Block fill:#161b22,stroke:#E34F26,stroke-width:2px,color:#fff
    style Memory_System fill:#0D1117,stroke:#3776AB,stroke-width:2px,color:#fff
