# Where Are the Old Left-Handed People?

A statistical investigation, using Bayes' theorem, into a widely-cited claim that left-handed people die significantly younger than right-handed people.

## Background

A 1991 study reported that left-handed people died, on average, nine years earlier than right-handed people. This notebook tests an alternative explanation: that the gap isn't caused by handedness itself, but by the fact that reported rates of left-handedness rose sharply over the 20th century (from ~3% in the early 1900s to ~11% today) due to changing social acceptability. If that's true, a population of recently deceased people will simply contain more old right-handers than old left-handers — purely as an artifact of when they were born, not how long they lived.

The notebook uses Bayesian statistics in `pandas` to reconstruct the apparent age-at-death gap from the changing rates of left-handedness alone, and compares the result to the original study's finding.

## Data Sources

Both datasets are loaded directly from remote URLs within the notebook (no local data files required):

- **Left-handedness rates by age** — digitized from a 1992 study by Gilbert & Wysocki, based on a 1986 National Geographic survey (~1 million respondents).
- **Death distribution data** — U.S. mortality data by age for 1999, from the [CDC](https://www.cdc.gov/nchs/nvss/mortality_tables.htm).

## Approach

1. Plot rates of left-handedness by age, then convert to birth year.
2. Apply Bayes' theorem to calculate the probability of being age *A* at death given left-handedness, and separately for right-handedness:

   P(A | LH) = P(LH | A) · P(A) / P(LH)

3. Combine with 1999 U.S. death distribution data to estimate the average age at death for each group.
4. Compare the resulting gap to the original study's reported 9-year difference.
5. Repeat the calculation using a hypothetical 2018 study year, to show how the gap shrinks as left-handedness rates stabilize across generations.

## Setup

```bash
pip install -r requirements.txt
jupyter notebook MTE.ipynb
```

Run all cells in order — the notebook fetches its data from the internet, so an active connection is required.

## Key Finding

The changing rates of left-handedness alone reproduce a meaningful chunk of the reported age gap, though not the full 9 years — suggesting the original study's result was likely driven substantially (if not entirely) by this generational/reporting effect rather than any causal link between handedness and lifespan.

## Contents

- `MTE.ipynb` — main analysis notebook
- `requirements.txt` — Python dependencies

## License

This project is licensed under the MIT License — see the LICENSE file for details.
