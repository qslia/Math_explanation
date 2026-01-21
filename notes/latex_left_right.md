### What `\left` and `\right` do

In LaTeX (and in Markdown math rendered by MathJax/KaTeX),  

- **`\left` and `\right` are *not* visible symbols**.  
- They tell LaTeX: “**auto-size the delimiter (parenthesis, bracket, brace, etc.) to fit the height of what’s inside**.”

Example:

- **Without** `\left`/`\right`  
  ```tex
  \left( \frac{1}{x^2} \right)   % with
  ( \frac{1}{x^2} )             % without
  ```
  The first version will give large parentheses that stretch around the fraction;  
  the second keeps normal-sized parentheses.

They always come as a **pair**: `\left(` must match with `\right)`, `\left[ ... \right]`, etc.  
If you only need one side, you use a dot, e.g. `\left( x^2 \right.`.

### In your specific line

You have:

```tex
\ln!\left(1+\frac x2\right)
```

- **`\left(` and `\right)` are not needed here**, because `1 + x/2` is not very tall; normal parentheses are fine:
  ```tex
  \ln(1 + \tfrac{x}{2})
  ```
  or, if you like, you *can* keep auto-sizing:
  ```tex
  \ln\left(1 + \frac{x}{2}\right)
  ```
- The `!` in `\ln!` is almost certainly a typo; the usual notation is just `\ln`.

So for your formula, **you can safely remove `\left` and `\right`** unless you’re wrapping something tall (like a big fraction, matrix, or multi-line expression).