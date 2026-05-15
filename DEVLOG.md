# Development Log – The Torchbearer

**Student Name:** ___Tianna Nelson________________________
**Student ID:** ____130894618_______________________

> Instructions: Write at least four dated entries. Required entry types are marked below.
> Two to five sentences per entry is sufficient. Write entries as you go, not all in one
> sitting. Graders check that entries reflect genuine work across multiple sessions.
> Delete all blockquotes before submitting.

---

## Entry 1 – [5/13/26 3pm]: Initial Plan

> Required. Write this before writing any code. Describe your plan: what you will
> implement first, what parts you expect to be difficult, and how you plan to test.

My plan is to first figure out dikstra's algorithm for this 
problem and work out solving all the questions I have for the problem and fully understanding it
I will work out each part incrementally like for dikstra's I need to understand the input
How to process the input, how to keep track of visited nodes, how to update the table etc
I also feel like the precompute distances part would be difficult but once dijkstra's is implemented it should be easier
I forgot to write this devlog entry oops

---

## Entry 2 – [5/13/26 7pm]: [Short description]

> Required. At least one entry must describe a bug, wrong assumption, or design change
> you encountered. Describe what went wrong and how you resolved it.

I didn't realize there needed to be a visited set for dijkstra's and that the 
current node needed to be updated so I only had 1 for loop for the actual processing part for a while and didn't understand why the distance set wasn't updating properly. My dijkstra algorithm is not optimized with n^2 time so I will probably attempt to optimize it, I see heapq is imported which is probably what I need to use.

---

## Entry 3 – [5/14/26 3pm - 7pm]: [Short description]

Finished part 3 and optimized dijkstra's algorithm
Finished doing part 4 of the final

For part 5 and 6 I did some research and I plan on implementing backtracking and pruning along with dijkstra to make this work. I would probably create the skeleton first with the optimal function and then implement the recursion that is needed for backtracking, Then I would implement pruning last.

---

## Entry 4 – [5/14/26 9 pm]: Post-Implementation Reflection

> Required. Written after your implementation is complete. Describe what you would
> change or improve given more time.


My pruning is very short I don't really optimize it at all so I would probably implement something related to checking for current expensive branches and not possible expensive branches
---

## Final Entry – [Date]: Time Estimate

> Required. Estimate minutes spent per part. Honesty is expected; accuracy is not graded.

| Part | Estimated Hours |
|---|---|
| Part 1: Problem Analysis | 30 minutes |
| Part 2: Precomputation Design | 3 hours |
| Part 3: Algorithm Correctness | 1 hour|
| Part 4: Search Design | 1 hour |
| Part 5: State and Search Space | 3 hours (planning)|
| Part 6: Pruning | 10 minutes|
| Part 7: Implementation | 2 hours |
| README and DEVLOG writing | 1 hour total|
| **Total** | 11 hours 40 minutes |
