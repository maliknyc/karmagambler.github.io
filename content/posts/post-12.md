+++
title = 'Introduction to Hedging for Bettors'
date = '2025-01-26'
math = true
draft = true
+++
#### Levels 2 & 3

In fixed-odds betting, where payouts are proportional to the “betting odds” of events, hedging becomes a powerful strategy. The betting odds for an event are set by the bookmakers and **roughly** reflect the “true” probabilities of different outcomes occurring. Though the reality of the relationship between the betting odds and the true probabilities is much more complex than the assumption that they are equal, for the purposes of hedging and discussing hedging strategies, only betting odds matter. We will dive more deeply into how betting odds are actually set in a later exploration about probability matching for bookmakers. Let us explore how to implement the probability-matching-like strategy of hedging in betting.


Consider a simple scenario where a bettor is presented with odds on an event with two mutually exclusive outcomes — a game where either Team A or Team B must win. Also assume for the moment that there is no vigorish (i.e., no built-in bookmaker margin or edge) so that the odds represent “fair” payouts. “Team A to win” is offered at +300, corresponding to an implied probability of \(p_A = \frac{100}{300+100} = 0.25\) and a proportional payout multiplier of 4.0x (if you bet \$100 and win, you are returned your \$100 stake plus \$300 in winnings). Team B is offered at -300, corresponding to an implied probability of \(p_B = 1-0.25 = 0.75\) and a payout multiplier of 1.33x. If the bettor has a total stake \(M\) that must be wagered in full and wishes to eliminate risk — i.e., ensure a break-even outcome — the bettor can allocate the stake in direct proportion to the implied probabilities. The bettor would wager

\[
w_A = M \cdot 0.25 = \$25 \text{ on Team A}
\]

and

\[
w_B = M \cdot 0.75 = \$75 \text{ on Team B.}
\]

The payoff structure is designed such that if Team A wins, the bettor gets back their \$25 stake on Team A, is rewarded \$75 in winnings, and loses \$75 on Team B, netting \$0 in total profit. Conversely, if Team B wins, they get back their \$75 wager on Team B, are rewarded \$25 in winnings, and lose \$25 on Team A, netting \$0 in total profit. The bettor's dollars (or some fixed unit) are allocated in proportion to the market's implied probabilities — an instance of using a strategy *similar* to probability matching used to eliminate risk. If this strategy seems completely pointless, consider a situation where someone might bet \$25 on Team A, immediately regret it, and bet another \$75 on Team B in order to “close out” of their bet.

A more dynamic hedging scenario arises when a bettor anticipates that market odds will shift over time. Consider another situation with the same conditions (where Team A is priced at +300 and Team B is priced at -300). Suppose a bettor believes that Team A is undervalued — that is, the bettor estimates that Team A's true chance of winning is actually 50%. This bettor also believes that the market will eventually adjust to reflect his assessment of the true probabilities. Acting on these beliefs (though, the latter belief alone is sufficient justification) the bettor initially wagers \(w_A\) (say, \$50) on Team A at +300. If the bettor is correct and the odds for both teams eventually shift to even money (+100 for each, or 50-50 probabilities), a hedging opportunity arises. Let us denote the decimal odds for Team A at +300 by \(d_A\) and for Team B at even money by \(d_B^*\). The bettor already bet \$50 on Team A at \(d_A = 4.00\) and now has the opportunity to bet on Team B at \(d_B^* = 2.00\). A **general rule** for achieving a risk-free hedge is as follows: the set of wagers should be structured so that the resulting net return is identical regardless of which outcome materializes. Let \(w_B\) be the amount the bettor wagers on Team B at \(d_B^*\), \(R_A\) the net return if Team A wins, and \(R_B\) the net return if Team B wins. Then, the return structure should be:

\[
R_A = w_A d_A - (w_A+w_B), \quad R_B = w_B d_B^* - (w_A+w_B).
\]

Since \(R_A = R_B\) must be satisfied to eliminate risk, we can obtain

\[
w_A d_A - (w_A+w_B) = w_B d_B^* - (w_A+w_B),
\]

\[
w_A d_A = w_B d_B^*.
\]

Thus, it becomes clear that the ratio of the stakes must satisfy

\[
\frac{w_A}{w_B}=\frac{d_B^*}{d_A}.
\]

The decimal odds are directly related to the implied probabilities of the outcomes, so matching the ratio of your stakes to the ratio of the odds is equivalent to matching the proportion of units you bet to the underlying probabilities. For our example, the ratio of stakes must be:

\[
\frac{w_A}{w_B} = \frac{d_B^*}{d_A} = \frac{2.00}{4.00} = \frac{1}{2}.
\]

That is, the stake on Team A should be half the stake on Team B. If the bettor initially wagers \(w_A = \$50\) on Team A at +300 odds, then the appropriate hedge is to wager \$100 on Team B at +100 odds. If Team A wins, the bettor gets back their \$50 stake on Team A, wins \$150, and loses \$100 on Team B, netting a profit of \$50. If Team B wins, the bettor gets back their \$100 stake on Team B, wins \$100, and loses \$50 on Team A, netting a profit of \$50.
