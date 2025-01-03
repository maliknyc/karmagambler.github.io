+++
title = 'Constant Relative Risk Aversion Quiz'
date = '2025-01-02'
math = true
+++

We want to undersatnd how risk-averse a person is. The plan involves developing a quiz (or experimental task) that asks participants to choose between safe and risky options. By analyzing their choices, we can estimate their *risk-aversion coefficient*, \(\gamma\), using the constant relative risk aversion (CRRA) utility framework defined as:

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

CRRA utility entails decreasing absolute risk aversion, the intuitive preference of taking on \textbf{less} risk as wealth increases.


