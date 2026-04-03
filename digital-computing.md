---
marp: true
theme: default
paginate: true
style: |
  section {
    font-family: 'Segoe UI', sans-serif;
    font-size: 28px;
  }
  h1 { color: #1a1a2e; font-size: 2em; }
  h2 { color: #16213e; font-size: 1.5em; border-bottom: 3px solid #0f3460; padding-bottom: 6px; }
  code { background: #f0f4ff; border-radius: 4px; padding: 2px 6px; }
  pre { background: #1a1a2e; color: #e0e0e0; border-radius: 8px; padding: 16px; }
  .highlight { color: #e94560; font-weight: bold; }
  table { border-collapse: collapse; width: 100%; }
  th { background: #0f3460; color: white; padding: 8px 12px; }
  td { border: 1px solid #ccc; padding: 8px 12px; text-align: center; }
---

# Digital Computing
## From AND Gates to Algorithms

**Teaching your juniors the magic inside every computer**

---

## 🗺️ Roadmap

```
Electricity → Logic Gates → Binary Numbers
     ↓
Circuits → Memory → CPU
     ↓
Machine Code → Assembly → High-Level Languages
     ↓
Algorithms → Complexity → The Programs You Write Today
```

> Every app, game, and AI starts here.

---

## ⚡ Everything is Electricity

A computer only understands **two states**:

| State | Voltage | We call it |
|-------|---------|------------|
| Off   | ~0 V    | **0** (FALSE) |
| On    | ~5 V    | **1** (TRUE)  |

This is called **binary** — "bi" meaning *two*.

> 💡 Your entire Instagram feed, a 3-hour movie, and GPT-4 are all ultimately just **billions of 0s and 1s** switching on and off, billions of times per second.

---

## 🔧 Logic Gates — The Basic Building Blocks

A **logic gate** is a tiny electronic circuit that takes one or two binary inputs and produces one binary output based on a rule.

They are built from **transistors** — microscopic switches etched onto silicon.

> Modern CPUs contain **over 50 billion transistors**, each smaller than a virus.

---

## 🔧 The AND Gate

**Rule:** Output is 1 **only if both** inputs are 1.

```
  A ──┐
      ├──[ AND ]──── Output
  B ──┘
```

| A | B | A AND B |
|---|---|---------|
| 0 | 0 |    0    |
| 0 | 1 |    0    |
| 1 | 0 |    0    |
| 1 | 1 |    1    |

*Real-world analogy: A lamp that turns on only when **both** switches are flipped.*

---

## 🔧 The OR Gate

**Rule:** Output is 1 **if at least one** input is 1.

```
  A ──┐
      ├──[ OR ]──── Output
  B ──┘
```

| A | B | A OR B |
|---|---|--------|
| 0 | 0 |   0    |
| 0 | 1 |   1    |
| 1 | 0 |   1    |
| 1 | 1 |   1    |

*Real-world analogy: A lamp that turns on when **either** switch is flipped.*

---

## 🔧 The NOT Gate (Inverter)

**Rule:** Output is the **opposite** of the input.

```
  A ──[ NOT ]──── Output
```

| A | NOT A |
|---|-------|
| 0 |   1   |
| 1 |   0   |

> 💡 With just **AND, OR, and NOT**, you can build **any logic** imaginable — including an entire CPU.

---

## 🔧 The NAND Gate — Why It's Special

**NAND = NOT AND** — output is 0 only when both inputs are 1.

| A | B | NAND |
|---|---|------|
| 0 | 0 |  1   |
| 0 | 1 |  1   |
| 1 | 0 |  1   |
| 1 | 1 |  0   |

### 🌟 NAND is "functionally complete"
You can build **AND, OR, and NOT** using only NAND gates.
→ A computer could be built from a **single type of gate**.

---

## 🔢 Binary Numbers — Counting in Base 2

We count in **base 10** (digits 0–9). Computers count in **base 2** (digits 0–1).

| Place value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-------------|-----|----|----|----|---|---|---|---|
| Bit         |  0  |  0 |  1 |  0 | 1 | 1 | 0 | 1 |

**0010 1101** = 32 + 8 + 4 + 1 = **45** in decimal

> Each binary digit is called a **bit**.
> 8 bits = 1 **byte**.
> 1 byte can represent **256** different values (2⁸).

---

## 🔢 Why Binary? Why Not Base 10?

| Base 10 (decimal) | Base 2 (binary) |
|--------------------|-----------------|
| Needs 10 distinct voltage levels | Only needs 2 (on/off) |
| Hard to distinguish reliably | Easy — high voltage or low voltage |
| Complex circuits | Simple, reliable, fast |
| Harder to mass-produce | Scales to billions of transistors |

> **Reliability** and **simplicity** are why binary won.

---

## ➕ Half Adder — Adding Two Bits

Combining gates to do **arithmetic**:

```
  A ──┬──[ XOR ]──── Sum
  B ──┴──[ AND ]──── Carry
```

| A | B | Sum | Carry |
|---|---|-----|-------|
| 0 | 0 |  0  |   0   |
| 0 | 1 |  1  |   0   |
| 1 | 0 |  1  |   0   |
| 1 | 1 |  0  |   1   |

Chain multiple **Full Adders** together → add any size numbers.
This is literally how your CPU does **1 + 1**.

---

## 🧠 From Adders to the ALU

The **Arithmetic Logic Unit (ALU)** is a circuit built from gates that can:

- ➕ Add and subtract
- 🔢 Compare numbers (equal? greater than?)
- 🔀 Perform bitwise AND, OR, NOT, XOR
- ↕️ Shift bits left/right (fast multiply/divide by 2)

The ALU is the **"calculator"** inside every CPU.

> All mathematical operations a computer does — from rendering pixels to training neural networks — trace back to the ALU.

---

## 💾 Memory — Storing a Bit

An **SR Latch** built from two NAND gates can **remember** a single bit:

```
  Set ──┬──[ NAND ]──┬── Q   (stored value)
        │     ↑      │
        └──[ NAND ]──┘── Q̄  (inverse)
  Reset─┘
```

- Set input → stores **1**, and it *stays* 1 even when Set goes back to 0
- Reset input → stores **0**

Scale this up:
- **1 latch** = 1 bit
- **8 latches** = 1 byte
- **8 billion latches** = 1 GB of RAM

---

## 🗄️ The Memory Hierarchy

Faster memory is more expensive and physically larger per bit — so computers use layers:

```
  Registers (CPU, ~1 ns, ~KB)
       ↓
  L1 Cache (~1 ns, ~64 KB)
       ↓
  L2/L3 Cache (~5 ns, ~MB)
       ↓
  RAM (~100 ns, ~GB)
       ↓
  SSD (~100 µs, ~TB)
       ↓
  Hard Drive / Cloud (~ms, ~PB)
```

> Your program runs fast when data stays in cache. **Cache misses** are a major cause of slowdowns.

---

## ⚙️ The CPU — Putting It All Together

A CPU has three main jobs, done **millions of times per second**:

```
  ┌─────────────────────────────────────┐
  │  Fetch → Decode → Execute           │
  │                                     │
  │  Fetch:   Read next instruction     │
  │           from memory               │
  │  Decode:  Figure out what it means  │
  │  Execute: Do it (ALU, memory, etc.) │
  └─────────────────────────────────────┘
```

This is the **Fetch-Decode-Execute cycle** — the heartbeat of every computer.

---

## 📝 Machine Code & Assembly

The CPU only understands **machine code** — raw binary instructions:

```
10110000 01100001   →  Move the value 97 into register AL
```

**Assembly language** gives human-readable names to these instructions:

```asm
MOV AL, 61h   ; Move hex 61 (= decimal 97 = ASCII 'a') into AL
```

> Early programmers wrote everything in assembly. It was tedious, error-prone, and machine-specific — one reason high-level languages were invented.

---

## 🖥️ High-Level Languages — Abstraction Layers

```
  Your Python code:   x = 5 + 3
          ↓  Compiler/Interpreter
  Assembly:           ADD R1, 5, 3
          ↓  Assembler
  Machine code:       0001 0000 0101 0011
          ↓  Electronics
  Transistors:        (billions of switches flip)
```

Each layer **hides complexity** and lets us think at a higher level.

> **Abstraction** is the most powerful concept in computing.

---

## 🧮 What is an Algorithm?

An **algorithm** is a step-by-step set of instructions to solve a problem.

**Example: Find the largest number in a list**

```
1. Start: assume first number is the largest
2. Look at the next number
3. If it is larger, update "largest"
4. Repeat steps 2–3 until end of list
5. Return "largest"
```

This is the **linear search / max-find** algorithm.

> An algorithm is a *recipe*. The computer is the *kitchen*.

---

## 🔍 Searching — Linear vs Binary Search

**Linear Search** — check one by one:
```
List: [3, 7, 1, 9, 4]   Find: 9
→ Check 3, 7, 1, 9 ✓   (4 steps)
```

**Binary Search** — only works on sorted lists, halves the problem each step:
```
Sorted: [1, 3, 4, 7, 9]   Find: 9
→ Middle = 4. 9 > 4, search right half [7, 9]
→ Middle = 7. 9 > 7, search right half [9]
→ Found! (3 steps)
```

| Algorithm | Steps for 1 billion items |
|-----------|--------------------------|
| Linear    | 1,000,000,000            |
| Binary    | **30**                   |

---

## 📊 Algorithm Complexity — Big-O Notation

**Big-O** describes how an algorithm's runtime grows with input size *n*:

| Notation  | Name        | Example                        |
|-----------|-------------|--------------------------------|
| O(1)      | Constant    | Array index lookup             |
| O(log n)  | Logarithmic | Binary search                  |
| O(n)      | Linear      | Linear search                  |
| O(n log n)| Linearithmic| Merge sort                     |
| O(n²)     | Quadratic   | Bubble sort                    |
| O(2ⁿ)     | Exponential | Brute-force password crack     |

> A bad algorithm can make even the fastest CPU useless. A great algorithm can run on a potato.

---

## 🔄 Sorting — Bubble Sort vs Merge Sort

**Bubble Sort** O(n²) — simple but slow:
```
[5, 3, 1, 4] → [3, 1, 4, 5] → [1, 3, 4, 5]
Compare neighbours, swap if wrong order. Repeat.
```

**Merge Sort** O(n log n) — divide and conquer:
```
[5, 3, 1, 4]
→ [5, 3]  [1, 4]
→ [3, 5]  [1, 4]   (sort each half)
→ [1, 3, 4, 5]     (merge)
```

> Sorting sounds trivial. But your database, search engine, and GPS **depend on fast sorting** to work in real time.

---

## 🌐 Connecting It All — The Layers of a Computer

```
  Problem (e.g., "Show me a webpage")
       ↓ Algorithm
  Program (Python / JavaScript)
       ↓ Compiler / Interpreter
  Machine Code (binary instructions)
       ↓ CPU (Fetch-Decode-Execute)
  Logic Circuits (ALU, registers, cache)
       ↓ Gates (AND, OR, NOT)
  Transistors (billions of on/off switches)
       ↓ Physics (electricity, silicon)
```

Every single step in this chain was designed, engineered, and optimised by humans.

---

## 🚀 From Gates to the Modern World

The same principles — gates, binary, circuits, algorithms — power:

- 🤖 **AI & Machine Learning** — matrix multiplications, billions of times per second
- 🎮 **Video Games** — physics engines, rendering pipelines
- 📱 **Smartphones** — ARM chips with 15 billion transistors
- 🛰️ **Space Exploration** — guidance computers, telemetry
- 💊 **Medical Devices** — pacemakers, MRI machines

> The transistor was invented in **1947**.
> Today, we fit **50 billion** of them on a chip the size of your fingernail.

---

## 🧩 Key Takeaways

| Concept | One-line summary |
|---------|-----------------|
| Logic gates | AND/OR/NOT — the atoms of computation |
| Binary | Computers speak in 0s and 1s for reliability |
| Circuits | Gates combine to do arithmetic and store memory |
| CPU | Fetch, decode, execute — billions of times/second |
| Abstraction | Each layer hides complexity from the layer above |
| Algorithm | A precise recipe for solving a problem |
| Big-O | Measures how fast an algorithm scales |

---

## 🧪 Try It Yourself

1. **Build a half adder** using an online logic gate simulator (e.g., *logic.ly* or *circuitverse.org*)

2. **Trace binary**: Convert your age to binary. Convert it back.

3. **Compare search algorithms**: Write linear and binary search in Python. Time them on a list of 1 million numbers.

4. **Explore Big-O**: Why does doubling the input size double linear search time, but only add 1 step to binary search?

> The best way to understand computing is to **build something**.

---

## 📚 Resources to Go Deeper

- 📘 **"Code" by Charles Petzold** — builds a computer from scratch, concept by concept
- 🎓 **CS50 (Harvard, free on edX)** — world's most popular intro CS course
- 🔬 **"But How Do It Know?" by J. Clark Scott** — a computer from first principles
- 🧑‍💻 **Nand2Tetris (nand2tetris.org)** — build a CPU and programming language from NAND gates
- 🎥 **3Blue1Brown (YouTube)** — visual intuitions for CS and maths

---

## 🙏 Thank You!

**Digital Computing: From AND Gates to Algorithms**

```
  0 + 0 = 0
  0 + 1 = 1
  1 + 0 = 1
  1 + 1 = 10  ← This is how it all begins.
```

*Questions? Curiosity? Both are welcome.*

---
<!-- Speaker notes template for each slide are embedded via marp comments.
     To export: npx @marp-team/marp-cli digital-computing.md --html
     or open with the Marp extension in VS Code. -->
