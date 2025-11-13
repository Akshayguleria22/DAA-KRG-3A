# DAA-KRG-3A — Algorithms Experiments (C++)

A collection of 10 small, interactive C++ programs for classic data structures and algorithms, suitable for Design and Analysis of Algorithms (DAA) lab work.

## Overview
Each `ExperimentN.cpp` is a standalone console program. Build them individually and run from the terminal. Most programs prompt for input at runtime.

## Repository Layout
- `Experiment1.cpp` — Stack (array-based) with push/pop/traverse and overflow/underflow helpers
- `Experiment2.cpp` — Fast exponentiation `x^y` in O(log n)
- `Experiment3.cpp` — Frequency of array elements in O(n) using `unordered_map`
- `Experiment4.cpp` — Doubly Linked List: insert at begin/end, delete at begin/end, display
- `Experiment5.cpp` — Quick Sort
- `Experiment6.cpp` — Subset Sum (DP): check if any subset sums to target
- `Experiment7.cpp` — 0-1 Knapsack (note: current code matches Subset Sum check; see notes)
- `Experiment8.cpp` — Dijkstra’s shortest path (undirected; adjust for directed as noted in code)
- `Experiment9.cpp` — Naive string search
- `Experiment10.cpp` — KMP string matching

## Prerequisites
- A C++ compiler (C++17 or newer). On Windows, MinGW-w64 `g++` is common.
- Terminal: Windows PowerShell.

Verify your compiler:
```powershell
g++ --version
```

## Build and Run (Windows / PowerShell)
Build any experiment into an EXE and run it:
```powershell
# Example: Experiment 5 (Quick Sort)
g++ -std=gnu++17 Experiment5.cpp -o Experiment5.exe
./Experiment5.exe
```

Recommended flags: `-std=gnu++17` (or `-std=c++17`).

### Compile All (quick loop)
This compiles every `.cpp` file in the folder into a matching `.exe`:
```powershell
Get-ChildItem *.cpp | ForEach-Object {
  $out = "$($_.BaseName).exe";
  g++ -std=gnu++17 $_.Name -o $out
}
```
Run any program with:
```powershell
./ExperimentN.exe
```

## Experiments Summary
| No. | File              | Topic / Algorithm                                  | Notes |
|-----|-------------------|-----------------------------------------------------|-------|
| 1   | Experiment1.cpp   | Stack (array-based)                                 | Push, Pop, Traverse, Overflow/Underflow helpers |
| 2   | Experiment2.cpp   | Fast Power (Exponentiation by Squaring)             | O(log n) time |
| 3   | Experiment3.cpp   | Frequency Count (Hash Map)                          | Preserves first-seen order for display |
| 4   | Experiment4.cpp   | Doubly Linked List                                   | Insert/Delete at both ends, Display |
| 5   | Experiment5.cpp   | Quick Sort                                           | In-place, Lomuto-style partition on last pivot |
| 6   | Experiment6.cpp   | Subset Sum (DP)                                      | Boolean DP table `n x target` |
| 7   | Experiment7.cpp   | 0-1 Knapsack (placeholder)                           | Currently implements Subset Sum check; see below |
| 8   | Experiment8.cpp   | Dijkstra’s Shortest Path                             | Uses min-heap; undirected; remove 1 line for directed |
| 9   | Experiment9.cpp   | Naive String Search                                  | Reports all starting indices |
| 10  | Experiment10.cpp  | KMP String Matching                                  | LPS preprocessing + linear-time search |

## Usage Examples
- Quick Sort:
  1) Build and run `Experiment5.exe`
  2) Enter `n` and the list of `n` integers when prompted
  3) View sorted output

- Subset Sum (Experiment 6):
  1) Build and run `Experiment6.exe`
  2) Enter `n`, then `n` integers, then the target sum
  3) Program prints whether a subset with the target sum exists

- String Matching:
  - Naive (`Experiment9.exe`) and KMP (`Experiment10.exe`) both prompt for text and pattern and print all match positions (0-based indices).

## Notes and Tips
- Input with `getline`: Experiments 9 and 10 use `getline`. If you adapt these programs to mix `cin >>` and `getline`, add `cin.ignore(numeric_limits<streamsize>::max(), '\n');` before the first `getline` after formatted extraction to clear the buffer.
- Directed vs Undirected (Dijkstra): `Experiment8.cpp` currently adds edges both ways. Remove the second `push_back` to treat the graph as directed, as commented in the file.
- Experiment 7 (0-1 Knapsack): The file header says 0-1 Knapsack, but the current implementation matches a Subset Sum check (boolean feasibility). To extend to true 0-1 Knapsack, replace it with a value-maximizing DP over weights.

## Troubleshooting
- "command not found" or `g++` missing: Install MinGW-w64 and ensure `g++` is on your PATH.
- Build errors: Use `-std=gnu++17` (or `-std=c++17`). Ensure you run the command in the folder containing the `.cpp` files.

---
Happy coding! If you want, I can also add a simple `build.ps1` script to compile all experiments into a `bin/` folder. 
