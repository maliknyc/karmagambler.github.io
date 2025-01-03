+++
title = '[Betting] Probability Weighting Quiz'
date = '2025-01-03'
math = true
+++

Building onto the [CRRA Quiz](https://maliknyc.github.io/karmagambler.github.io/posts/post-2/), we might want to assess how susceptible someone is to probability weighting: the tendency to overweight low probabilities and underweight large probabilities. For now, we'll focus on binary gambles with risky options that offer low-probability gains and high-probability losses. In other words, we're essentially attempting to explain "favorite-longshot bias" &mdash; an observed tendency for bettors to overvalue heavy underdogs and undervalue heavy favorites (Griffith 1949). Our setup might also bring to mind concepts from Salience Theory, which suggests that decision-makers overweight extremely &mdash; or "saliently" &mdash; unlikely events if they are aware of their possibility (i.e. we react more to possibility than we do to probability) (Bordalo 2012). The participant's baseline preferences will be modeled using the CRRA utility function and estimated risk aversion coefficient, \(\gamma\), elicited in the prior section. To capture the non-linear perception of probabilities, we will employ Prelec's probability weighting function:
$$
w\left(p\right)=\exp\left(-\left(-\ln p\right)^{\alpha}\right)
$$
Where:
- \( p \in (0, 1) \): the objective probability.
- \( \alpha > 0\): the degree of probability distortion (or the **curvature parameter**).
When \( \alpha < 1 \), the function overweights low probabilities and underweights high probabilities. When \( \alpha = 1 \), the function causes no probability distortion. When \( \alpha > 1 \), the function underweights low probabilities and overweights high probabilities. Because empirical estimates suggest an s-shape, for now, we will constrain \( \alpha \) to (0, 1).

Our goal is to integrate the weighting function into CRRA utility calculations to create a more comprehensive framework that incorporates the phenomenon of probability weighting.

Let us establish a particular decision framework that tests our aforementioned focus. Participants begin with an initial wealth of $1,000. In each round of the quiz, participants are presented with two options:

- **Option A:** A sure gain of $0. In other words, no bet.
- **Option B:** A 2% probability of gaining $1,000 and a 98% probability of losing \(X^*\).

Similar to our previous quiz, both the initial wealth amount and the sure gain amount are arbitrary and chosen for consistency and interpretability. The probability distribution is chosen to produce an option that offers a low-probability gain prospect and a high-probability loss prospect, similar to a "longshot" bet or a lottery scenario where $X^*$ is the price of a lottery ticket a participant is willing to pay. To finish constructing our quiz, we will have to compute the \( X^* \) values where the participant will be indifferent between Option A and Option B at different combinations of \( \alpha \) and \( \gamma \).

First, let us examine two strategies for applying probability weighting in binary gambles: (a) independently applying the weighting function to both outcomes and (b) applying the weighting function to one probability and deriving the other as its complement.
