+++
title = 'Introduction to Hedging for Bettors'
date = '2025-02-06'
math = true
draft = false
+++
#### Levels 2 & 3

Although it seems easy to call hedging --- where we match the units bet to the underlying probabilities --- an example of probability matching, there are clear distinctions between this strategy and classical probability matching. The classical probability matching strategy would not be to bet 75% of the units on Team A and 25% of the units on Team B within the same event, but rather to have a 75% chance of betting 100% of the units on Team A and a 25% chance of betting 100% of the units on Team B. Let us compare a classical probability matching strategy against both a hedging strategy and a deterministic strategy (where we bet on the likelier outcome 100% of the time).

Let us consider a situation where there are a sequence of independent, identical events that can be bet on. In each event, there are two mutually exclusive outcomes --- Team A winning or Team B winning --- defined by the set \(\Omega = \{A,B\}\) with \(Pr(A) = 0.75\) and \(Pr(B)=0.25\). The payout multipliers are “fair” (i.e., there is no vigorish) and represented by the “decimal odds,” which are the reciprocal of the probabilities. That is,

\[
d_A = \frac{1}{0.75}\approx1.3333, \quad d_B = \frac{1}{0.25}=4.00
\]

The net return for any wager \(w>0\) placed on an outcome with decimal odds \(d\) will be \(R = wd-w\), so for a bet of size \(w\) on outcome \(i\) (where \(i\) is either \(A\) or \(B\)), the net return is \(R_i=w(d_i-1)\). The bettor is committed to betting a fixed amount of \(w=\$100\) per event.

### Strategy 1: Pure Hedging

Consider Strategy 1, the hedging approach that we have already discussed. For each event, the bettor commits \$100 but splits their bet according to the implied probabilities:

\[
w_A = 0.75w. \quad w_B = 0.25w,
\]

so that \(w_A + w_B = \$100\). The net return when \(i\) occurs is as follows:

\[
R_i=
\begin{cases}
    w_A d_A - (w_A+w_B) & \text{if } i=A,\\[1mm]
    w_B d_B - (w_A+w_B) & \text{if } i=B.
\end{cases}
\]

Substituting in \(w=\$100\) yields \(R_A=R_B=0\) for every event. Because the net return is always 0, the variance is also zero (making it a degenerate lottery). The bettor's action is a mapping \(s_1:\Omega \rightarrow[0,w_A] \times [0,w_B]\). Regardless of whether Team A or Team B wins, the bettor always nets \$0, so Strategy 1 **completely** eliminates idiosyncratic risk.

### Strategy 2: Probability Matching

Then, consider Strategy 2, which involves classical probability matching. Here, instead of splitting \(w\) based on the implied probabilities, the bettor will wager the full amount \(w\) on **one** of the outcomes in each event, but the choice is randomized according to the implied probabilities. The action for each event can be defined as a function \(s_2:\Omega \rightarrow \{A, B\}\) where \(Pr(s_2=A)=0.75\) and \(Pr(s_2=B)=0.25\). The net return \(R\) for a single event is determined by both the chosen action and the realized outcome. Let us find the expected net return \(\mathbf{E}[R]\) per event. First, we can let event \(E_{ij}\) denote the event where the bettor chooses \(i\) and the outcome \(j\) occurs, with \(i, j \in \{A, B\}\). We can also let \(R_j^{(i)}\) be the net return when the bettor bets on \(i\) and the outcome \(j\) occurs. The probability \(P(E_{ij})\) should equal \(P(s_2=i)\cdot P(j)\), where the bettor's decision is independent of the outcome. Then, we can compute the following:

\[
\mathbf{E}[R]=\sum_{i\in \{A,B\}}\sum_{j\in \{A,B\}}P(E_{ij})R_j^{(i)}.
\]

There are four possibilities. First, consider the event where the bettor chooses \(A\) and outcome \(A\) occurs. This returns

\[
R_A^{(A)}=100(d_A-1)=100(1.3333-1)=33.33
\]

with a probability of \(P(E_{AA})=P(s_2=A) \cdot P(A) = 0.75 \cdot 0.75 = 0.5625\). There is also the event where the bettor chooses \(B\) and outcome \(B\) occurs. This returns

\[
R_B^{(B)}=100(d_B-1)=100(4-1)=300
\]

with a probability of \(P(E_{BB})=P(s_2=B) \cdot P(B) = 0.25 \cdot 0.25 = 0.0625\). Then, there are the two possibilities where the bettor loses their bet: \(E_{AB}\) and \(E_{BA}\). Both of them simply return the loss of the stake,

\[
R_A^{(B)}=R_B^{(A)}=-100,
\]

each occurring at the same probability:

\[
P(E_{AB})=P(s_2=A)P(B)=0.75\cdot0.25=0.1875,
\]
\[
P(E_{BA})=P(s_2=B)P(A)=0.25\cdot0.75=0.1875.
\]

We can then rewrite and solve for \(\mathbf{E}[R]\):

\[
\mathbf{E}[R]=P(E_{AA})\cdot R_A^{(A)}+
P(E_{AB})\cdot R_A^{(B)}+
P(E_{BB})\cdot R_B^{(B)}+
P(E_{BA})\cdot R_B^{(A)}
\]
\[
=(0.75\cdot0.75)(33.33)+(0.75\cdot0.25)(-100)+(0.25\cdot0.25)(300)+(0.25\cdot0.75)(-100)
\]
\[
=0.
\]

