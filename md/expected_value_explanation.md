# Expected Value Formula

## Formula

**E[X] = Σ xi · P(xi)**

Or written out: E[X] = x₁·P(x₁) + x₂·P(x₂) + x₃·P(x₃) + ... + xₙ·P(xₙ)

## What Is Expected Value?

The **Expected Value** is the average value you would expect to get from a random variable if you repeated an experiment many, many times. It's like asking "what's the typical outcome over the long run?"

## Breaking Down the Formula

- **E[X]** - This is the expected value (the answer we're calculating)
- **xi** - Each possible outcome or value (x₁, x₂, x₃, etc.)
- **P(xi)** - The probability of each outcome happening
- **Σ** - The summation symbol, meaning "add all of these up"

## How to Calculate It

Follow these simple steps:

1. **List all possible outcomes** of your random variable
2. **Find the probability** of each outcome
3. **Multiply each outcome by its probability**
4. **Add all those products together**

The result is your expected value!

## Simple Example: Flipping a Coin

Let's say you win $1 for heads and lose $1 for tails.

- Outcome 1: Win $1 with probability 0.5
- Outcome 2: Lose $1 with probability 0.5

**Calculation:**
- E[X] = (1)(0.5) + (-1)(0.5)
- E[X] = 0.5 - 0.5
- E[X] = $0

The expected value is $0, meaning this is a fair game over the long run.

## Detailed Example: Rolling a Die

When you roll a standard six-sided die, what's the expected value?

**Step 1: List all outcomes**
- 1, 2, 3, 4, 5, 6

**Step 2: Find probabilities**
- Each number has a 1/6 probability (about 0.167)

**Step 3: Multiply each outcome by its probability**
- 1 × (1/6) = 1/6
- 2 × (1/6) = 2/6
- 3 × (1/6) = 3/6
- 4 × (1/6) = 4/6
- 5 × (1/6) = 5/6
- 6 × (1/6) = 6/6

**Step 4: Add them all up**
- E[X] = 1/6 + 2/6 + 3/6 + 4/6 + 5/6 + 6/6
- E[X] = 21/6
- **E[X] = 3.5**

So on average, you'll roll a 3.5! Notice that you can't actually roll 3.5, but that's the average over many rolls.

## Real-World Example: Lottery Ticket

Imagine a simple lottery:
- 1% chance to win $100
- 99% chance to win $0
- Ticket costs $2

**What's the expected value?**
- E[X] = (100)(0.01) + (0)(0.99)
- E[X] = 1 + 0
- E[X] = $1

But the ticket costs $2, so your **net expected value is -$1**. On average, you lose $1 per ticket!

## Important Points to Remember

1. **Weighted Average**: Expected value is a weighted average where probabilities are the weights
2. **Long-Run Average**: It tells you what happens "on average" over many trials
3. **Not Always Possible**: The expected value doesn't have to be an outcome that can actually happen (like rolling 3.5)
4. **Probabilities Must Sum to 1**: All your probabilities must add up to 1 (or 100%)
5. **Decision Making Tool**: Helps compare different options by their long-term averages

## Where Is This Used?

- **Insurance**: Companies use it to set premiums
- **Gambling**: Casinos ensure expected value favors the house
- **Finance**: Investors estimate expected returns
- **Business**: Companies evaluate risky projects
- **Statistics**: Foundation for many statistical methods
- **Game Theory**: Players calculate optimal strategies
- **Risk Management**: Professionals assess potential losses

## Key Takeaway

Expected value answers the question: **"If I did this over and over again, what would my average result be?"**

It's one of the most fundamental concepts in probability, statistics, and decision-making under uncertainty.
