The formula in the image is for the **expected value** (or mean) of a discrete random variable (X).

[
E[X] = \sum x_i , P(x_i)
]

### Breaking it down:

1. **Random Variable (X)**

   * A random variable is a variable whose possible values are outcomes of a random process.
   * Example: Rolling a die → (X) can take values (1, 2, 3, 4, 5, 6).

2. **Possible Values (x_i)**

   * These are the actual outcomes the variable can take.
   * Example: For a die, (x_i \in {1, 2, 3, 4, 5, 6}).

3. **Probability (P(x_i))**

   * This is the probability that (X) takes the value (x_i).
   * Example: For a fair die, (P(x_i) = \frac{1}{6}) for each (i).

4. **Multiplying (x_i \cdot P(x_i))**

   * You weigh each possible value by how likely it is.

5. **Summation (\sum)**

   * You add up all these weighted values.

### Intuition:

The expected value is like the "long-run average" if you repeated the experiment many times.

**Example (Fair die):**
[
E[X] = \sum_{i=1}^6 x_i \cdot P(x_i) = 1 \cdot \tfrac{1}{6} + 2 \cdot \tfrac{1}{6} + \dots + 6 \cdot \tfrac{1}{6}
]
[
= \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = 3.5
]

So, if you roll a die many times, the **average outcome tends toward 3.5**, even though you’ll never actually roll a 3.5.

---

👉 Do you want me to also explain how this works for **continuous random variables** (where we use an integral instead of a sum)?
