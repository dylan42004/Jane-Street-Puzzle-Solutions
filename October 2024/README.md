# October 2024 — Knight Moves 6

## The puzzle
A 6×6 board is partitioned into three regions labeled A, B, and C, each assigned a
distinct positive integer. A knight starts in a corner with a score equal to its
starting square's value. On each move: if it moves to a square in the **same** region,
the square's value is **added** to the score; if to a **different** region, the score
is **multiplied** by that value.

The task: choose values for A, B, and C — minimizing A + B + C — such that there
exists a knight's path scoring exactly **2024** from a1 to f6, *and* a second path
scoring exactly 2024 from a6 to f1. Submit both paths.

[View the original puzzle](https://www.janestreet.com/puzzles/archive/)

## My approach
I solved it programmatically (Python) with a search over both the values and the paths:

1. **Brute-forced the value assignment.** Looped over distinct candidate values for
   A, B, C, pruning any combination whose sum already exceeded the best sum found —
   so the search converges quickly toward the minimal A + B + C.
2. **Searched paths with a knight-move BFS.** For each value set, ran a breadth-first
   search over legal knight moves, tracking the running score and pruning any path
   whose score exceeded 2024 (scores are non-decreasing, so overshooting is terminal).
3. **Constrained the endpoint.** Since both target corners (f6, f1) sit in region C,
   I anchored the search on the C-region squares a knight can reach the corner from,
   which sharply prunes the path space.
4. **Required both trips simultaneously.** A value set only counts if it admits a
   valid 2024-scoring path for *both* a1→f6 and a6→f1.

## Result
Minimal sum **A + B + C = 6**, achieved by **A = 1, B = 3, C = 2**.

| Trip | Path (scores exactly 2024) |
|------|----------------------------|
| a1 → f6 | a1, b3, c1, d3, e5, c4, d6, e4, f2, d1, b2, a4, b6, d5, f6 |
| a6 → f1 | a6, b4, c2, d4, e6, c5, b3, c1, d3, e1, f3, d2, c4, e3, f1 |

Both verified: every step is a legal knight move and each path totals exactly 2024.
This matches the official minimal answer (sum 6), which (1, 3, 2) achieves.

## Files
- `solution.ipynb` — the solver (value search + knight-move BFS), with output
