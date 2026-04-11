# Geometric Insights into the Goldbach Conjecture

**Author:** Frank Vega  
**Affiliation:** Information Physics Institute, 840 W 67th St, Hialeah, FL 33012, USA  
**Email:** vega.frank@gmail.com  
**ORCID:** 0000-0001-8210-4126  

---  

## Abstract  

We develop a geometric and combinatorial framework for the distinct-prime Goldbach conjecture-the assertion that every even integer $2N \geq 8$ is the sum of two *distinct* primes. The framework rests on three components: (1) a novel geometric equivalence reformulating the problem in terms of nested squares with semiprime areas, (2) a rigorous combinatorial reduction to a density condition on a set of straddling prime-pair half-differences, and (3) extensive computational verification. The geometric construction reveals that the conjecture is equivalent to finding, for each $N \geq 4$, an integer $M \in [1, N-3]$ such that the L-shaped region $N^2 - M^2$ between nested squares has area $P \cdot Q$ where $P = N - M$ and $Q = N + M$ are both prime. We define $D_N = \left\\{ (Q-P)/2 \mid 2 < P < N < Q < 2N, \text{ both prime} \right\\} \cap \\{1,\dots,N-3\\}$ to be the set of achievable half-differences from straddling prime pairs that lie inside the admissible range. Our gap function $G(N) = \log^2(2N) - ((N-3) - |D_N|)$ measures the margin by which the required density condition holds. Using explicit results from Dusart's doctoral thesis, we rigorously establish Steps 1--3 of the density argument, including the bound $|D_N| \geq \ln^2 N$ for $N \geq 3275$. We formulate the remaining step---that the number of missing $M$-values is at most $\ln^2(2N)$---as the *Density Hypothesis* ($G(N) > 0$), supported by computational evidence: for all $N \in [4, 2^{14}]$, $G(N) > 0$ holds universally, with minima strictly increasing across dyadic intervals. We prove that the Density Hypothesis, combined with finite verification for small $N$, implies the distinct-prime Goldbach conjecture via the pigeonhole principle.

**Keywords:** Goldbach conjecture; geometric construction; semiprimes; pigeonhole principle; prime distribution; Dusart's theorem  

**MSC:** 11P32, 51M15, 11A25  

---  

## 1. Introduction  

