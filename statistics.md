## The Hypergeometric Distribution

The hypergeometric distribution is a **probability distribution** that describes the number of successes in a sequence of draws **without replacement** from a finite population.

## Key Characteristics

- **Without replacement** - Unlike binomial distribution (which is with replacement)
- **Finite population** - The total population size is fixed
- **Two categories** - Each item is either a "success" or "failure"
- **Dependent trials** - Probabilities change after each draw

## Parameters

| Parameter | Description |
|-----------|-------------|
| **N** | Population size (total items) |
| **K** | Number of success states in the population |
| **n** | Number of draws (sample size) |
| **k** | Number of observed successes (random variable) |

## Probability Mass Function (PMF)

The probability of getting exactly **k** successes in **n** draws is:

\[
P(X = k) = \frac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}
\]

Where:
- \(\binom{a}{b}\) is the binomial coefficient ("a choose b")
- \(max(0, n - (N - K)) \leq k \leq min(n, K)\)

## Key Properties

### Mean (Expected Value):
\[
E[X] = n \cdot \frac{K}{N}
\]

### Variance:
\[
Var(X) = n \cdot \frac{K}{N} \cdot \frac{N-K}{N} \cdot \frac{N-n}{N-1}
\]

The last factor \(\frac{N-n}{N-1}\) is the **finite population correction factor**.

## Comparison with Binomial Distribution

| Feature | Hypergeometric | Binomial |
|---------|----------------|---------|
| Sampling | Without replacement | With replacement |
| Independence | Dependent trials | Independent trials |
| Population | Finite | Infinite or large |
| Probability | Changes each draw | Constant |

As \(N \to \infty\), the hypergeometric distribution **approaches** the binomial distribution with \(p = K/N\).

## Examples

### Example 1: Card Drawing
Draw 5 cards from a standard 52-card deck. What's the probability of getting exactly 2 aces?

- \(N = 52\) (total cards)
- \(K = 4\) (aces in deck)
- \(n = 5\) (cards drawn)
- \(k = 2\) (aces desired)

\[
P(X = 2) = \frac{\binom{4}{2} \binom{48}{3}}{\binom{52}{5}} \approx 0.0399
\]

### Example 2: Quality Control
A batch of 100 items contains 10 defective items. If you randomly select 15 items for inspection, what's the probability of finding exactly 2 defective items?

- \(N = 100\)
- \(K = 10\) (defective items)
- \(n = 15\)
- \(k = 2\)

\[
P(X = 2) = \frac{\binom{10}{2} \binom{90}{13}}{\binom{100}{15}} \approx 0.318
\]

## Applications

1. **Quality Control** - Sampling products without replacement
2. **Lottery/Card Games** - Probability calculations
3. **Biology** - Capture-recapture studies
4. **Survey Sampling** - When sampling without replacement from a finite population
5. **Genetics** - Analyzing gene frequencies
6. **Election Polling** - Predicting outcomes from samples

## In Programming

### JavaScript Implementation:
```javascript
function hypergeometricProbability(N, K, n, k) {
    function binomialCoefficient(n, k) {
        if (k < 0 || k > n) return 0;
        let result = 1;
        for (let i = 1; i <= k; i++) {
            result = result * (n - i + 1) / i;
        }
        return result;
    }
    
    return (binomialCoefficient(K, k) * binomialCoefficient(N - K, n - k)) / binomialCoefficient(N, n);
}
```

### Python Implementation (using scipy):
```python
from scipy.stats import hypergeom

# P(X = k)
prob = hypergeom.pmf(k, N, K, n)

# Expected value
mean = hypergeom.mean(N, K, n)

# Variance
variance = hypergeom.var(N, K, n)
```

## Relationship to Other Distributions

- **Approaches Binomial** as \(N \to \infty\)
- **Approaches Poisson** when \(K/N\) is small and \(n\) is large
- **Special case of Multivariate Hypergeometric** when there are more than 2 categories

The hypergeometric distribution is fundamental in probability theory and statistics, especially in fields where sampling without replacement from finite populations is common.
----

