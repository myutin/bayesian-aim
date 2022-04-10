# Bayesian Aim
Calculates the probability of clicking circles

## Concept
Any osu beatmap perscribes a series of cursor movements. We want to measure how difficult these movements are. Historically, difficulty splits into two components: agility and precision. Here we combine both of these aspects into one computation.

We describe a range of comfortable cursor movements. Some of these movements fit a beatmap. We can rephrase the agility-precision split as follows:
- Agility: how uncomfortable are the prescribed cursor movements?
- Precision: what margin of error does the beatmap permit?

The answer to both of these questions is probability.

We start with a model of cursor movement. This model assigns different probabilities to various movements. Comfortable movements have high probabilities; uncomfortable movements have low probabilities. A beatmap prescribes some range of movements. We add up the total probability of this range under our model.

This total probability measures both agility and precision. A more agile, less comfortable, range of motion has a lower probability. A more precise, narrower, range of motion also has a lower probability.

See also the included math-blog-posts. These more fully describe the above concepts.

## Roadmap

### Document underlying math:
- jerk as white noise
- integrals as linear transformations
- Bayes' law
- the failures of normal distributions
- the actual distribution in use

Answer any questions with supporting documentation. Iterate until no more questions.

### Agile development:
- write psuedocode
- write unit-tests
- write code

Minimum feature list:
- read .osu files (library already exists)
- evaluate difficulty
  - most likely, difficulty will be evaluated per-segment, with some other algorithm aggregating the segments.
- produce sample cursor paths
  - this lets us visually check that our model is correct
  - ideally, this would take the form of a generated .npy file
  - however, a .gif would also suffice

Deployment and monitoring (_i.e._, parameter tuning):
- some parameters have objective mathematical descriptions
  - analytical derivations will work for some
  - computational methods might work for others
  - one of the parameters has 100+ dimensions, so that'll be fun
- other parameters should be fit to human player data
  - that's what you guys do best, right?
