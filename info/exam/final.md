# Computer Architecture Cheat Sheet

Revolution of Computing: Computing power has increased exponentially, driven by Moore's Law, which states that the number of transistors on a chip doubles roughly every two years. This revolution has introduced applications like: **Automotive Systems**: Control pollution, improve fuel efficiency, and enhance safety (e.g., airbags, lane-departure systems). **Mobile Communication**: Smartphones enable near-universal connectivity. **Scientific Breakthroughs**: Human Genome Project and other research projects rely on affordable and powerful computing.

Implications of exponential progress: If the transportation industry matched computing improvements, a trip from New York to London would cost a penny and take a second.

Three Classes of Computers: - Personal Computers (PCs) Designed for individual use, balance performance and cost, examples: Laptops, desktops.  Servers - Handle workloads for multiple users or large-scale computations, range from simple file servers to powerful supercomputers, emphasize reliability and scalability. Embedded Computers - Integrated into devices to perform specific tasks, found in appliances, vehicles, and industrial machines.

Post-PC Era: Personal Mobile Devices (PMDs) like smartphones and tablets dominate. Cloud computing and SaaS deliver software without requiring local installation.
Moore's Law: Predicts exponential growth in hardware capabilities.
Embedded Systems: Computers built into other devices to perform specialized tasks.
Server: A computer that processes large workloads or multiple simultaneous user requests.

### Problems
1. **Identify Classes of Computers**:
   - A weather forecasting machine: **Server**.
   - A smartwatch: **Embedded Computer**.
   - A gaming desktop: **PC**.

2. **Performance Metric Calculation**:
   - **Question**: A processor has a clock rate of 3 GHz and executes 12 billion instructions. If the CPI is 2, find the execution time.
   - **Solution**:
     $
     \text{Execution Time} = \frac{\text{Instruction Count} \times \text{CPI}}{\text{Clock Rate}} = \frac{12 \times 10^9 \times 2}{3 \times 10^9} = 8 \, \text{seconds}.
     $

---

## Chapter 3: Processor Implementation



### Problems
1. **Analyze Instruction Execution**:
   - **Question**: A program consists of:
     - Load instructions: 2,000,000 (CPI = 5).
     - Arithmetic instructions: 5,000,000 (CPI = 2).
     - Branch instructions: 1,000,000 (CPI = 4).
   - Calculate total cycles and execution time for a 2 GHz processor.
   - **Solution**:
     $
     \text{Total Cycles} = (2,000,000 \times 5) + (5,000,000 \times 2) + (1,000,000 \times 4) = 23,000,000 \, \text{cycles}.
     $
     $
     \text{Execution Time} = \frac{\text{Total Cycles}}{\text{Clock Rate}} = \frac{23,000,000}{2 \times 10^9} = 0.0115 \, \text{seconds}.
     $

2. **Pipeline Speedup**:
   - **Question**: A non-pipelined processor executes 100 instructions in 500 ns. A pipelined processor with 5 stages and a 1 ns clock cycle executes the same instructions. Calculate speedup.
   - **Solution**:
     Non-pipelined time: \(100 \times 5 \, \text{ns} = 500 \, \text{ns}\).
     Pipelined time: \(5 \, \text{ns (filling stages)} + 95 \, \text{ns} = 100 \, \text{ns}\).
     Speedup: \(\frac{500}{100} = 5\).

---

## Chapter 4: Memory Hierarchy

Principle of Locality: Temporal Locality: Recently accessed data is likely to be reused soon. Spatial Locality: Data near recently accessed addresses is also likely to be accessed.

Memory Hierarchy: Organized from fastest (and smallest) to slowest (and largest):
1. Registers
2. L1 Cache
3. L2/L3 Cache
4. Main Memory
5. Disk/Secondary Storage

Performance metrics:
- Hit Rate: Fraction of accesses found in the cache.
- Miss Rate: Fraction of accesses not found in the cache (\(1 - \text{Hit Rate}\)).
- Miss Penalty: Time to retrieve data from a lower level.

- Cache Line: The smallest unit of data in a cache.
- Hit Time: Time to access the cache.
- Miss Penalty: Time to retrieve a cache miss from the next level.

### Problems
1. **Cache AMAT Calculation**:
   - A processor has:
     - Hit rate: 95%.
     - Cache hit time: 1 ns.
     - Miss penalty: 50 ns.
   - **Question**: Calculate AMAT.
   - **Solution**:
     $
     \text{AMAT} = \text{Hit Time} + (\text{Miss Rate} \times \text{Miss Penalty}) = 1 + (0.05 \times 50) = 3.5 \, \text{ns}.
     $

2. **Optimization**:
   - **Question**: If miss penalty drops to 40 ns, calculate new AMAT.
   - **Solution**:
     $
     \text{AMAT} = 1 + (0.05 \times 40) = 3 \, \text{ns}.
     $

---

## Chapter 5: Parallel Processing

### Key Concepts
- **Parallelism**:
  - Multiple processors handle parts of a program simultaneously.
  - Types:
    - **Data-Level Parallelism**: Operate on different pieces of data.
    - **Task-Level Parallelism**: Execute independent tasks on separate processors.

- **Amdahl's Law**:
  - Limits the speedup achievable with parallelism:
    $
    \text{Speedup} = \frac{1}{\text{(Sequential Fraction)} + \frac{\text{(Parallel Fraction)}}{\text{Number of Processors}}}.
    $

- **Scaling**:
  - **Strong Scaling**: Speedup without increasing problem size.
  - **Weak Scaling**: Speedup by proportionally increasing problem size.

### Terminology
- **Multicore Processor**: A processor with multiple cores in a single chip.
- **Shared Memory Multiprocessor (SMP)**: Processors share a single memory address space.
- **Synchronization**: Coordination between processors to ensure correct results.

### Problems
1. **Amdahl’s Law Application**:
   - **Question**: A program is 20% sequential. Calculate speedup with 4 processors.
   - **Solution**:
     $
     \text{Speedup} = \frac{1}{0.2 + \frac{0.8}{4}} = \frac{1}{0.2 + 0.2} = 2.5.
     $

2. **Strong vs. Weak Scaling**:
   - **Question**: A workload has 10% sequential tasks. What is the theoretical maximum speedup for 10 processors?