We can then compute variance:

\[
\text{Var}(R)=\mathbf{E}[R^2]-(\mathbf{E}[R])^2
\]
\[
= (0.5625)(33.33^2)+(0.1875)(100^2)+(0.0625)(300^2)+(0.1875)(100^2)
\]
\[
= 10000.
\]

Given our calculations, we can essentially define \(R\) as a random variable that takes on the four possible values displayed in Table 1.

| **(Action, Outcome)** | **\(R\)** | **Probability**                    |
|-----------------------|-----------|-------------------------------------|
| \((A,A)\)             | \(33.33\) | \(0.75 \times 0.75 = 0.5625\)         |
| \((A,B)\)             | \(-100\)  | \(0.75 \times 0.25 = 0.1875\)         |
| \((B,B)\)             | \(300\)   | \(0.25 \times 0.25 = 0.0625\)         |
| \((B,A)\)             | \(-100\)  | \(0.25 \times 0.75 = 0.1875\)         |

*Table 1: Net return for each outcome under Strategy 2.*

It is apparent that probability matching yields the same expected net return as Strategy 1 but increases the variance (or, for our purposes, “risk”) dramatically.

### Strategy 3: Always Betting on \(A\)

Lastly, consider the deterministic strategy of committing the full stake to outcome \(A\) for every event. The bettor's action is a constant mapping \(s_3 : \Omega \rightarrow \{A\}\). The net returns are defined as follows:

\[
R_i=
\begin{cases}
100\,(d_A-1) = 100\,(1.3333-1) \approx 33.33 & \text{if } i=A,\\[1mm]
-100 & \text{if } i=B.
\end{cases}
\]

The expected net return is then

\[
\mathbf{E}[R] = P(A)\cdot R_A+P(B)\cdot R_B
\]
\[
=(0.75)(33.33) + (0.25)(-100)
\]
\[
=0.
\]

Computing the variance:

\[
\mathrm{Var}(R) = E[R^2] - (E[R])^2
\]
\[
= P(A)\,(R_A)^2 + P(B)\,(R_B)^2 - (E[R])^2
\]
\[
= 0.75 \cdot (33.33)^2 + 0.25 \cdot (100)^2 - 0^2
\]
\[
\approx 3333.33.
\]

Strategy 3 yields the same expected net return of 0, but with a lower variance than Strategy 2 and a higher variance than Strategy 1.

Though potentially dubious, one can try to view Strategy 1 as a form of probability matching if one conceptualizes the \$100 wager as being divisible into many independent one-unit bets. Then, for each one-unit bet, a biased coin is flipped so that there is a 75% chance the unit is assigned to bet on Team A and a 25% chance the unit is assigned to bet on Team B. The more parts the \$100 is divided into, the more coin flips occur, and the more certain that 75% of the \$100 will be wagered on Team A and 25% of the \$100 will be wagered on Team B within a single event. Then, when aggregated, the hedging strategy “averages out” the randomness and yields a risk-free outcome. Still, classical probability matching would not allow for such diversification within a single event, and thus incurs greater variance. All three strategies are equivalent in expected net return under fair odds, but differ significantly in “risk.”

Although a risk-neutral bettor is indifferent among the three strategies, given that the expected net returns are equal, any risk-averse bettor should take the strategy that yields the lowest risk. For any risk-averse bettor — whose preferences are represented by an increasing, concave utility function \(u(\cdot)\) — a distribution with less dispersion is preferred if the mean is held constant. It is quite intuitive to conclude that Strategy 1 should generally be preferred over Strategy 3, and Strategy 3 should generally be preferred over Strategy 2, but just in case, let us make sure.

In our analysis, the net return in each event can be treated as a random variable so that for each strategy \(i \in \{1, 2, 3\}\), \(R^{(i)}\) can denote the random variable representing the net return per event when using Strategy \(i\). \(R^{(i)}\) should exhibit second-order stochastic dominance over \(R^{(j)}\) if

\[
\mathbf{E}[u(R^{(i)})] \ge \mathbf{E}[u(R^{(j)})]
\]

for every increasing concave function \(u\). We know that all three strategies net expected returns of 0, and we also know that \(R^{(1)}\) has zero variance and that the dispersion of \(R^{(3)}\) is lower than that of \(R^{(2)}\). So, the following holds for every increasing concave \(u\):

\[
\mathbf{E}\bigl[u(R^{(1)})\bigr] > \mathbf{E}\bigl[u(R^{(3)})\bigr] > \mathbf{E}\bigl[u(R^{(2)})\bigr].
\]

Because we can be sure that Strategy 1 second-order stochastically dominates Strategy 3 and Strategy 3 second-order stochastically dominates Strategy 2, the ordering

\[
\text{Strategy 1} \succ \text{Strategy 3} \succ \text{Strategy 2}
\]

should hold for any risk-averse bettor. This is important to know: it hints at the general wisdom that pure, classical probability matching is not very useful in betting, but employing the “probability-matching-like” strategy of hedging can be incredibly powerful for minimizing (or completely eliminating) betting risk. At the risk of going on a slight tangent from classical probability matching, we will discuss a few more uses of Strategy 1.
