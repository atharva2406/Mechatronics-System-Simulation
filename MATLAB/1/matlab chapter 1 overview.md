# 🚀 Last-Minute Calculus & Programming Review Script

## 📊 Section 1: Polyfit vs. Polyval (Curve Fitting)
* **The Rule:** **`polyfit` creates the rule; `polyval` evaluates the rule.**
* **Workflow:**
  1. **Create the Rule:** `a = polyfit(x, y, degree)`
     * Takes your known data (`x` and `y`).
     * Calculates the polynomial coefficients (the mathematical rule).
     * *Correction:* You **must** specify the `degree` (e.g., `1` for a straight line, `2` for a parabola).
  2. **Use the Rule:** `new_y = polyval(a, b)`
     * Takes your rule `a`.
     * Plugs in new input values `b` to predict or calculate the new outputs.

---

## 📐 Section 2: Element-by-Element Operations (`.*`)
* **The Rule:** **When multiplying arrays element-by-element, you MUST use the dot operator `.*`**.
* **The Setup:** If `x = -2:0.1:2`, it is a vector (an array of numbers). 
* **The Math:** To define a function or multiply equations, you must process each element individually.
  * ❌ **Wrong:** `y = x * 2` or `z = x * y` (This triggers matrix multiplication and crashes).
  * ✅ **Right:** `y = x + 2` (Adding a scalar to a vector is fine).
  * ✅ **Right:** `z = x .* y` (Multiplies each individual index of `x` by each index of `y`).
  * ✅ **Right:** `y = x.^2` (Squaring every individual number in the array requires `.^`).

---

## 🖼️ Section 3: Subplots Layout
* **The Rule:** **`subplot(rows, cols, index)`**
* **The Logic:** Avoid using `x` and `y` here so you don't confuse them with your graph axes.
  * `rows`: Total number of horizontal rows of plots.
  * `cols`: Total number of vertical columns of plots.
  * `index`: The active window you are currently drawing on (numbered left-to-right, top-to-bottom).
* **Example for 2 stacked graphs:**
  * Top graph: `subplot(2, 1, 1); plot(x, y);`
  * Bottom graph: `subplot(2, 1, 2); plot(x, z);`

---

## 🧮 Section 4: Calculus Workflow Roadmap
Always start with your original equation defined symbolically: `syms x; y = f(x);`

### 1. Finding Roots (x-Intercepts)
* **Definition:** Where the graph crosses the x-axis.
* **Calculus Step:** Set the **original equation** to zero.
* **Code:** `roots_x = solve(y == 0, x)`

### 2. Finding Turning Points (Local Maxima / Minima)
* **Definition:** Where the graph reaches a peak or a valley and changes direction.
* **Calculus Step 1:** Find the **first derivative** (y').
* **Calculus Step 2:** Set the first derivative to zero to find the x-coordinates: `tp_x = solve(diff(y) == 0, x)`
* **Calculus Step 3:** Plug `tp_x` back into the **original** equation `y` to get the y-coordinates.
* *Bonus Exam Check:* Plug `tp_x` into the *second derivative* (y''). If y'' > 0 it’s a minimum; if y'' < 0 it’s a maximum.

### 3. Finding Inflection Points
* **Definition:** Where the curve changes its bending direction (concavity changes from frowning to smiling, or vice versa). 
* **Calculus Step 1:** Find the **second derivative** (y'').
* **Calculus Step 2:** Set the second derivative to zero to find the x-coordinates: `inf_x = solve(diff(y, 2) == 0, x)`
* **Calculus Step 3:** Plug `inf_x` back into the **original** equation `y` to get the y-coordinates.

---

### Summary Cheat Sheet Table

| Objective | Target Derivative | Code Equation to Solve | Final Step for Y-Value |
| :--- | :--- | :--- | :--- |
| **Roots** | Original Function (y) | `solve(y == 0, x)` | Already solved (y=0) |
| **Turning Points** | First Derivative (y') | `solve(diff(y) == 0, x)` | Substitute x back into original y |
| **Inflection Points**| Second Derivative (y'') | `solve(diff(y, 2) == 0, x)`| Substitute x back into original y |