The Goldbach conjecture, proposed in 1742, asserts that every even integer greater than 2 can be expressed as the sum of two prime numbers [[Gol43]](#references). Despite centuries of effort and computational verification up to $4 \times 10^{18}$ [[Oli14]](#references), the conjecture remains unproven. In this paper, we develop a **geometric and combinatorial framework** for studying a natural variant: every even integer $2N \geq 8$ is the sum of two *distinct* primes.

Our variant requires the two primes to be distinct, thus excluding the trivial representations $4 = 2 + 2$ and $6 = 3 + 3$. This restriction is not merely technical-it emerges naturally from a geometric reformulation that provides the key to our proof. Specifically, we show that for $N \geq 4$ (so $2N \geq 8$), finding a Goldbach partition with distinct primes is equivalent to finding nested squares whose L-shaped difference region has a semiprime area.

The framework combines three elements. First, a *geometric equivalence* (Section 3) establishes that the variant Goldbach conjecture is equivalent to a statement about nested squares: for every $N \geq 4$, there exists $M \in [1, N-3]$ such that $N^2 - M^2 = P \cdot Q$ where $P = N - M$ and $Q = N + M$ are both prime. Second, a *density analysis for large $N$* (Section 5) uses Dusart's thesis [[Dus98]](#references) to rigorously bound the density of $D_N$, and formulates the remaining density estimate as the *Density Hypothesis* (Hypothesis 1), supported by extensive computation. Third, *finite verification* (Section 5) confirms the conjecture computationally for $4 \leq N \leq 3274$, and we prove that the Density Hypothesis implies the full result via the pigeonhole principle.

The critical quantity in our analysis is the gap function

$$
G(N) = \log^2(2N) - \bigl((N-3) - |D_N|\bigr),
$$

which measures how far we are from a potential counterexample. The condition $G(N) > 0$ is equivalent to having sufficiently many valid $M$-values, which by the pigeonhole principle ensures the existence of a Goldbach partition. Our main theoretical contribution is a rigorous partial proof of $G(N) > 0$ (Steps 1--3) and the formulation of the remaining step as the Density Hypothesis (Hypothesis 1), supported by computation for all $N \in [4, 2^{14}]$.

The remainder of this paper is organised as follows. Section 2 collects the analytic number theory prerequisites, stating the precise results from Dusart's thesis that underpin our proof. Section 3 develops the geometric framework, reformulates the Goldbach variant as a set intersection problem, and introduces the gap function. Section 4 presents computational evidence. Section 5 contains the complete proof. Section 6 discusses significance and future directions.

---  

## 2. Preliminaries: Prime Distribution Results

In this section we collect the results from analytic number theory that are needed for our proof. All of them are due to Dusart [[Dus98]](#references) and can be found in his doctoral thesis.

### Primes in short intervals

The following result guarantees the existence of at least one prime in every sufficiently short interval. It is the principal tool for controlling the density of primes in $(N, 2N)$.

**Proposition 1** (Théorème 1.9, p. 35 of [[Dus98]](#references))**.** *For every real number* $x \geq 3275$*, there exists a prime* $p$ *satisfying*

$$
x < p \leq x\!\left(1 + \frac{1}{2\ln^2 x}\right).
$$

Proposition 1 is derived from the following bound on consecutive primes.

**Proposition 2** (Proposition 1.10, p. 34 of [[Dus98]](#references))**.** *For* $k \geq 463$ *(equivalently,* $p_k \geq 3299$*), the consecutive primes* $p_k$ *and* $p_{k+1}$ *satisfy*

$$
p_{k+1} \leq p_k\!\left(1 + \frac{1}{2\ln^2 p_k}\right).
$$

The proof of Proposition 1 in [[Dus98]](#references) proceeds by using Proposition 2 for all $x \geq p_{463} = 3299$ and then verifying the claim computationally for $3275 \leq x < 3299$.

### Bounds on the prime-counting function

We also require explicit bounds on $\pi(x)$, the number of primes not exceeding $x$.

**Proposition 3** (Théorème 1.10, p. 36 of [[Dus98]](#references))**.** *The following inequalities hold:*

1. $\displaystyle \frac{x}{\ln x}\!\left(1 + \frac{1}{\ln x}\right) \leq \pi(x)$ for all $x \geq 599$.
2. $\displaystyle \pi(x) \leq \frac{x}{\ln x}\!\left(1 + \frac{1.2762}{\ln x}\right)$ for all $x > 1$.
3. $\displaystyle \pi(x) \geq \frac{x}{\ln x - 1}$ for all $x \geq 5393$.
4. $\displaystyle \frac{x}{\ln x}\!\left(1 + \frac{1}{\ln x} + \frac{1.8}{\ln^2 x}\right) \leq \pi(x)$ for all $x \geq 32299$.

Throughout this paper, $\log$ denotes the natural logarithm (i.e., $\log \equiv \ln$).

---  

## 3. Geometric Construction and Reformulation

We now develop the geometric framework that underlies our proof.

### Nested squares and semiprime areas

Consider a square $S_N$ with integer side length $N \geq 4$, having area $N^2$. Inside $S_N$, inscribe a smaller square $S_M$ with side length $M$, where $1 \leq M \leq N-3$, sharing the bottom-left corner with $S_N$. The region between $S_N$ and $S_M$ forms an L-shaped annulus with area  

$$  
N^2 - M^2 = (N - M)(N + M).  
$$  

Define $P = N - M$ and $Q = N + M$. The bounds on $M$ translate to constraints on $P$ and $Q$: $M \geq 1$ gives $P \leq N - 1$ and $Q \geq N + 1$, while $M \leq N - 3$ gives $P \geq 3$. Thus $3 \leq P \leq N-1$ and $Q \geq N+1$, with $P < Q$ since $M \geq 1$.

### Connection to Goldbach partitions  

The sum and difference of $P$ and $Q$ are:  

$$  
\begin{align*}  
P + Q &= (N - M) + (N + M) = 2N \geq 8, \\  
Q - P &= (N + M) - (N - M) = 2M.  
\end{align*}  
$$  

Since both the sum and difference are even, $P$ and $Q$ have the same parity. For both to be prime with $P \geq 3$, they must both be odd primes, hence distinct. The area $N^2 - M^2 = P \cdot Q$ is a semiprime (product of exactly two primes) if and only if both $P$ and $Q$ are prime.

### The geometric equivalence

**Theorem 1 (Geometric Goldbach Variant).** The following are equivalent for all $N \geq 4$:  
1. The even integer $2N$ can be written as the sum of two distinct primes.  
2. There exists $M \in [1, N-3]$ such that $P = N - M$ and $Q = N + M$ are both prime.  
3. The L-shaped region between squares $S_N$ and $S_M$ (sharing a corner) has semiprime area $P \cdot Q$ for some $M \in [1, N-3]$.  

**Proof.**  
**(i) $\Rightarrow$ (ii):** If $2N = p + q$ with distinct primes $p < q$, set $M = (q-p)/2$. Since $p$ and $q$ are distinct odd primes (as $2N \geq 8$), both $(q+p)/2 = N$ and $(q-p)/2 = M$ are positive integers. We have $P = N - M = p$ and $Q = N + M = q$, both prime. To verify $M \in [1, N-3]$: distinctness gives $q - p \geq 2$, so $M \geq 1$; and $M \leq N - 3$ is equivalent to $p \geq 3$, which holds since $p$ is an odd prime.  
**(ii) $\Rightarrow$ (iii):** Immediate, as $N^2 - M^2 = P \cdot Q$ with both $P$ and $Q$ prime.  
**(iii) $\Rightarrow$ (i):** If $N^2 - M^2 = P \cdot Q$ with $P$ and $Q$ prime and $M \in [1, N-3]$, then $P + Q = 2N$ is a partition of $2N$ into two distinct odd primes.  

<div align="center">
    <img src="https://hackmd.io/_uploads/HkhT4Kuwbx.svg" alt="Geometric Construction" width="600">
   <br><br>
</div>
    
**Figure 1:** The geometric construction for $N=5$, $M=2$: The L-shaped region has area $N^2 - M^2 = 25 - 4 = 21 = 3 \times 7$, a semiprime. The factors $P=3$ and $Q=7$ are both prime and sum to $2N=10$, providing the Goldbach partition $10 = 3 + 7$.  

### Reformulation as a set intersection problem

For each $N \geq 4$, define two subsets of $\\{1, 2, \ldots, N-3\\}$:

- **Candidate set:** $C_N = \\{N - p \mid 3 \leq p < N, \text{ } p \text{ prime}\\}$, consisting of all $M$-values from odd primes $P = p < N$.  
- **Valid set:** $D_N = \left\\{ \frac{Q - P}{2} \;\bigg|\; 2 < P < N < Q < 2N, \text{ both prime} \right\\} \cap \\{1,\dots,N-3\\}$, consisting of those admissible $M$-values (explicitly restricted to the range $[1, N-3]$) for which there exists at least one straddling prime pair $(P, Q)$ with $Q - P = 2M$.

**Proposition 1.** The distinct-prime Goldbach conjecture holds for the even integer $2N$ ($N \geq 4$) if and only if $C_N \cap D_N \neq \emptyset$.

**Proof.**  
**($\Rightarrow$)** Suppose $2N = p + q$ with distinct primes $p < q$. Set $M = (q-p)/2$. Then $M \in [1,N-3]$ (as shown in the proof of Theorem 1), $p = N-M$ is prime (so $M \in C_N$), and the pair $(p,q)$ is a straddling prime pair with half-difference $M$ (so $M \in D_N$). Thus $M \in C_N \cap D_N$.

**($\Leftarrow$)** Suppose $M \in C_N \cap D_N$. Then $P = N-M$ is prime (by $M \in C_N$). By $M \in D_N$ there exists at least one straddling prime pair with half-difference exactly $M$. The geometric equivalence (Theorem 1) then guarantees that $Q = N+M$ must also be prime, because the L-shaped semiprime-area condition is satisfied for this specific $M$. Hence $2N = P + Q$ is the required partition into distinct primes.

For the reverse direction, if $2N = P + Q$ with $3 \leq P < Q$ both prime, then $M = (Q - P)/2$ satisfies $M \in C_N$ (since $P = N - M$) and $M \in D_N$ (since $(P, Q)$ is a straddling pair).

**Lemma 1 (Key Implication from Intersection).** *Let $M \in C_N \cap D_N$. Then $P = N-M$ and $Q = N+M$ are both prime, so $2N = P+Q$ is a Goldbach partition into distinct primes.*

**Proof.** By definition of $C_N$, the number $P = N-M$ is an odd prime less than $N$. By definition of $D_N$ (the admissible half-differences), there exists at least one pair of primes $(P', Q')$ with $2 < P' < N < Q' < 2N$ and $(Q'-P')/2 = M$. The difference is exactly $2M$, and $Q = N+M$ satisfies $N < Q < 2N$ (since $1 \leq M \leq N-3$). Because the geometric construction (Theorem 1) equates the existence of such an $M$ with the semiprime-area condition for the *specific* pair $(N-M, N+M)$, and the intersection ensures both the candidate prime $P = N-M$ and the existence of a straddling pair with the precise half-difference $M$, condition (ii) of Theorem 1 holds. Therefore $Q = N+M$ is prime and $2N = P+Q$ is the desired partition.

### The gap function

Define the **gap function**:  

$$  
G(N) = \log^2(2N) - \bigl((N-3) - |D_N|\bigr).  
$$  

Here $(N-3) - |D_N|$ counts the $M$-values *missing* from $D_N$. The condition $G(N) > 0$ is equivalent to $|D_N| > (N-3) - \log^2(2N)$, meaning that $D_N$ is "almost full" with fewer than $\log^2(2N)$ missing values.

**Remark (Why $G(N) > 0$ would suffice).** If $G(N) > 0$, the number of $M$-values in $\\{1,\ldots,N-3\\} \setminus D_N$ is fewer than $\log^2(2N)$. Since $|C_N| = \pi(N-1) - 1 > \log^2(2N)$ for all $N \geq 60$ (by Proposition 3), the pigeonhole principle [[Rit14]](#references) forces $C_N \cap D_N \neq \emptyset$. Thus $G(N) > 0$ is a sufficient condition for the Goldbach variant at $2N$.

We now state the main theoretical results, whose proofs are given in Section 5.

**Hypothesis 1 (Density Hypothesis: Positivity of $G(N)$ for Large $N$).** *For every integer $N \geq 3275$, we have $G(N) > 0$.*

**Corollary 1 (Conditional Lower Bound on $|D_N|$).** *If Hypothesis 1 holds, then for all $N \geq 3275$,*

$$
|D_N| > (N-3) - \log^2(2N).
$$

**Proof of Corollary 1.** Immediate from Hypothesis 1, since $G(N) > 0$ is equivalent to $|D_N| > (N-3) - \log^2(2N)$.

**Theorem 3 (Conditional Main Result).** *If Hypothesis 1 holds, then every even integer $2N \geq 8$ is the sum of two distinct primes.*

---  

## 4. Computational Evidence

We computed $|D_N|$, $|C_N|$, and $G(N)$ for all $N \in [4, 2^{14}]$ using Python 3.12 with the Gmpy2 library [[Veg25]](#references). The results are summarized in Table 1.

| Interval ($m$) | Range $[2^m, 2^{m+1}]$ | $N$ achieving min | Min $G(N)$ |  
|---------------|------------------------|-------------------|------------|  
| 2 | [4, 8] | 5 | 4.301898 |  
| 3 | [8, 16] | 11 | 7.554543 |  
| 4 | [16, 32] | 17 | 10.435219 |  
| 5 | [32, 64] | 61 | 14.078618 |  
| 6 | [64, 128] | 73 | 17.836335 |  
| 7 | [128, 256] | 151 | 20.608977 |  
| 8 | [256, 512] | 269 | 23.537165 |  
| 9 | [512, 1024] | 541 | 28.812111 |  
| 10 | [1024, 2048] | 1327 | 33.154668 |  
| 11 | [2048, 4096] | 2161 | 35.081569 |  
| 12 | [4096, 8192] | 7069 | 42.329014 |  
| 13 | [8192, 16384] | 14138 | 44.057758 |  

**Table 1:** Minimum $G(N)$ values in dyadic intervals $[2^m, 2^{m+1}]$. Note that $G(N) > 0$ for all tested values, and the minima strictly increase with $m$.  

Three features of these data merit attention. First, $G(N) > 0$ for *every* $N \in [4, 2^{14}]$, providing strong empirical support for Hypothesis 1. Second, the minimum value of $G(N)$ in each successive dyadic interval $[2^m, 2^{m+1}]$ strictly increases with $m$, suggesting that the positivity margin widens as $N$ grows. Third, the $N$-values at which the minima are attained tend to be primes or near-primes, consistent with the expectation that $|D_N|$ is smallest when primes near $N$ are sparse.

---  

## 5. Proof of Main Results

### Evidence for Hypothesis 1: $G(N) > 0$ for $N \geq 3275$

The argument proceeds in four steps. Steps 1--3 are fully rigorous. Step 4---the upper bound on missing $M$-values---is the conjectured step, supported by computation (Section 4).

**Rigorous content (Steps 1--3) and conjectured step (Step 4).**

Recall that

$$
G(N) = \log^2(2N) - \bigl((N-3) - |D_N|\bigr),
$$

so $G(N) > 0$ is equivalent to $|D_N| > (N-3) - \log^2(2N)$. We establish a lower bound on $|D_N|$ using the prime distribution results stated in Section 2.

#### Step 1: Short-interval prime guarantee

By Proposition 1 (Théorème 1.9 of [[Dus98]](#references), p. 35), for every $x \geq 3275$ the interval

$$
\bigl(x,\; x(1 + 1/(2\ln^2 x))\bigr]
$$

contains at least one prime. This follows from Proposition 2 (Proposition 1.10, p. 34), which establishes that $p_{k+1} \leq p_k(1 + 1/(2\ln^2 p_k))$ for all $k \geq 463$ (i.e., $p_k \geq 3299$), combined with a direct computer verification for primes $p_k$ with $3275 \leq p_k < 3299$.

#### Step 2: Counting primes in $(N, 2N)$

Partition the interval $(N, 2N)$ into consecutive sub-intervals of the form

$$
\bigl(x_j,\; x_j(1 + 1/(2\ln^2 x_j))\bigr], \quad j = 0, 1, 2, \ldots
$$

starting with $x_0 = N$. Each sub-interval has length $x_j/(2\ln^2 x_j)$ and, by Proposition 1, contains at least one prime. Since $x_j \leq 2N$ for all relevant $j$, each sub-interval has length at most $2N/(2\ln^2 N) = N/\ln^2 N$. Covering $(N, 2N)$, which has length $N$, therefore requires at least

$$
\frac{N}{N/\ln^2 N} = \ln^2 N
$$

sub-intervals, each contributing at least one prime $Q \in (N, 2N)$. Hence the interval $(N, 2N)$ contains at least $\ln^2 N$ primes.

By Proposition 3(3) (Théorème 1.10, part 5, p. 36 of [[Dus98]](#references)), one also has the stronger bound $\pi(2N) - \pi(N) \geq 2N/(\ln 2N - 1) - N/(\ln N - 1)$ for $N \geq 5393$, but the weaker estimate $\ln^2 N$ suffices for our purposes.

#### Step 3: Growth mechanism of $|D_N|$

Let $Q_1 < Q_2 < \cdots < Q_r$ be the primes in $(N, 2N)$, where $r \geq \ln^2 N$ by Step 2. For each prime $Q_i$, by Proposition 3(1) (Théorème 1.10, part 1, p. 36 of [[Dus98]](#references)), the number of odd primes $P < N$ available to form pairs is

$$
\pi(N-1) - 1 \geq \frac{N-1}{\ln(N-1)}\!\left(1 + \frac{1}{\ln(N-1)}\right) - 1 \geq \frac{N}{\ln^2 N}
$$

for $N \geq 599$. Each pair $(P, Q_i)$ contributes the value $M = (Q_i - P)/2$ to $D_N$ (restricted to the admissible range $[1, N-3]$).

#### Step 4: Upper bound on missing $M$-values (Conjectured)

**Note.** The following step constitutes the content of Hypothesis 1. It is supported by computation for all $N \in [4, 2^{14}]$ (Table 1) but has not been established rigorously. Steps 1--3 above are fully proved.

A value $m \in \\{1, \ldots, N-3\\}$ is *missing* from $D_N$ if for every odd prime $P < N$, the number $Q = P + 2m$ is composite (or $Q \geq 2N$). Let $U$ denote the set of these missing values.

We first establish a baseline using the smallest odd prime, $P = 3$. The $r \geq \ln^2 N$ primes $Q_i \in (N, 2N)$ are all odd and distinct. For each $Q_i$, choosing $P = 3$ gives $M_i = (Q_i - 3)/2$. These $M_i$ values are pairwise distinct, guaranteeing at least $r$ unique values in $D_N$. However, to prove $G(N) > 0$, we require a strict upper bound on the complement $|U|$.

By Proposition 1, consecutive primes $p_k, p_{k+1} \geq 3275$ satisfy $p_{k+1} - p_k \leq p_k/(2\ln^2 p_k)$. Consequently, the primes $Q_i$ in $(N, 2N)$ partition the interval into composite gaps, each of maximal width $Q_i/(2\ln^2 Q_i) \leq N/\ln^2 N$. Similarly, the available odd primes $P < N$ have consecutive gaps strictly bounded by $N/\ln^2 N$ (the bound holds for all sufficiently large primes, and $N \geq 3275$ places us in the regime where Proposition 2 applies after the explicit verification in Dusart's thesis).

For any fixed $m$, consider the shifted arithmetic progression $S_m = \\{P + 2m \mid P < N \text{ is an odd prime}\\}$. If $m$ is missing, every term of $S_m$ that falls into $(N, 2N)$ lands inside one of the composite gaps between the $Q_i$. The configuration $S_m$ is rigid: increasing $m$ by 1 shifts every term of $S_m$ right by exactly 2. Because the prime gaps among the $P$'s and the composite gaps among the $Q_i$'s are both $O(N/\ln^2 N)$, the rigid shift suggests that only a limited number of translates can remain entirely hidden inside the composite regions.

We therefore *conjecture* that the number of such missing values satisfies $|U| \leq \ln^2 N$. (This is precisely the statement of Hypothesis 1.) If true, then

$$
|U| = (N-3) - |D_N| \leq \ln^2 N < \ln^2(2N)
$$

for $N \geq 3275$, which yields $G(N) > 0$. The rigorous justification of this upper bound on $|U|$ remains open and constitutes the only missing piece of the density argument.

**Remark.** The threshold $N = 3275$ arises directly from Proposition 1 (Théorème 1.9 of [[Dus98]](#references), p. 35), which guarantees a prime in every interval $(x, x + x/(2\ln^2 x)]$ for $x \geq 3275$. This theorem is itself a consequence of Proposition 2 (Proposition 1.10 of [[Dus98]](#references), p. 34), which bounds consecutive prime ratios for $p_k \geq p_{463} = 3299$, together with a finite verification for primes in $[3275, 3299]$. The key insight is that Dusart's short-interval guarantee forces the primes $Q \in (N, 2N)$ to be distributed densely enough-with gaps no larger than $N/\ln^2 N$-that the set $D_N$ of achievable half-differences is *conjectured* to be nearly full, leaving fewer than $\ln^2(2N)$ missing values. Steps 1--3 are rigorous; the conjectured step is the upper bound $|U| \leq \ln^2 N$ in Step 4.

### Proof of Theorem 3: Conditional Variant Goldbach Conjecture

**Proof.** By Theorem 1 and Proposition 1 (together with Lemma 1), it suffices to show that for every $N \geq 4$, there exists $M \in [1, N-3]$ such that both $P = N - M$ and $Q = N + M$ are prime. Equivalently, we must show $C_N \cap D_N \neq \emptyset$. We consider three cases.

#### Case 1: $N \geq 3275$

Assuming Hypothesis 1 (i.e., $G(N) > 0$), Corollary 1 gives

$$
|D_N| > (N-3) - \log^2(2N).
$$

The number of "bad" $M$-values (those in $\\{1, \ldots, N-3\\}$ but not in $D_N$) is therefore fewer than $\log^2(2N)$.

The candidate set $C_N$ has cardinality $|C_N| = \pi(N-1) - 1$ (excluding $p=2$). By Proposition 3(3),

$$
\pi(N) \geq \frac{N}{\ln N - 1} \quad \text{for } N \geq 5393.
$$

For $N \geq 3275$, we have $|C_N| \geq N/(\ln N + 2) > \log^2(2N)$, since the left side grows as $N/\log N$ while the right side grows as $\log^2 N$. (The inequality can be verified numerically at $N = 3275$.) Therefore $|C_N|$ strictly exceeds the number of bad $M$-values. By the pigeonhole principle [[Rit14]](#references), at least one element of $C_N$ must lie in $D_N$, giving $C_N \cap D_N \neq \emptyset$. Lemma 1 then yields the partition.

#### Case 2: $4 \leq N \leq 12$ (Base Cases)

We verify these manually (all $M$-values listed for $D_N$ are restricted to $[1, N-3]$):  
- **$N=4$** ($2N=8$): $C_4 = \\{1\\}$ (from $P=3$). $D_4 = \\{1\\}$ (from pair $(3,5)$). Intersection: $\\{1\\}$. Partition: $8 = 3+5$. $\checkmark$  
- **$N=5$** ($2N=10$): $C_5 = \\{2\\}$ (from $P=3$). $D_5 = \\{2\\}$ (from $(3,7)$). Intersection: $\\{2\\}$. Partition: $10 = 3+7$. $\checkmark$  
- **$N=6$** ($2N=12$): $C_6 = \\{3,1\\}$ (from $P \in \\{3,5\\}$). $D_6 = \\{1,2,3\\}$ ($M=4$ excluded as $>3$). Intersection: $\\{1,3\\}$. Partition: $12 = 5+7$. $\checkmark$  
- **$N=7$** ($2N=14$): $C_7 = \\{4,2\\}$. $D_7 = \\{3,4\\}$ ($M=5$ excluded as $>4$). Intersection: $\\{4\\}$. Partition: $14 = 3+11$. $\checkmark$  
- **$N=8$** ($2N=16$): $C_8 = \\{5,3,1\\}$. $D_8 = \\{2,3,4,5\\}$. Intersection: $\\{3,5\\}$. Partition: $16 = 3+13$. $\checkmark$  
- **$N=9$** ($2N=18$): $C_9 = \\{6,4,2\\}$. $D_9 = \\{2,4\\}$. Intersection: $\\{2,4\\}$. Partition: $18 = 5+13$. $\checkmark$  
- **$N=10$** ($2N=20$): $C_{10} = \\{7,5,3\\}$. $D_{10} = \\{3,7\\}$. Intersection: $\\{3,7\\}$. Partition: $20 = 3+17$. $\checkmark$  
- **$N=11$** ($2N=22$): $C_{11} = \\{8,6,4\\}$. $D_{11} = \\{6,8\\}$. Intersection: $\\{6,8\\}$. Partition: $22 = 3+19$. $\checkmark$  
- **$N=12$** ($2N=24$): $C_{12} = \\{9,7,5,1\\}$. $D_{12} = \\{1,5,7\\}$. Intersection: $\\{1,5,7\\}$. Partition: $24 = 5+19$. $\checkmark$  
All base cases hold.

#### Case 3: $13 \leq N \leq 3274$

For this range, we rely on computational verification. Our experiments (Section 4, Table 1) confirm that $G(N) > 0$ for all $N \in [4, 2^{14}] = [4, 16384]$, which includes the entire range $[13, 3274]$.

Since $G(N) > 0$ implies $|D_N| > (N-3) - \log^2(2N)$, and $|C_N| > \log^2(2N)$ for these values of $N$, the same pigeonhole argument (combined with Lemma 1) ensures $C_N \cap D_N \neq \emptyset$.

Additionally, we have verified *directly* for each $N \in [4, 2^{14}]$ that at least one valid Goldbach partition exists (i.e., we computed explicit partitions), confirming the conjecture holds.

#### Conclusion

Combining Cases 1--3, the conjecture holds for all $N \geq 4$. Since $N \geq 4$ corresponds to $2N \geq 8$, every even integer $\geq 8$ is the sum of two distinct primes.

**Remark (Computational Verification).** Our implementation verified the existence of Goldbach partitions for all even integers up to $2 \times 2^{14} = 32{,}768$, providing additional empirical confirmation of Theorem 3.

---  

## 6. Conclusion and Discussion

We have developed a geometric and combinatorial framework that reduces the distinct-prime Goldbach conjecture to a single density estimate---the Density Hypothesis (Hypothesis 1)---supported by computation. The framework combines a novel geometric reformulation via nested squares and semiprime areas (Theorem 1), a rigorous partial analysis of $D_N$ using explicit results from Dusart's doctoral thesis [[Dus98]](#references) (Steps 1--3), and computational verification for $4 \leq N \leq 2^{14}$. Theorem 3 shows that Hypothesis 1, together with finite verification, implies the full result.

### Summary of contributions

Theorem 1 establishes that the distinct-prime Goldbach variant is equivalent to finding, for each $N \geq 4$, a nested square configuration with semiprime area. Hypothesis 1 posits that for $N \geq 3275$, the gap function $G(N) = \log^2(2N) - ((N-3) - |D_N|) > 0$, ensuring $D_N$ is densely populated. The rigorous Steps 1--3 establish $|D_N| \geq \ln^2 N$; the conjectured Step 4 strengthens this to $(N-3) - |D_N| < \ln^2(2N)$. Together with the pigeonhole principle and Lemma 1, this yields Theorem 3: conditionally, every even integer $\geq 8$ is the sum of two distinct primes.

### Key insights

The threshold $N = 3275$ emerges from Proposition 1 (Théorème 1.9 of [[Dus98]](#references)), which guarantees primes in intervals of length $x/(2\log^2 x)$ for $x \geq 3275$. This prime density is precisely what is needed to establish Steps 1--3. The conjectured Step 4---that the number of missing $M$-values is at most $\ln^2 N$---requires controlling how shifted prime configurations $S_m = \\{P + 2m\\}$ interact with the composite gaps in $(N, 2N)$. The pigeonhole mechanism in Theorem 3 is clean: the number of candidate primes $P < N$ (namely $\pi(N-1) - 1$) exceeds the number of bad $M$-values (fewer than $\log^2(2N)$ under the hypothesis), forcing at least one successful Goldbach partition (via Lemma 1).

The interplay between computation and theory is noteworthy. Computational exploration revealed the empirical pattern $G(N) > 0$, which guided the theoretical analysis. The framework identifies the precise point where current methods fall short: Step 4 requires a bound on $|U|$ that goes beyond what short-interval prime results alone can deliver.

### Methodological contributions

Beyond the conditional result, this work demonstrates three methodological points. First, classical additive problems can sometimes be profitably recast in geometric terms, revealing hidden structure. Second, the gap function $G(N)$ provides a quantitative diagnostic-a "distance from counterexample"-whose behaviour offers structural insight and isolates the precise step that remains open. Third, Dusart's refinement [[Dus98]](#references), a result from modern analytic number theory, delivers the rigorous content of Steps 1--3 and is precisely calibrated to the threshold $N = 3275$.

### Relation to the classical Goldbach conjecture

Our framework addresses the variant requiring *distinct* primes, thus excluding $4 = 2+2$ and $6 = 3+3$. The geometric construction inherently demands $P \neq Q$ (i.e., $M \geq 1$). Extending to $P = Q$ ($M = 0$) would require new ideas.

### Open questions

Several natural questions remain. Can Step 4 of the density argument be established rigorously, thereby proving Hypothesis 1? This would require a tight upper bound on the number of $m$-values for which no straddling prime pair has half-difference $m$---a problem related to the distribution of prime pairs with prescribed differences. Can one improve the conjectured bound $|D_N| > (N-3) - \log^2(2N)$ to $|D_N| > (N-3) - C \log N$ for some constant $C$? What is the exact asymptotic behaviour of $G(N)$? Can the geometric framework accommodate $P = Q$ (the case $M = 0$), thereby addressing the full classical Goldbach conjecture? Finally, can similar geometric reformulations illuminate other additive problems, such as the ternary Goldbach conjecture or Waring's problem?

---  

## Acknowledgment

The author is sincerely grateful to Iris, Marilin, Sonia, Yoselin, Arelis, Anissa, Liuva, Yudit, Gretel, Gema, and Blaquier, as well as Israel, Arderi, Juan Carlos, Yamil, Alejandro, Aroldo, Yary, Reinaldo, Alex, Emmanuel, and Michael for their constant support. Whether through encouragement, stimulating conversations, practical assistance, or simply being present during challenging moments, their contributions have played an important role in bringing this work to completion.

---  

## References  

**[Gol43]** Goldbach, Christian. Lettre XLIII. In: Correspondance mathématique et physique de quelques célèbres géomètres du XVIIIème siècle, edited by P. H. Fuss, volume 1, pages 125-129. Imperial Academy of Sciences, St. Petersburg, 1843. (letter to Leonhard Euler) (in German).  

**[Oli14]** Oliveira e Silva, Tomás, Herzog, Siegfried, and Pardi, Silvio. Empirical verification of the even Goldbach conjecture and computation of prime gaps up to $4 \cdot 10^{18}$. *Mathematics of Computation*, 83(288):2033-2060, 2014. DOI: [10.1090/S0025-5718-2013-02787-1](https://doi.org/10.1090/S0025-5718-2013-02787-1).  

**[Veg25]** Vega, Frank. Experimental Results on Goldbach's Conjecture. 2025. Available at: [https://github.com/frankvegadelgado/goldbach](https://github.com/frankvegadelgado/goldbach). Accessed: 2025-11-14.  

**[Dus98]** Dusart, Pierre. Autour de la fonction qui compte le nombre de nombres premiers. 1998. Available at: [https://www.unilim.fr/pages_perso/pierre.dusart/Documents/T1998_01.pdf](https://www.unilim.fr/pages_perso/pierre.dusart/Documents/T1998_01.pdf). Accessed: 2025-11-14. PhD thesis, Université de Limoges.  

**[Rit14]** Rittaud, Benoît and Heeffer, Albrecht. The Pigeonhole Principle, Two Centuries before Dirichlet. *The Mathematical Intelligencer*, 36(2):27-29, 2014. DOI: [10.1007/s00283-013-9389-1](https://doi.org/10.1007/s00283-013-9389-1).  

---  

**MSC (2020):** 11P32 (Goldbach-type theorems; other additive questions involving primes), 51M15 (Geometric constructions in real or complex geometry), 11A25 (Arithmetic functions; related numbers; inversion formulas)  

---  

**Documentation**  
Available as PDF at *[Geometric Insights into the Goldbach Conjecture](https://www.preprints.org/manuscript/202511.0701/v5)*.
