# November 2024 — Beside the Point

## The puzzle
Two points, one red and one blue, are chosen uniformly and independently from the
interior of a unit square. To ten decimal places, what is the probability that there
exists a point on the side of the square closest to the blue point that is equidistant
from both the blue and the red point?

[View the original puzzle](https://www.janestreet.com/puzzles/archive/)

## My approach
I solved this analytically and finished the one intractable piece numerically.

1. **Reduced by symmetry.** The square's symmetry splits it into four equal triangular
   regions (one per closest side), each equally likely, so I worked within a single
   triangle and computed the probability there (WLOG).
2. **Set up the success condition as areas.** For a fixed blue point (x, y), the
   probability of success is governed by circle regions around the two points. I
   expressed the target probability as **A₁ + A₂ − 2A₃**, where:
   - **A₁, A₂** are the areas tied to each point individually — π(x²+y²) and
     π((x−1)²+y²) — which integrate cleanly.
   - **A₃** is the overlap (lens) between the two circles, the circle–circle
     intersection area.
3. **Did the analytic parts by hand.** Integrating A₁ + A₂ over the triangular region
   gives a clean **π/6**.
4. **Handled the overlap numerically.** A₃ is the standard two-circle lens area
   (the arccos + radical formula). Substituting the radii in terms of (x, y) made the
   double integral analytically nasty, so I evaluated the 2·A₃ integral in **MATLAB**:
   2·A₃ integral ≈ 4 × 0.0080477991899... ≈ 0.0321911967599...
5. **Combined.** P(success) = (A₁ + A₂) − 2A₃ = π/6 − 0.0321911967599... = 0.4914075788...

## Result
**Final answer: 0.4914075788**

## Files
- `solution.pdf` — my full handwritten derivation and MATLAB result
