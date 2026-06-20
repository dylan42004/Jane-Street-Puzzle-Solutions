# March 2025 — Hall of Mirrors 3

## The puzzle
A 10×10 grid is surrounded by lasers pointing into the field from the perimeter,
some labeled with numbers. The goal is to place diagonal mirrors in some cells so
that, for each labeled laser, the product of its path's segment lengths equals the
clue. Mirrors can't be placed in orthogonally adjacent cells.

Once the grid is solved, you determine the missing perimeter clues, sum the clues
on each of the four sides, and multiply those four sums together for the final answer.

[View the original puzzle](https://www.janestreet.com/puzzles/archive/)

## My approach
I solved this by hand, using constraint-driven trial and error rather than a
program:

1. **Started with the most constrained clues.** Some lasers had only a few factorizations
   into valid segment lengths given the 10×10 bounds, so those had very few possible
   mirror placements. I locked those in first.
2. **Propagated constraints.** Each placed mirror redirects a laser and limits where
   adjacent mirrors can go (no orthogonally adjacent mirrors), so each fixed cell
   narrowed the options for neighboring paths.
3. **Filled the rest by trial and error**, backtracking whenever a placement made a
   clue's product impossible.

## Result
With the grid solved, I read off the missing perimeter clues and summed each side:

| Side | Sum |
|------|-----|
| Left | 2,251 |
| Top | 480 |
| Right | 166 |
| Bottom | 3,356 |

**Final answer:** 2,251 × 480 × 166 × 3,356 = **601,931,086,080**

## Files
- `solution.pdf` — my handwritten grid solution and side-sum calculations
