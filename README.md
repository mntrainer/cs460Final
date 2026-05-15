# The Torchbearer

**Student Name:** ______Tianna Nelson_____________________
**Student ID:** ______130894618_____________________
**Course:** CS 460 – Algorithms | Spring 2026

> This README is your project documentation. Write it the way a developer would document
> their design decisions , bullet points, brief justifications, and concrete examples where
> required. You are not writing an essay. You are explaining what you built and why you built
> it that way. Delete all blockquotes like this one before submitting.

---

## Part 1: Problem Analysis

> Document why this problem is not just a shortest-path problem. Three bullet points, one
> per question. Each bullet should be 1-2 sentences max.

- **Why a single shortest-path run from S is not enough:**
  shortest path means the shortest path from point a to point b, but in this situation 
  a set number of nodes must be visited so the shortest path run wouldn't work cause it might exclude the required nodes in the set.

- **What decision remains after all inter-location costs are known:**
  choosing which path from S to the required nodes in the set would be most optimal and the least amount of weight.

- **Why this requires a search over orders (one sentence):**
  Because the order of how the required nodes are visited may amount to a different weight depending on the paths that taken for example a node could have 2 possible paths to different nodes and depending on which node the path took previously the weights could be different, amounting to a different total cost.

---

## Part 2: Precomputation Design

### Part 2a: Source Selection

> List the source node types as a bullet list. For each, one-line reason.

Source nodes are nodes that start and connect to another node

| Source Node Type | Why it is a source |
|---               |---                 |
| Entrance Node S  | This is the source node to the rest of the path |
| Relic Node       | These are source nodes to parts parts of the path |
| Exit node        | Shortest path to the exit might be needed |

### Part 2b: Distance Storage

> Fill in the table. No prose required.

| Property                    | Your answer |
|---       |---               |
| Data structure name         | Hash map    |
| What the keys represent     | The keys should be the letters for the nodes |
| What the values represent   | The current least weight known from the start to that node |
| Lookup time complexity      | O(1)|
| Why O(1) lookup is possible | because the letters for the nodes would be unique and known|

### Part 2c: Precomputation Complexity

> State the total complexity and show the arithmetic. Two to three lines max.

- **Number of Dijkstra runs:** 
  2 + R number of relics would be the run 2 for entry and exit and R for the amount of relics needed
- **Cost per run:**
  Currently my cost per run for dijkstra is n^2 + n
- **Total complexity:** 
  O((R + 2)(N^2 + N))
- **Justification (one line):** _your answer_

---

## Part 3: Algorithm Correctness

> Document your understanding of why Dijkstra produces correct distances.
> Bullet points and short sentences throughout. No paragraphs.

### Part 3a: What the Invariant Means

> Two bullets: one for finalized nodes, one for non-finalized nodes.
> Do not copy the invariant text from the spec.

- **For nodes already finalized (in S):**
  The stored distance is the shortest possible distance from the source

- **For nodes not yet finalized (not in S):**
  There are other paths can be taken that could also have a shorter distance than the current distance

### Part 3b: Why Each Phase Holds

> One to two bullets per phase. Maintenance must mention nonnegative edge weights.

- **Initialization : why the invariant holds before iteration 1:**
  The source will be 0 before initialization because it is the starting node, all other paths will start at infinity because they haven't been explored yet

- **Maintenance : why finalizing the min-dist node is always correct:**
  The algorithm will choose the node with the smallest known distance next, since the weights cannot be negative no other path chosen to that node will be more than the current min distance.

- **Termination : what the invariant guarantees when the algorithm ends:**
  When the algorithm ends, every node that was able to be reached with the minimum cost has been reached which terminates the algorithm.

### Part 3c: Why This Matters for the Route Planner

> One sentence connecting correct distances to correct routing decisions.

The shortest distances are needed so minimum costs to all required nodes are compared and the cheapest valid route can be determined.

---

## Part 4: Search Design

### Why Greedy Fails

> State the failure mode. Then give a concrete counter-example using specific node names
> or costs (you may use the illustration example from the spec). Three to five bullets.

- **The failure mode:** The greedy will the local optimum but the total route would not result in the global optimum. 
- **Counter-example setup:** 
  S : (['E', 1], ['G', 2])
  E: (['G', 100], ['T', 2])
  G: (['E', 1], ['T', 1])
  T: ([])
- **What greedy picks:** Greedy will pick S->E then E->G then G->T (102)
- **What optimal picks:** S->G then G->E then E->T which results in (5)
- **Why greedy loses:** greedy will lose here since choosing the local optimal route created a more expensive route in the future

### What the Algorithm Must Explore

> One bullet. Must use the word "order."

- The algorithm must consider the relic choice order since choosing the closest cheapest relic is not always the best option.

---

## Part 5: State and Search Space

### Part 5a: State Representation

> Document the three components of your search state as a table.
> Variable names here must match exactly what you use in torchbearer.py.

| Component | Variable name in code | Data type | Description |
|---        |---                    |---        |---          |
| Current location | current_loc    | node      | current route end location |
| Relics already collected | relics_visited_order    | list[node] | The relics visited|
| Fuel cost so far |   cost_so_far. | float     |   total fuel cost by the route |

### Part 5b: Data Structure for Visited Relics

> Fill in the table.

| Property | Your answer |
|---|---|
| Data structure chosen | |
| Operation: check if relic already collected | Time complexity: |
| Operation: mark a relic as collected | Time complexity: |
| Operation: unmark a relic (backtrack) | Time complexity: |
| Why this structure fits | |

### Part 5c: Worst-Case Search Space

> Two bullets.

- **Worst-case number of orders considered:** _Your answer (in terms of k)._
- **Why:** _One-line justification._

---

## Part 6: Pruning

### Part 6a: Best-So-Far Tracking

> Three bullets.

- **What is tracked:** _Your answer here._
- **When it is used:** _Your answer here._
- **What it allows the algorithm to skip:** _Your answer here._

### Part 6b: Lower Bound Estimation

> Three bullets.

- **What information is available at the current state:** _Your answer here._
- **What the lower bound accounts for:** _Your answer here._
- **Why it never overestimates:** _Your answer here._

### Part 6c: Pruning Correctness

> One to two bullets. Explain why pruning is safe.

- _Your answer here._

---

## References

> Bullet list. If none beyond lecture notes, write that.

- _Your references here._