This text is introducing the **probability mass function (PMF)** for a discrete random variable, though they're calling it a "probability density function" (pdf) — which is technically the term for continuous variables.

Let me break this down piece by piece:

---

## What is a Random Variable?

A **random variable** \( X \) is a function that maps outcomes from a sample space \( S \) to numbers:

\[
X: S \to \mathbb{R}
\]

For example:
- \( S = \{\text{Heads}, \text{Tails}\} \)
- \( X(\text{Heads}) = 1 \), \( X(\text{Tails}) = 0 \)

---

## What is \( p_X(k) \)?

The notation \( p_X(k) \) represents the **probability that the random variable \( X \) equals the specific value \( k \)**.

Formally:

\[
p_X(k) = P(\{s \in S \mid X(s) = k\})
\]

### Breaking this down:

| Symbol | Meaning |
|--------|---------|
| \( S \) | The sample space (all possible outcomes) |
| \( s \) | A single outcome in the sample space |
| \( X(s) \) | The value of the random variable for outcome \( s \) |
| \( \{s \in S \mid X(s) = k\} \) | The set of all outcomes where \( X(s) \) equals \( k \) |
| \( P(\cdots) \) | The probability of that set of outcomes |

---

## A Concrete Example

Let's say you roll one fair die. Define:
- \( X \) = the number showing on the die

Then:
- \( S = \{1, 2, 3, 4, 5, 6\} \)
- \( X(s) = s \) (the identity function)

For \( k = 3 \):

\[
p_X(3) = P(\{s \in S \mid X(s) = 3\}) = P(\{3\}) = \frac{1}{6}
\]

For \( k = 7 \) (not in the range):
\[
p_X(7) = 0
\]

---

## The Simplified Notation

The text says:

> For notational simplicity, we will usually delete all references to \( s \) and \( S \) and write \( p_X(k) = P(X = k) \)

This means:
- Instead of writing the full set-builder notation \( P(\{s \in S \mid X(s) = k\}) \)
- We simply write \( P(X = k) \)

This is standard shorthand. It's easier to read and still clearly means "the probability that the random variable \( X \) takes the value \( k \)".

---

## Key Properties of a PMF

For a discrete random variable:

1. **Non-negativity**: \( p_X(k) \geq 0 \) for all \( k \)
2. **Sum to one**: \( \sum_{k} p_X(k) = 1 \) (sum over all possible values of \( X \))
3. **Zero outside range**: \( p_X(k) = 0 \) if \( k \) is not a possible value of \( X \)

---

## Visual Example: Two Dice Sum

Let \( X \) = sum of two fair dice:

| k | Possible outcomes | \( p_X(k) = P(X = k) \) |
|---|-------------------|------------------------|
| 2 | (1,1) | 1/36 |
| 3 | (1,2), (2,1) | 2/36 |
| 4 | (1,3), (2,2), (3,1) | 3/36 |
| ... | ... | ... |
| 7 | (1,6), (2,5), (3,4), (4,3), (5,2), (6,1) | 6/36 |
| ... | ... | ... |
| 12 | (6,6) | 1/36 |

Here, \( p_X(7) = 6/36 \) is the probability mass at \( k = 7 \).

---

## Why This Matters

The probability mass function completely describes the distribution of a discrete random variable. Once you know \( p_X(k) \) for all \( k \), you can calculate:
- Expected value: \( E[X] = \sum_k k \cdot p_X(k) \)
- Variance: \( \text{Var}(X) = \sum_k (k - E[X])^2 \cdot p_X(k) \)
- Probabilities of events: \( P(X \in A) = \sum_{k \in A} p_X(k) \)

So the PMF is the fundamental building block for working with discrete random variables.
---


## What is \( \sum_k \) ?

The notation \( \sum_k \) means **sum over all possible values of \( k \)** (the index variable). It's a shorthand for writing out a sum without explicitly listing every term.

## The Full Form

When you see:

\[
\sum_k p_X(k)
\]

