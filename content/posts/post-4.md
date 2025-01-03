+++
title = '[BBM 3] Generalized Kelly Criterion'
date = '2025-01-03'
math = true
+++

# Betting Behavior Methodologies 3: Generalized Kelly Criterion

Now, we can discuss practical ways to implement these risk aversion and probability weighting results for bets with varying conditions. To find a systematic way of modeling betting behavior &mdash; particularly **how much** someone might wager given a certain bet &mdash; we can look to the *Kelly Criterion* as a baseline. The Kelly Criterion is a widely recognized strategy in probability theory, financial decision-making, and betting for sizing bets in a manner that maximizes long-term geometric growth (Kelly 1956). It's traditionally derived using a logarithmic utility function, which is "optimal" but fairly unrealistic if used for modeling general risk behavior. Given finite wealth and a limited time horizon, not everyone exhibits perfectly logarithmic risk preferences. Luckily, logarithmic utility lies neatly within CRRA family, and if the classical Kelly Criterion is the utility-maximizing solution for someone with logarithmic utility, any "Kelly-like" criterion derived from a related concave CRRA utility function should also be the utility-maximizing solution for someone with those preferences. We will try to do exactly that: use the CRRA framework to create a more generalized form of the Kelly Criterion that can be adjusted for varying degrees of risk tolerance.

Let us first review the classical Kelly Criterion, and a few assumptions it holds. The Kelly Criterion prescribes the optimal fraction \(f^*\) of capital &mdash; or, in betting terminology, of the "bankroll" &mdash; to wager on a favorable (positive expected value) bet to maximize the long-term geometric growth rate. Given a bet with probability $p$ of winning and net odds \(b\) (net odds = decimal odds minus one), the classical Kelly Criterion is:
$$
f^* = \frac{p \cdot b - (1 - p)}{b}
$$
A few assumptions are:
- The bets have binary outcomes (although we can reframe any particular multi-outcome bet as multiple binary bets).
- Losing a bet involves losing the entire stake.
- The outcomes of the bets are independent.
- The investor can make repeated bets of identical structure.
- \(0 < f < 1\) should practically be assumed, as:
    - \(f \leq 0\) prescribes abstaining from betting.
    - \(f = 1\) only occurs when \(p = 1\) (an oxymoronic "risk-free bet").
    - \(f \leq 1\) will always hold true.

Let us establish the decision framework and the structure of the bets we will be working with. Given a bettor starting with wealth $W$, the goal is to determine the optimal fraction \(f\). A single bet is binary and characterized by two parameters: \(p\), the probability of winning, and \(b\), the net odds of winning (i.e., if the bettor wagers 1 unit, they receive \(1+b\) units if they win). Upon losing, the investor loses the wagered fraction \(f\) of their wealth. The final wealth \(W_{final}\) is therefore:
$$
    W_{\text{final}} = \begin{cases}
        W \cdot (1 + fb) & \text{with probability }p\\
        W \cdot (1 - f) & \text{with probability }1-p.
    \end{cases}
$$
Before we delve into the "irrational" component, let us first assume that the bettor **does** seek to maximize the expected utility of final wealth:
$$
\underset{f}{\text{max}}\text{ }\textbf{E}[u(W_{\text{final}})] = \underset{f}{\text{max}}\left[p \cdot u(W \cdot (1 + fb)) + (1 - p) \cdot (W \cdot (1 - f))\right]
$$
For simplicity, since the fraction \(f^*\) is scale-invariant, we can assume initial wealth \(W = 1\). Then, we can substitute in the CRRA utility function:
$$
\underset{f}{\text{max}}\text{ }\textbf{E}[u(W_{\text{final}})] = \underset{f}{\text{max}}\left[p \cdot \frac{(1 + f b)^{1 - \gamma} - 1}{1 - \gamma} + (1 - p) \cdot \frac{(1 - f)^{1 - \gamma} - 1}{1 - \gamma}\right]
$$
To find the optimal \(f^*\), we take the first-order condition of \(\textbf{E}[u(W_{\text{final}})]\) with respect to \(f\) and set it equal to zero:
$$
\frac{d}{df}\textbf{E}[u(W_{\text{final}})] = 0
$$
Computing the derivative:
$$
\begin{align*}
\frac{d}{df} \mathbf{E}[u(W_{\text{final}})] &= p \cdot \frac{d}{df} \left[ \frac{(1 + f b)^{1 - \gamma} - 1}{1 - \gamma} \right] + (1 - p) \cdot \frac{d}{df} \left[ \frac{(1 - f)^{1 - \gamma} - 1}{1 - \gamma} \right] \\
&= p \cdot (1 + f b)^{-\gamma} \cdot b + (1 - p) \cdot (1 - f)^{-\gamma} \cdot (-1) \\
&= p b \cdot (1 + f b)^{-\gamma} - (1 - p) (1 - f)^{-\gamma}
\end{align*}
$$