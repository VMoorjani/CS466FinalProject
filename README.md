# Hirschberg and Needleman-Wunsch Alignment Algorithms

This repository contains an implementation of the Hirschberg algorithm for global sequence alignment, as well as the Needleman-Wunsch algorithm, and tools for benchmarking their performance.

## Key Implementations

- **Hirschberg Algorithm:**  
  Uses O(n) memory while preserving O(n^2) time complexity.
  
- **Needleman-Wunsch (NW) Algorithm:**  
  NW uses O(n^2) memory. Here, we’ve replaced its direct call with a `global_align` function, which provides alignment and scoring under the same scoring scheme.
  
- **Benchmarking Scripts:**  
  Code to measure and compare the runtime and memory usage of Hirschberg vs. Needleman-Wunsch. This can be run with different sequence lengths and multiple samples per length.

## Data Generation

Synthetically generated DNA sequences are used for benchmarking. The `generate_synthetic_dna()` function can create random sequences of a specified length (defaulting to an even distribution of A, C, G, T). This allows consistent testing across varying sequence sizes.

## Running Hirschberg

```python
seq1 = "ACGTACGTAC"
seq2 = "TACGTCGT"
intermediate_data = []

aligned_seq1, aligned_seq2, score = hirschberg(seq1, seq2, intermediate_data)
print("Hirschberg Alignment:")
print(aligned_seq1)
print(aligned_seq2)
print("Score:", score)
```

## Running Needleman-Wunsch 

```python
score, alignment = global_align(seq1, seq2)
print("Global Alignment (NW):")
print(alignment)
print("Score:", score)
```

## Benchmarking

The benchmarking cell can be used to measure time and memory usage for both algorithms at various sequence lengths:

This will:
- Generate sequences of different lengths.
- Run both algorithms multiple times per length.
- Record mean, variance, time, and memory usage.
- Plot the results and print statistics

Plots include:
- Time comparison: Hirschberg vs. Needleman-Wunsch
- Memory comparison: Hirschberg vs. Needleman-Wunsch

The results help confirm theoretical expectations:
- Hirschberg uses less memory at scale.
- Needleman-Wunsch may be slightly faster for smaller problems but quickly becomes memory intensive.