It means:

\[
\sum_{\text{all } k \text{ in the range of } X} p_X(k)
\]

Or more explicitly:

\[
\sum_{k \in \text{Range}(X)} p_X(k)
\]

Where \(\text{Range}(X)\) is the set of all values the random variable \(X\) can take.

## Concrete Examples

### Example 1: Rolling a Die

Let \(X\) = number showing on a fair die.

Possible values: \( \{1, 2, 3, 4, 5, 6\} \)

\[
\sum_k p_X(k) = \sum_{k=1}^{6} \frac{1}{6} = \frac{1}{6} + \frac{1}{6} + \frac{1}{6} + \frac{1}{6} + \frac{1}{6} + \frac{1}{6} = 1
\]

### Example 2: Sum of Two Dice

Let \(X\) = sum of two dice.

Possible values: \( \{2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12\} \)

\[
\sum_k p_X(k) = p_X(2) + p_X(3) + p_X(4) + \cdots + p_X(12)
\]

\[
= \frac{1}{36} + \frac{2}{36} + \frac{3}{36} + \frac{4}{36} + \frac{5}{36} + \frac{6}{36} + \frac{5}{36} + \frac{4}{36} + \frac{3}{36} + \frac{2}{36} + \frac{1}{36} = 1
\]

### Example 3: Expected Value

The expected value formula:

\[
E[X] = \sum_k k \cdot p_X(k)
\]

For a fair die:

\[
E[X] = \sum_{k=1}^{6} k \cdot \frac{1}{6} = \frac{1}{6} + \frac{2}{6} + \frac{3}{6} + \frac{4}{6} + \frac{5}{6} + \frac{6}{6} = 3.5
\]

## Different Ways to Write the Same Thing

| Notation | Meaning |
|----------|---------|
| \(\sum_k\) | Sum over all values of \(k\) |
| \(\sum_{k} p_X(k)\) | Sum over all possible \(k\) |
| \(\sum_{k \in \text{Range}(X)}\) | Explicitly says sum over the range |
| \(\sum_{k=-\infty}^{\infty}\) | Sum over all integers (most values are zero) |

## Why Use This Shorthand?

1. **Simplicity** - Avoids writing the range explicitly every time
2. **Generality** - Works regardless of what the specific values are
3. **Flexibility** - Can be used with \( \sum_k \), \( \sum_x \), \( \sum_i \), etc.

## Common Uses in Probability

### 1. Sum of probabilities equals 1:
\[
\sum_k p_X(k) = 1
\]

### 2. Expected value:
\[
E[X] = \sum_k k \cdot p_X(k)
\]

### 3. Variance:
\[
\text{Var}(X) = \sum_k (k - \mu)^2 \cdot p_X(k)
\]

### 4. Probability of an event:
\[
P(X \in A) = \sum_{k \in A} p_X(k)
\]

## In Programming Terms

If you were to implement this in code:

```python
# ∑k p_X(k) for a die
probabilities = [1/6, 1/6, 1/6, 1/6, 1/6, 1/6]
total = sum(probabilities)  # 1.0

# Expected value E[X] = ∑ k·p_X(k)
values = [1, 2, 3, 4, 5, 6]
expected = sum(k * p for k, p in zip(values, probabilities))  # 3.5
```

The \(\sum_k\) notation is just a compact mathematical way to say "add up all these terms over every possible value of \(k\)".

---

This is the **probability mass function (PMF) of the Binomial Distribution**! Let me explain it in detail.

## The Formula

