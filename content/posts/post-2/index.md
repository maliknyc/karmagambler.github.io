+++
title = 'Constant Relative Risk Aversion Quiz'
date = '2025-01-02'
math = true
+++

We want to understand how risk-averse a person is. The plan involves developing a quiz (or experimental task) that asks participants to choose between safe and risky options. By analyzing their choices, we can estimate their *risk-aversion coefficient*, \(\gamma\), using the constant relative risk aversion (CRRA) utility framework defined as:

$$
    u(W) = \begin{cases}
        \frac{W^{1-\gamma} - 1}{1 - \gamma} & \text{for } \gamma\geq0, \gamma\neq1\\
        \ln(W) & \text{for } \gamma = 1
    \end{cases}
$$

Where:
- \( W \): the final wealth.
- \( \gamma \): the relative risk aversion . A higher \(\gamma\) corresponds with greater risk-aversion, while \(\gamma = 1\) indicates risk-neutrality.
- \( \ln(W) \): logarithmic utility when \(\gamma = 1\), as \(\lim_{x\to1}\frac{x^{1-\gamma}-1}{1-\gamma}\) converges to \(\ln(x)\).

CRRA utility entails decreasing absolute risk aversion, the intuitive preference of taking on **less** risk as wealth increases.

Let's establish the quiz's decision framework. Participants begin with an initial wealth of $1,000. In each round of the quiz, participants are presented with two options:
- **Option A:** A sure gain of $150.
- **Option B:** A 36.79% probability of gaining \( $X_1 \) and a 63.21% probability of gaining \( $X_2 \).

The initial wealth amount is arbitrary and chosen to set a consistent baseline for all participants. The sure gain amount is also arbitrary and chosen to keep the subsequent demonstrative calculations consistent. The probability distribution (the \(\approx\) 63:37 split) is chosen as an approximation of the fixed inflection point at \(1/e\) in Prelec's probability weighting function, \( w(p)=\exp(-(-\ln p)^{\alpha}) \) (Prelec 1998). We will go into greater detail regarding the probability weighting function in the following section. For now, we are also avoiding the domain of losses and the concept of loss aversion altogether (although Option A can be interpreted as establishing a soft "reference point" of sorts at $1,150).

Now, we construct the \($X_2\) indifference points given different \($X_1\) and \(\gamma\) values. We can establish an indifference condition where a participant is equally likely to choose between the safe and the risky option. The indifferent condition can be represented as:
$$
u(\text{Option A}) = \mathbf{E}[u(\text{Option B})]
$$

