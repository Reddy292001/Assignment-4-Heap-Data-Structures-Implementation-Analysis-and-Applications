# Assignment 4: Heap Data Structures Implementation, Analysis, and Applications

**Name:** Sakthidhar Koneru

## Overview

This repository contains my work for Assignment 4 on **heap data structures**, their implementation, analysis, and applications.

The assignment focuses on two main parts:

1. **Heapsort**
2. **Priority Queue using a Binary Heap and a Scheduler Simulation**

The goal of this assignment was not only to implement heap-based algorithms, but also to analyze their performance theoretically and empirically, and to demonstrate how heap structures can be used in practical applications such as task scheduling.

This repository includes:
- a Colab/Jupyter notebook containing the full implementation, experiments, analysis, and observations
- CSV files containing experimental and simulation results
- this README file explaining the process followed, how to run the code, and the main findings

---

## Repository Contents

```text
Assignment4_Heap_Data_Structures.ipynb
sorting_comparison_results.csv
scheduler_execution_results.csv
scheduler_summary_results.csv
README.md
```

> If your notebook file has a different name, update the filename in this README before submission.

---

## Work Completed

### Part 1: Heapsort Implementation and Analysis

For the first part of the assignment, I implemented **Heapsort** using a **binary max-heap** stored in a Python list.

The implementation includes:
- `heapify`
- `build_max_heap`
- `heapsort`

I then:
- tested the implementation for correctness
- explained the time complexity of Heapsort
- discussed why Heapsort runs in \(O(n \log n)\) in the best, average, and worst cases
- compared Heapsort empirically with **Quicksort** and **Merge Sort**

#### Input types used in the comparison
- random arrays
- already sorted arrays
- reverse-sorted arrays

---

### Part 2: Priority Queue Implementation and Applications

For the second part of the assignment, I implemented a **priority queue** using a **binary max-heap**.

The implementation includes:
- a `Task` class
- a `MaxHeapPriorityQueue` class

The priority queue supports:
- `insert(task)`
- `extract_max()`
- `increase_key(task_id, new_priority)`
- `decrease_key(task_id, new_priority)`
- `is_empty()`

I also used this priority queue in a **simple task scheduler simulation**.

The scheduler:
- inserts tasks when they arrive
- always selects the highest-priority task first
- records execution information such as:
  - start time
  - completion time
  - waiting time
  - turnaround time
  - whether the deadline was met

---

## Development Process

One of the main goals of this assignment was to show not only the final code, but also the **process followed**.

### Step 1: Implement Heapsort
I first implemented the main heap functions needed for sorting:

- `heapify`
- `build_max_heap`
- `heapsort`

While doing this, I added:
- clear **docstrings**
- inline **comments**
- helper functions for readability and correctness testing

I used a Python list to represent the heap because it is the standard and most efficient way to implement a binary heap.

### Step 2: Verify correctness of Heapsort
Before doing any analysis or runtime experiments, I tested Heapsort on:
- empty arrays
- single-element arrays
- already sorted arrays
- reverse-sorted arrays
- arrays with repeated values
- arrays with negative values

This step helped ensure that the implementation was correct before comparing it with other sorting algorithms.

### Step 3: Compare Heapsort with other sorting algorithms
After confirming correctness, I compared Heapsort with:
- Quicksort
- Merge Sort

For each input type and size, I:
1. generated the input array
2. ran all three algorithms on the same data
3. measured runtime using `time.perf_counter()`
4. repeated the measurements multiple times
5. recorded the average runtime in a CSV file

This helped me connect the empirical behavior of Heapsort with its theoretical guarantees.

### Step 4: Implement the priority queue
Next, I implemented a priority queue using a binary max-heap.

I created:
- a `Task` class to represent tasks
- a `MaxHeapPriorityQueue` class to manage tasks by priority

I also added a `position_map` dictionary so that task priorities could be updated efficiently using task IDs.

### Step 5: Verify correctness of the priority queue
Before building the scheduler simulation, I tested the priority queue for:
- task insertion
- extracting the highest-priority task
- increasing priority
- decreasing priority
- checking whether the queue is empty

This step ensured that the heap operations were working correctly.

### Step 6: Build the scheduler simulation
After the priority queue was working, I used it to simulate a simple scheduler.

I assumed that:
- each task has a task ID, priority, arrival time, deadline, and description
- each task takes **one unit of execution time**

The scheduler:
- inserts tasks into the queue when they arrive
- always executes the highest-priority available task
- records execution metrics for analysis