\[
P(X = k) = p_X(k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, 2, \ldots, n
\]

## What It Represents

This formula gives the probability of getting exactly **k successes** in **n independent trials**, where:
- Each trial has only two outcomes: success or failure
- The probability of success is **p** (same for every trial)
- The probability of failure is **(1-p)**

## Breaking Down Each Component

### 1. \(\binom{n}{k}\) — The Binomial Coefficient

\[
\binom{n}{k} = \frac{n!}{k!(n-k)!}
\]

This counts the **number of ways** to choose which k trials out of n are successes.

**Example:** For n = 3 trials, getting exactly k = 2 successes:
- Possible patterns: SSF, SFS, FSS (3 ways)
- \(\binom{3}{2} = 3\) ✓

### 2. \(p^k\) — Probability of k Successes

If each success has probability p, then the probability of getting k specific successes (in specific positions) is:
\[
p \times p \times \cdots \times p = p^k
\]

### 3. \((1-p)^{n-k}\) — Probability of (n-k) Failures

Similarly, the probability of all the failures occurring is:
\[
(1-p) \times (1-p) \times \cdots \times (1-p) = (1-p)^{n-k}
\]

### 4. Putting It All Together

For any specific sequence with k successes and (n-k) failures:
\[
\text{Probability} = p^k (1-p)^{n-k}
\]

Since there are \(\binom{n}{k}\) such sequences:
\[
P(X = k) = \binom{n}{k} \times p^k \times (1-p)^{n-k}
\]

## Concrete Example

**Problem:** Flip a fair coin 5 times. What's the probability of getting exactly 3 heads?

Here:
- n = 5 trials
- k = 3 successes (heads)
- p = 0.5 (probability of heads)

\[
P(X = 3) = \binom{5}{3} (0.5)^3 (0.5)^{2}
\]

\[
\binom{5}{3} = \frac{5!}{3!2!} = \frac{120}{6 \times 2} = 10
\]

\[
(0.5)^3 = 0.125
\]
\[
(0.5)^2 = 0.25
\]
\[
0.125 \times 0.25 = 0.03125
\]

\[
P(X = 3) = 10 \times 0.03125 = 0.3125
\]

So there's a 31.25% chance of getting exactly 3 heads in 5 flips.

## Visual Example: n = 5, p = 0.5

| k (successes) | \(\binom{5}{k}\) | \(p^k\) | \((1-p)^{5-k}\) | Probability |
|---------------|-----------------|---------|----------------|-------------|
| 0 | 1 | 1 | 0.03125 | 0.03125 |
| 1 | 5 | 0.5 | 0.0625 | 0.15625 |
| 2 | 10 | 0.25 | 0.125 | 0.3125 |
| 3 | 10 | 0.125 | 0.25 | 0.3125 |
| 4 | 5 | 0.0625 | 0.5 | 0.15625 |
| 5 | 1 | 0.03125 | 1 | 0.03125 |

Sum = 1.0 ✓

## Key Properties

### 1. Sum of All Probabilities = 1
\[
\sum_{k=0}^{n} \binom{n}{k} p^k (1-p)^{n-k} = 1
\]
(This is just the binomial theorem: \((p + (1-p))^n = 1^n = 1\))

### 2. Expected Value
\[
E[X] = np
\]

### 3. Variance
\[
\text{Var}(X) = np(1-p)
\]

## Common Applications

1. **Quality Control** - Probability of finding defective items in a sample
2. **Medical Trials** - Success rate of a treatment in n patients
3. **Sports** - Probability of winning exactly k games in a season
4. **Genetics** - Probability of inheriting a specific trait
5. **Surveys** - Number of people who support a candidate in a sample

## When to Use Binomial Distribution

Use the binomial distribution when:
- ✓ Fixed number of trials (n)
- ✓ Each trial is independent
- ✓ Only two outcomes per trial
- ✓ Probability p is constant

## Relationship to Other Distributions

- **Bernoulli Distribution** = Binomial with n = 1
- **Approaches Normal** as n gets large (Central Limit Theorem)
- **Approaches Poisson** when n is large and p is small (rare events)

This binomial PMF is one of the most fundamental and widely used probability distributions!

---

This passage explains how to calculate the probability that a **discrete** random variable falls within a certain range using its **probability mass function (PMF)**.

## The Core Idea

For a discrete random variable \(X\), the probability that \(X\) is between two values \(s\) and \(t\) (inclusive) is simply the **sum of the probabilities** for each individual value in that range.

## The Formula

\[
P(s \leq X \leq t) = \sum_{k=s}^{t} p_X(k)
\]

Where:
- \(s\) = lower bound (inclusive)
- \(t\) = upper bound (inclusive)
- \(p_X(k) = P(X = k)\) = probability that \(X\) equals exactly \(k\)

## Why This Works

For discrete random variables, events like \(\{X = s\}\), \(\{X = s+1\}\), ..., \(\{X = t\}\) are **mutually exclusive** (they cannot happen simultaneously). By the **additivity of probability**:

\[
P(\text{event}_1 \text{ or } \text{event}_2 \text{ or } \cdots) = P(\text{event}_1) + P(\text{event}_2) + \cdots
\]

## Concrete Example

Let's say \(X\) = number of heads in 3 coin flips (binomial with n=3, p=0.5).

First, calculate the PMF:

| k | \(p_X(k)\) |
|---|-----------|
| 0 | 1/8 = 0.125 |
| 1 | 3/8 = 0.375 |
| 2 | 3/8 = 0.375 |
| 3 | 1/8 = 0.125 |

### Example 1: \(P(1 \leq X \leq 2)\)

\[
P(1 \leq X \leq 2) = \sum_{k=1}^{2} p_X(k) = p_X(1) + p_X(2)
\]

\[
= 0.375 + 0.375 = 0.75
\]

### Example 2: \(P(0 \leq X \leq 1)\)

\[
P(0 \leq X \leq 1) = p_X(0) + p_X(1) = 0.125 + 0.375 = 0.5
\]

### Example 3: \(P(2 \leq X \leq 3)\)

\[
P(2 \leq X \leq 3) = p_X(2) + p_X(3) = 0.375 + 0.125 = 0.5
\]

## Visual Representation

For a discrete distribution, you can think of each possible value \(k\) as having a "spike" of probability at that point. To find the probability over an interval, you add up the heights of all spikes within that interval:

```
p_X(k)
  ^
0.4 |     *
    |     *   *
0.3 |     *   *
    |     *   *
0.2 | *   *   *
    | *   *   *
0.1 | *   *   *
    | *   *   *
0.0 +---+---+---+---→ k
      0   1   2   3
      
P(1 ≤ X ≤ 2) = height at 1 + height at 2 = 0.375 + 0.375 = 0.75
```

## Common Variations

### 1. Strict Inequalities
\[
P(s < X < t) = \sum_{k=s+1}^{t-1} p_X(k)
\]

### 2. One-sided Bounds
\[
P(X \leq t) = \sum_{k=-\infty}^{t} p_X(k) = \sum_{k=0}^{t} p_X(k) \quad \text{(if X is non-negative)}
\]
\[
P(X \geq s) = \sum_{k=s}^{\infty} p_X(k) = \sum_{k=s}^{n} p_X(k) \quad \text{(if X has maximum n)}
\]

### 3. Cumulative Distribution Function (CDF)
\[
F_X(t) = P(X \leq t) = \sum_{k=-\infty}^{t} p_X(k)
\]

Then:
\[
P(s \leq X \leq t) = F_X(t) - F_X(s-1)
\]

## Example with Binomial Distribution

Let \(X \sim \text{Binomial}(n=10, p=0.3)\). What's \(P(2 \leq X \leq 5)\)?

\[
P(2 \leq X \leq 5) = \sum_{k=2}^{5} \binom{10}{k} (0.3)^k (0.7)^{10-k}
\]

This would be tedious to compute by hand, but in practice you'd use:
- Statistical tables
- Calculator functions (binompdf)
- Programming:

```python
from scipy.stats import binom

n, p = 10, 0.3
prob = sum(binom.pmf(k, n, p) for k in range(2, 6))
print(prob)  # Approximately 0.700
```

## Key Takeaway

For discrete random variables:
- **Point probability**: \(P(X = k) = p_X(k)\)
- **Interval probability**: Add up the point probabilities for all values in the interval

This additive property is what makes discrete distributions simpler to work with than continuous ones (where you need integration instead of summation).
---
