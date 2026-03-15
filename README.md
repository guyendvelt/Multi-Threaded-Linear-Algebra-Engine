# Multi-Threaded Linear Algebra Engine

An advanced parallel computing engine in Java designed to solve complex linear algebra expressions on large matrices by optimizing system resources and implementing intelligent thread management.

## Technical Highlights

* **Custom Fatigue-Aware Scheduling (TiredExecutor)**: Implemented a unique execution service that manages worker threads (`TiredThread`) based on their "fatigue" levels. The system utilizes a `PriorityBlockingQueue` (min-heap) to schedule tasks to the most rested available thread, ensuring a fair workload distribution (Fairness) and optimizing CPU performance.
* **Thread-Safe Shared Memory Model**: Developed the `SharedMatrix` class to enable safe, concurrent data access. It implements fine-grained Read/Write locking at the individual vector level, allowing different threads to operate on separate parts of the matrix simultaneously without unnecessary contention.
* **Parallel Computation Tree Resolution**: The engine recursively resolves mathematical expression trees. At each step, the system identifies "resolvable" nodes (operations ready for execution) and submits them to the executor for parallel processing across multiple cores.
* **Optimized Matrix Operations**:
* **Matrix Multiplication**: Employs intelligent **Row-Major** and **Column-Major** representations to enhance memory access patterns (Cache Locality) during vector-matrix multiplications.
* **Arithmetic Operations**: Features parallel implementations for addition (ADD), negation (NEGATE), and transposition at the row level to maximize multi-core utilization.


* **Performance Monitoring & Reporting**: Includes a built-in mechanism to generate detailed activity reports. These reports display each worker's fatigue, active work time versus idle time, and a **Fairness Score** calculated based on the sum of squared deviations of workload distribution.

## Tech Stack

* **Language**: Java 11+.
* **Concurrency**: `PriorityBlockingQueue`, `AtomicInteger`, custom thread implementation, and manual lock management.
* **Build Tool**: Maven.
* **Data Formats**: JSON-based input for computation trees and output for results.

## System Architecture

1. **Parsing Phase**: The system receives a computation tree where each node represents a mathematical operation or a matrix operand.
2. **Scheduling Phase**: The `LinearAlgebraEngine` traverses the tree and submits independent, resolvable tasks to the `TiredExecutor`.
3. **Execution Phase**: Tasks are distributed among worker threads, each securely updating the `SharedMatrix`.
4. **Reporting Phase**: Upon completion, a detailed report can be generated to analyze the efficiency and load balance of the parallel execution.

---

### Professional Summary

This project demonstrates deep proficiency in **Concurrent Programming** and mathematical optimization. It showcases the ability to build a custom thread management framework from scratch, solve complex synchronization challenges in shared memory environments, and implement high-performance algorithms tailored for modern multi-core hardware.