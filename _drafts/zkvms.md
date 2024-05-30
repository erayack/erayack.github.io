---
layout: post
title: zkVMs
---

# zkVMs

## **Introduction to zkVMs**

A zkVM, or zero-knowledge Virtual Machine, is an emulation of a CPU architecture into a universal circuit that enables the computation and proving of any program from a given set of opcodes. In essence, a zkVM is a zk circuit that runs a virtual machine, with the program's instructions passed as public input to the circuit. Several projects, such as Risc0, Jolt, and Sp1, listed in the table, are actively developing zkVMs.

| Organization / Company | Project |
| --- | --- |
| @a16zcrypto | Jolt |
| @NexusLabsHQ | Nexus |
| @RiscZero | Risc0 |
| @SuccinctLabs | Sp1 |
| @lita_xyz | Valida |
| @the_matter_labs | zkOS |
| @0xPolygon | Miden |
| @ola_zkzkvm | Ola |
| @seagodcrypto | TritonVM |
| @StarkWareLtd | CairoVM |
| @fluentxyz | zkWASM |
| @ProjectZKM | zkM |

One of the primary goals when designing a zkVM is to maximize the prover's performance. However, it is surprising to note that not all zkVMs are designed with this objective in mind. The main advantage of zkVMs lies in providing developers with a seamless experience without exposing them to the underlying cryptographic complexities. Any program can be compiled to a defined set of opcodes, which, being finite and generally small, can be easily audited.

zkVMs allow developers to leverage existing tooling and compiler infrastructure. A single universal zkVM circuit can be sufficient to run all programs up to a certain bound, requiring only one verifier. This eliminates the need for a preprocessing step per circuit, which is necessary when using different manually written circuits that require different verifiers.

## Comparison to Traditional CPU Architectures

Traditional CPUs are physical integrated circuits containing millions or even billions of electrical components that execute machine-level instructions and perform operations on data. Over time, CPUs have evolved to include multiple cores for parallel processing, caches for fast memory access, and microcode for executing complex instructions.

In contrast, zkVMs are virtual emulations of CPU architectures using zk circuits, providing a higher level of abstraction over the underlying hardware. While this abstraction offers a more developer-friendly approach to zero-knowledge computation, it comes at the cost of performance compared to traditional CPUs.

## Current Limitations and Challenges

Despite their benefits, zkVMs as they currently exist are not a perfect solution. They exhibit much poorer performance compared to manually optimized circuits due to the extra overhead of adding abstractions such as memory, stack, and embedding instructions in the universal circuit.

Moreover, writing efficient circuits, whether manually or using libraries like arkworks, halo2 or DSLs such as Noir, is a challenging task that requires expertise and is prone to errors. This complexity is an issue, albeit arguably less significant than the performance overhead.

## Design Space and Tradeoffs

| VM Feature | Jolt | Risc0 | Sp1 |
| --- | --- | --- | --- |
| Design Approach | Sum-check protocol and lookup singularity with Lasso | STARKs lineage | STARKs lineage |
| Field of Operation | 256-bit field | 31-bit or 64-bit fields | - |
| Recursion Implementation | Not yet implemented | Implemented but close source | Partially implemented |
| Polynomial Commitment Scheme | Hyrax (can be replaced with Binius) | - | - |
| Field of operation | 256-bit | 31-bit | 64-bit |

## **STARKish zkVMs**

## Future Directions and Potential Optimizations

To make zkVMs more practical and efficient, researchers and developers are exploring various optimization techniques:

1. **Circuit Optimization**: Improving the efficiency of the universal zkVM circuit by minimizing the number of constraints and reducing the circuit depth. This can be achieved through techniques like circuit parallelization, custom gate design, and efficient memory access patterns.
2. **Compiler Optimizations**: Developing advanced compiler optimizations specifically tailored for zkVMs, such as code reordering, constant folding, and dead code elimination. These optimizations can help reduce the size and complexity of the compiled programs.
3. **Hardware Acceleration**: Exploring the use of specialized hardware accelerators, such as GPUs or FPGAs, to speed up the proving process. By offloading computationally intensive tasks to dedicated hardware, the overall performance of zkVMs can be significantly improved.
4. **Hybrid Approaches**: Investigating hybrid approaches that combine the best aspects of zkVMs and manually optimized circuits. This could involve using zkVMs for the majority of the program logic while leveraging manually optimized circuits for performance-critical sections.
5. **Improved Developer Tools**: Investing in the development of better developer tools, libraries, and frameworks that simplify the process of writing efficient zkVM programs. This can include advanced debugging tools, performance profilers, and automated optimization techniques.

By addressing these limitations and exploring potential optimizations, zkVMs have the potential to become a more practical and efficient solution for zero-knowledge computation. As research in this field progresses, we can expect to see significant advancements in the performance and usability of zkVMs, bringing us closer to realizing their full potential.

## Conclusion

zkVMs represent a promising approach to making zero-knowledge computation more accessible and developer-friendly. By emulating CPU architectures using zk circuits, zkVMs provide a universal and auditable way to execute programs while preserving the privacy and integrity of the computations.

However, the current state of zkVMs still faces challenges in terms of performance and the complexity of writing efficient circuits. Overcoming these limitations will require a concerted effort from the research community and the development of advanced optimization techniques and tools.

As we continue to explore and refine zkVM technologies, we can look forward to a future where zero-knowledge computation becomes more widely adopted and integrated into various applications, enabling new possibilities for secure and private computation.