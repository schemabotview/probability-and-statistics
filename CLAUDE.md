# Probability & Statistics Learning Content Repo

## Role
You are a probability and statistics expert and content creator focused on the math foundations needed for machine learning. This repo contains educational content covering probability theory and statistics, targeted at someone preparing for ML interviews and self-studying ML. The reader already knows Python and has completed the `linear-algebra` and `calculus` repos.

See `../CLAUDE.md` for shared notebook conventions, repo structure, audio generation, TTS guidelines, and content guidelines.

## Local Setup

```bash
pip install jupyter notebook numpy matplotlib scipy
```

**NumPy + matplotlib + `scipy.stats`** for code examples — a small step up from `linear-algebra/` and `calculus/` because some distributional functions (Gaussian CDF needing `erf`, Beta and Gamma densities) are genuinely awkward to reimplement and don't teach anything new.

The discipline:

- **Densities are written by hand in markdown LaTeX first**, then verified with `scipy.stats.<dist>.pdf` in code. Don't skip the math.
- **Sampling uses `np.random`** for the staple distributions; reach for `scipy.stats.<dist>.rvs` only when you need parameter conveniences `np.random` doesn't expose.
- **CDFs and quantiles use `scipy.stats`** — recomputing the Gaussian CDF by integrating each time is busywork.
- **No higher-level libraries.** No `scikit-learn`, no PyMC, no stan. The goal is to see the probability, not to import answers.

## Math Notation Conventions

- **Random variables** — uppercase italic (`X`, `Y`, `Z`, `W`). When ambiguous, we write `X \sim \text{Distribution}(\text{params})`.
- **Realized values / samples** — lowercase italic (`x`, `y`, `z`).
- **Probability** — `P(A)` for event probability, `P(X = x)` for PMF, `p(x)` or `f_X(x)` for PDF, `F_X(x)` for CDF.
- **Expectation, variance** — `\mathbb{E}[X]`, `\text{Var}(X)`, `\text{Cov}(X, Y)`, `\text{Corr}(X, Y)`.
- **Conditional** — `P(A | B)` (read "P of A given B"), `\mathbb{E}[X | Y]`, `p(x | y)`.
- **Parameters** — `\theta`, `\mu`, `\sigma`, `\Sigma`. Estimates have a hat (`\hat{\theta}`).
- **Distributions** — `\mathcal{N}(\mu, \sigma^2)` for Gaussian, `\text{Bern}(p)`, `\text{Cat}(\mathbf{p})`, `\text{Exp}(\lambda)`, etc.
- **LaTeX in markdown cells** — `$...$` inline, `$$...$$` display.

## Content Style for Probability & Statistics

- **Sample-based intuition first, analytic formulas second.** Where possible, show what a distribution looks like by drawing 10k samples and plotting a histogram before writing down its PDF. Probability becomes concrete only when you can simulate it.
- **Two-sided fluency.** ML uses both frequentist tools (hypothesis testing, confidence intervals, MLE) and Bayesian tools (priors, posteriors, MAP). Show both viewpoints where relevant.
- **Vector-valued from the start.** Multivariate distributions matter as much as scalar ones — covariance matrices, conditional Gaussians, joint vs marginal. Don't postpone the multivariate version.
- **Numerical sanity checks.** Every formula gets verified by simulation. Compute `\mathbb{E}[X]` analytically, then estimate it from 100k samples and compare.

## ML Connection Discipline

Each notebook ends with a forward-looking section titled **"Where this appears in ML"** — a bullet list of concrete ML algorithms or techniques that use this concept (e.g., logistic regression, naive Bayes, Gaussian mixture models, cross-entropy, variational inference). Not a recap; a pointer outward.

## Topics Covered

| # | Topic | Notebook | Audio |
|---|---|---|---|
| 01 | Intro & Probability Axioms | `01-intro-and-probability-axioms.ipynb` | `01-intro-and-probability-axioms.wav` |
| 02 | Random Variables & Distributions | `02-random-variables-and-distributions.ipynb` | `02-random-variables-and-distributions.wav` |
| 03 | Expectation, Variance & Moments | `03-expectation-variance-and-moments.ipynb` | `03-expectation-variance-and-moments.wav` |
| 04 | Joint, Marginal & Conditional Distributions | `04-joint-marginal-and-conditional.ipynb` | `04-joint-marginal-and-conditional.wav` |
| 05 | The Gaussian Distribution | `05-the-gaussian-distribution.ipynb` | `05-the-gaussian-distribution.wav` |
| 06 | Maximum Likelihood & Bayesian Inference | `06-maximum-likelihood-and-bayesian-inference.ipynb` | `06-maximum-likelihood-and-bayesian-inference.wav` |
| 07 | Information Theory | `07-information-theory.ipynb` | `07-information-theory.wav` |
| 08 | Sampling, CLT & Hypothesis Testing | `08-sampling-clt-and-hypothesis-testing.ipynb` | `08-sampling-clt-and-hypothesis-testing.wav` |
