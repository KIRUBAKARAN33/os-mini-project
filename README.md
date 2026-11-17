# Parking Database Disk Scheduler – FCFS

A C program that simulates **First Come First Serve (FCFS)** disk scheduling
for a parking management system's entry/exit records.

## Introduction
A parking management system stores vehicle entry and exit records on disk.
When many records are requested at once, the operating system must decide the
order in which the disk head serves them. FCFS is the simplest policy: requests
are served in the order they arrive.

## Problem Statement
Accept the initial disk-head position and a sequence of disk requests. Process
the requests in arrival order, display the head-movement sequence, and calculate
the total head movement.

## Objectives
- Implement FCFS disk scheduling in C.
- Accept and validate the head position and requests.
- Display the head movement sequence.
- Calculate total (and average) head movement.
- Understand how disk scheduling affects performance.

## Technologies Used
| Item | Details |
|------|---------|
| Language | C |
| Compiler | GCC (MinGW-w64) |
| Editor | Visual Studio Code |
| OS | Windows 10 |
| Version Control | Git & GitHub |

## FCFS Algorithm Explanation
FCFS serves disk requests strictly in arrival order. No sorting or
reordering is done. It is fair and easy to implement, but may cause long head
movements when requests are scattered across the disk.

Head movement for each step = |next request − current head position|

## Step-by-Step Algorithm
1. Start.
2. Read the initial head position.
3. Read the number of requests `n`.
4. Read the `n` requests into an array.
5. Set `total = 0` and `current = head`.
6. For each request in the original order:
   a. `distance = |request − current|`
   b. `total = total + distance`
   c. `current = request`
7. Display the movement sequence and `total`.
8. Stop.

## Source Code Explanation
| Part | Purpose |
|------|---------|
| `#define` constants | Set the maximum requests (100) and cylinder range (0–199). |
| `clearInputBuffer()` | Discards leftover characters after bad input. |
| `readInt()` | Reads an integer, rejects letters and out-of-range values, and repeats until valid. |
| `main()` | Takes input, prints the sequence, loops through requests in order, and sums distances. |
| `abs()` | Gives the absolute distance between two cylinders. |

## Sample Input
```
Initial Head Position : 50
Number of Requests : 7
Requests : 82 170 43 140 24 16 190
```

## Sample Output
```
Head Movement Sequence:
50 -> 82 -> 170 -> 43 -> 140 -> 24 -> 16 -> 190

Total Head Movement : 642 cylinders
Average Head Movement : 91.71 cylinders per request
```
See `output.txt` for the full output.

## Total Head Movement Calculation
| Step | From | To | Calculation | Movement |
|------|------|----|-------------|----------|
| 1 | 50 | 82 | \|82 − 50\| | 32 |
| 2 | 82 | 170 | \|170 − 82\| | 88 |
| 3 | 170 | 43 | \|43 − 170\| | 127 |
| 4 | 43 | 140 | \|140 − 43\| | 97 |
| 5 | 140 | 24 | \|24 − 140\| | 116 |
| 6 | 24 | 16 | \|16 − 24\| | 8 |
| 7 | 16 | 190 | \|190 − 16\| | 174 |
| | | | **Total** | **642** |

## Advantages
- Very simple to understand and implement.
- Fair: no request is starved.
- Preserves arrival order.
- Low overhead.

## Applications
- Teaching disk scheduling in OS courses.
- Parking, library, and billing record systems with light load.
- Baseline for comparing SSTF, SCAN, C-SCAN, and LOOK.
- Simple storage systems with sequential access patterns.

## How to Compile and Run
```
gcc parking_fcfs.c -o parking_fcfs
parking_fcfs
```

## Conclusion
The project shows that FCFS is fair and simple, but not always efficient. For
the sample data it produces a total head movement of 642 cylinders. It provides
a base for comparing more advanced disk scheduling algorithms.

## Author
KIRUBAKARAN R – SRM TRP engineering college -CSE /814725104075
