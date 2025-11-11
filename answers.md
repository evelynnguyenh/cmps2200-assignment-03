# CMPS 2200 Assignment 3
## Answers

**Name:**Hoang Dieu Linh Nguyen

Place all written answers from `assignment-03.md` here for easier grading.
Part 1: 
1a. Greedy Algorithm:
Start from the largest power-of-two coin ≤ N.
Take as many of this coin as possible, subtract from N,
then move to the next smaller denomination. Repeat until N = 0.

1b. Proof of Optimality:
Greedy-choice property:
For denominations 2^0, 2^1, ..., 2^k, each coin value is exactly double
the previous. One coin of 2^i cannot be replaced by fewer smaller coins,
so choosing the largest feasible coin is never suboptimal.

Optimal substructure:
If the optimal solution for value N uses coin 2^i first, the remaining
amount N - 2^i must also be solved optimally. Otherwise replacing the
sub-solution with an optimal one yields a better overall solution,
contradicting optimality.

1c. Work and Span:
Number of coin types = log2(N).
Work = O(log N)
Span = O(log N)


Part 2: Making Change Again (Fortuito)

2a. Counterexample:
Denominations {1, 3, 4}, target N = 6.
Greedy → 4 + 1 + 1 = 3 coins.
Optimal → 3 + 3 = 2 coins.
Therefore greedy fails.

2b. Optimal Substructure Property:
Define OPT(N) = minimum number of coins to make N.
If last coin used is D_i:
    OPT(N) = 1 + OPT(N - D_i)
Proof:
If the subproblem OPT(N - D_i) is not optimal, replacing it yields
a better total solution, contradicting optimality. Hence optimal
substructure holds.

2c. Dynamic Programming:
Bottom-up DP:
    dp[0] = 0
    dp[x] = min(1 + dp[x - D] for all D ≤ x)
Return dp[N].

Work = O(Nk) where k = number of denominations.
Span = O(N).
