# ARM-Assembly-Merge-Sort-Algorithm
This program implements Merge Sort in ARM assembly, breaking a fixed 10 integer array into halves, sorting them separately, and merging them back into a sorted order.
# Merge Sort in ARM Assembly

## Overview
This project implements the **Merge Sort** algorithm in ARM assembly language. It sorts an array of 10 integers using a divide-and-conquer approach by recursively splitting, sorting, and merging sub-arrays.

## Features
- Splits an array into left and right halves.
- Recursively divides each half into sub-arrays.
- Sorts each sub-array using element comparison.
- Merges sorted sub-arrays back together to form the final sorted array.
- Uses memory-mapped locations to store intermediate and final results.

## Code Breakdown
### 1. **Splitting the Array**
- The array `arr` is divided into two halves:
  - `Leftarr` (first 5 elements)
  - `Rightarr` (last 5 elements)
- Each half is further split into:
  - `Sub1` and `Sub2` for left half
  - `Sub1` and `Sub2` for right half

### 2. **Sorting Sub-arrays**
- Each sub-array is loaded into registers.
- Elements are compared and sorted using conditional `CMP`, `MOVGT`, and `STR` instructions.

### 3. **Merging Sorted Sub-arrays**
- The sorted sub-arrays are merged into `Leftarr` and `Rightarr`.
- Finally, `Leftarr` and `Rightarr` are merged into `result`.

## Memory Layout
| Memory Location  | Purpose |
|------------------|---------|
| `0x60004000`    | Stack Pointer |
| `0x60000000`    | Final sorted result |
| `0x60000100`    | Left half of the array |
| `0x60001000`    | Right half of the array |
| `0x60002000`    | Sub-array 1 |
| `0x60003000`    | Sub-array 2 |

## Instructions to Run
1. Assemble the code using an ARM assembler (such as Keil, ARM GCC, or an emulator like QEMU).
2. Load the binary into memory.
3. Set `arr` with the desired input values.
4. Run the program and check the `result` memory location for the sorted output.

## Example Input & Output
### Input (`arr`):
```
8, 50, 81, 29, 4, 24, 23, 30, 1, 7
```
### Output (`result` after sorting):
```
1, 4, 7, 8, 23, 24, 29, 30, 50, 81
```

## Notes
- The sorting algorithm is optimized for 10 elements but can be modified for larger arrays.
- The stack is used to preserve register values during function calls.
- The algorithm follows the **Merge Sort** method, ensuring `O(n log n)` complexity.

## Author
This ARM assembly implementation of Merge Sort was developed for educational purposes, demonstrating low-level sorting techniques in assembly language.

