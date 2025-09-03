# Serial vs Parallel Execution in Python

This repository contains a Jupyter Notebook that explores the differences between **serial (sequential)** and **parallel (concurrent)** execution in Python. It demonstrates how tasks behave when run one after another versus when executed using multiple workers (threads or processes). The project also highlights performance improvements, overheads, and common pitfalls when using parallelism.

---

## 📌 Overview

Modern computers often have multiple CPU cores, but not all programs automatically run faster with parallelism. This notebook helps in understanding:

- When serial code is sufficient and efficient
- When to use **threads** (for I/O-bound tasks)
- When to use **processes** (for CPU-bound tasks)
- Why sometimes parallel execution can actually be slower
- How to measure execution time and evaluate speedup

---

## 📖 Notebook Contents

1. **Introduction to Concepts**  
   Explains concurrency vs parallelism, CPU-bound vs I/O-bound tasks, and the role of the Python GIL (Global Interpreter Lock).

2. **Serial Execution**  
   Demonstrates sequential execution of tasks as a baseline for comparison.

3. **Thread-Based Concurrency**  
   Uses `ThreadPoolExecutor` to show how I/O-bound workloads can benefit from threading.

4. **Process-Based Parallelism**  
   Uses `ProcessPoolExecutor` to leverage multiple CPU cores for computation-heavy tasks.

5. **Performance Measurement**  
   Compares execution times for serial, thread-based, and process-based approaches.

6. **Discussion & Observations**  
   Explains results, highlighting cases where parallelization helps and where it does not.

---

## 🔑 Key Concepts

- **Concurrency vs Parallelism**  
  - Concurrency is about handling multiple tasks at once (structuring the program).  
  - Parallelism is about *actually running* tasks simultaneously (requires multiple cores).  

- **CPU-bound vs I/O-bound**  
  - **CPU-bound** tasks spend most time on computation → best with processes.  
  - **I/O-bound** tasks spend time waiting (disk, network, etc.) → best with threads.  

- **The Global Interpreter Lock (GIL)**  
  - Python threads cannot run Python bytecode in true parallel for CPU-bound tasks.  
  - This limits performance gains from threads on heavy computations.  

---

## 🧩 Patterns Demonstrated

### Serial Execution
Tasks are executed one after another:
```python
results = [work(x) for x in data]