### Step 7: Write analysis and conclusions
Finally, I connected the experimental and simulation results back to theory.

For Heapsort, I explained:
- why it runs in \(O(n \log n)\) in all major cases
- how it compares with Quicksort and Merge Sort

For the priority queue, I explained:
- the time complexity of each heap operation
- why heaps are useful in scheduling
- how the scheduler results reflect the priority-based selection rule

---

## How to Run the Code

### Option 1: Run in Google Colab
This assignment was designed to run well in **Google Colab**.

1. Open Google Colab
2. Upload `Assignment4_Heap_Data_Structures.ipynb`
3. Run the notebook cells from top to bottom
4. The notebook will:
   - define the Heapsort implementation
   - run Heapsort correctness tests
   - compare Heapsort with Quicksort and Merge Sort
   - define the heap-based priority queue
   - run priority queue tests
   - simulate the scheduler
   - generate result tables and plots
   - save CSV files

### Option 2: Run locally with Jupyter Notebook
If you want to run it locally:

1. Make sure Python 3 is installed
2. Install the required libraries:
   ```bash
   pip install pandas matplotlib
   ```
3. Open Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. Open the notebook and run all cells

---

## Required Libraries

The notebook uses the following Python libraries:

- `time`
- `random`
- `sys`
- `pandas`
- `matplotlib`

Some of these are part of the Python standard library.  
`pandas` and `matplotlib` may need installation if running locally.

---

## Summary of Findings

### Heapsort
The Heapsort implementation worked correctly on all tested inputs.

The theoretical and empirical analysis supported the same conclusion:

- Heapsort has time complexity \(O(n \log n)\) in the best, average, and worst cases.
- Its performance remained relatively stable across random, sorted, and reverse-sorted inputs.
- Compared with deterministic Quicksort, Heapsort was more predictable on already sorted and reverse-sorted arrays.
- Merge Sort and Heapsort both showed more stable behavior than fixed-pivot Quicksort.

### Priority Queue and Scheduler
The priority queue correctly supported all required heap operations.

Main observations:
- insertion was efficient
- extracting the maximum-priority task was efficient
- increasing and decreasing priority worked correctly
- using a `position_map` improved update efficiency

In the scheduler simulation:
- tasks were inserted as they arrived
- the highest-priority task was always selected first
- high-priority tasks tended to execute earlier
- lower-priority tasks sometimes waited longer
- deadline satisfaction depended on the interaction between arrival times, priorities, and deadlines

This showed that a heap-based priority queue is a natural fit for scheduling systems.

---

## Notes on Code Quality

To avoid the issues I faced in a previous assignment, I made sure that this repository documents both the **implementation** and the **process** clearly.

I intentionally included:
- detailed **docstrings**
- inline **comments**
- markdown cells explaining the **process followed**
- short written **observations** after major outputs
- clear explanations of time complexity and design choices

This was done so that the notebook and repository would show not just the final answer, but also the reasoning and steps used to build it.

---

## Output Files

Running the notebook generates the following result files:

- `sorting_comparison_results.csv`
- `scheduler_execution_results.csv`
- `scheduler_summary_results.csv`

These files contain the measured sorting results and the scheduler simulation results used in the analysis.

---

## Design Choices

### Why a list was used for the heap
I used a Python list to represent the binary heap because:
- it is the standard representation for heaps
- it is easy to implement
- parent and child indices are easy to compute
- heap operations are efficient with this representation

### Why a max-heap was chosen
I used a **max-heap** because the scheduler was designed to always process the **highest-priority** task first.

This made the scheduler logic straightforward:
- the highest-priority task is always at the root
- `extract_max()` directly returns the next task to execute

### Why a position map was added
I added a dictionary mapping `task_id` to heap index so that:
- `increase_key`
- `decrease_key`

could update priorities efficiently without scanning the entire heap linearly.

---

## Conclusion

This assignment helped me study heaps from both a theoretical and practical perspective.

The main lessons were:

- Heapsort is a reliable sorting algorithm with \(O(n \log n)\) time complexity in all major cases.
- Heaps provide predictable performance compared with some pivot-based sorting strategies.
- A binary heap is an efficient structure for implementing a priority queue.
- Heap-based priority queues are useful in real applications such as task scheduling.
- Combining code, experiments, and analysis gives a much better understanding of how data structures behave in practice.

Overall, this assignment showed how the same heap structure can support both:
- **sorting**, through Heapsort
- **task scheduling**, through a priority queue
