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

## (a) Independent Weighting of Both Probabilities
Here, the weighting function is independently applied to both the probability of gain and the probability of loss as follows:
$$
w_{gain} = w(p_{gain}), \quad w_{loss} = w(p_{loss})
$$

Using these weighted probabilities in a risky utility calculation gives us the expected weighted utility:
$$
\mathbf{E}[u(W)] = w_{gain} \cdot U(W_{gain}) + w_{loss} \cdot U(W_{loss})
$$
In the context of our decision framework, this becomes:
$$
\mathbf{E}[u(W)] = \exp\left(-\left(-\ln 0.02\right)^{\alpha}\right) \cdot 
\frac{(2,000)^{1-\gamma} - 1}{1 - \gamma} + \exp\left(-\left(-\ln 0.98\right)^{\alpha}\right)
\cdot \frac{(1,000-X^*)^{1-\gamma} - 1}{1 - \gamma}
$$
When put into practice, this approach seems to run into a \textbf{plethora of issues}. To start, since Prelec's function is non-linear, it is \textbf{typically true} that \(w_{gain} + w_{loss} \neq 1\). This disrupts the coherence of the probability space but is likely not a direct deal-breaker for modeling irrational probability perceptions. We will also encounter many undefined or incoherent solutions for \(X^*\), especially at the "higher" combinations of \(\alpha\) and \(\gamma\) where \(W_{loss} = W_0 - X^* \geq 0\) and the \(X^*\) values turn negative. Let us go through an example calculation of $X^*$ where \(\alpha = 0.25\) and \(\gamma = 0.7\). First, we can establish our CRRA utility function:
$$
u(w) = \frac{w^{0.3}-1}{0.3}
$$
Then, we can compute the utility of Option A (the safe option):
$$
u(1,000) = \frac{1,000^{0.3}-1}{0.3}
$$
The expected utility of Option B will be:
$$
\mathbf{E}[u(W)] = \exp\left(-\left(-\ln 0.02\right)^{0.25}\right) \cdot 
\frac{(2,000)^{0.3} - 1}{0.3} + \exp\left(-\left(-\ln0.98\right)^{0.25}\right)\cdot \frac{(1,000-X^*)^{0.3} - 1}{0.3}
$$
Setting the utility of Option A equal to the expected utility of Option B yields:
$$
\frac{1,000^{0.3}-1}{0.3} = \exp\left(-\left(-\ln 0.02\right)^{0.25}\right) \cdot 
\frac{(2,000)^{0.3} - 1}{0.3} + \exp\left(-\left(-\ln0.98\right)^{0.25}\right)\cdot \frac{(1,000-X^*)^{0.3} - 1}{0.3}
$$
Simplifying and solving for $X^*$:
\[
1,000^{0.3} - 1 - \exp\left(-\left(-\ln 0.02\right)^{0.25}\right) \cdot (2,000^{0.3} - 1) = \exp\left(-\left(-\ln 0.98\right)^{0.25}\right) \cdot \left( (1,000 - X^*)^{0.3} - 1 \right)
\]
\[
(1,000 - X^*) = \left( \frac{1,000^{0.3} - 1 - \exp\left(-\left(-\ln 0.02\right)^{0.25}\right) \cdot (2,000^{0.3} - 1) + \exp\left(-\left(-\ln 0.98\right)^{0.25}\right)}{\exp\left(-\left(-\ln 0.98\right)^{0.25}\right)} \right)^{\frac{1}{0.3}}
\]
\[
X^* = 1,000 - \left( \frac{1,000^{0.3} - 1 - \exp\left(-\left(-\ln 0.02\right)^{0.25}\right) \cdot (2,000^{0.3} - 1) + \exp\left(-\left(-\ln 0.98\right)^{0.25}\right)}{\exp\left(-\left(-\ln 0.98\right)^{0.25}\right)} \right)^{\frac{1}{0.3}}
\]
\[
X^* \approx -18.23
\]
In this context, negative $X^*$ values are incoherent and should be rejected. 