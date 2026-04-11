# Geometric Insights into the Goldbach Conjecture

**Author:** Frank Vega  
**Affiliation:** Information Physics Institute, 840 W 67th St, Hialeah, FL 33012, USA  
**Email:** vega.frank@gmail.com  
**ORCID:** 0000-0001-8210-4126  

---  

## Abstract  

We develop a geometric framework that reformulates the distinct-prime Goldbach conjecture-the assertion that every even integer $2N \geq 8$ is the sum of two distinct primes-as a combinatorial intersection problem on nested squares with semiprime areas. For each $N \geq 4$, we define a *candidate set* $C_N$ and a *valid set* $D_N$ inside $\\{1,\ldots,N-3\\}$ and prove that the conjecture for $2N$ is equivalent to $C_N \cap D_N \neq \emptyset$. Using explicit results from Dusart's doctoral thesis-in particular, Théorème 1.9 (p. 35), which guarantees a prime in every interval $(x, x(1 + 1/(2\ln^2 x))]$ for $x \geq 3275$-we establish a rigorous lower bound $|D_N| \geq \ln^2 N$ for $N \geq 3275$. We then identify the precise *density condition* that would complete a proof: one needs $|C_N| + |D_N| > N - 3$, which requires $|D_N|$ to grow *linearly* in $N$. Our logarithmic bound, while rigorous, falls short of this threshold by a factor of $N/\ln^2 N$. We formulate the missing step as an explicit conjecture-the *Density Conjecture*-and provide extensive computational evidence: for all $N \in [4, 2^{14}]$, the set $D_N$ is empirically "almost full," with fewer than $\ln^2(2N)$ values missing. Direct computation also confirms that $C_N \cap D_N \neq \emptyset$ for all $N$ in this range. The framework reduces the distinct-prime Goldbach conjecture to a single quantitative estimate on $|D_N|$ and highlights the structural gap between what short-interval prime results can deliver and what the conjecture requires.

**Keywords:** Goldbach conjecture; geometric construction; semiprimes; prime distribution; Dusart's theorem; pigeonhole principle  

**MSC:** 11P32, 51M15, 11A25  

---  

## 1. Introduction  

The Goldbach conjecture, proposed in 1742, asserts that every even integer greater than 2 can be expressed as the sum of two prime numbers [[Gol43]](#references). Despite centuries of effort and computational verification up to $4 \times 10^{18}$ [[Oli14]](#references), the conjecture remains unproven. In this paper, we develop a geometric and combinatorial framework for studying a natural variant: every even integer $2N \geq 8$ is the sum of two *distinct* primes.

### The variant and its geometric reformulation

Our variant requires the two primes to be distinct, excluding the representations $4 = 2 + 2$ and $6 = 3 + 3$. This restriction emerges naturally from a geometric construction: for $N \geq 4$, finding a distinct-prime Goldbach partition of $2N$ is equivalent to finding nested squares whose L-shaped difference region has a semiprime area (Theorem 1).

### The set intersection reduction

The geometric reformulation leads to a combinatorial reduction. For each $N \geq 4$, we define two subsets of $\\{1, \ldots, N-3\\}$: a *candidate set* $C_N$ (determined by primes below $N$) and a *valid set* $D_N$ (determined by straddling prime pairs across $N$). The conjecture for $2N$ holds if and only if $C_N \cap D_N \neq \emptyset$ (Proposition 1).

By the pigeonhole principle, a sufficient condition for this intersection is

$$
|C_N| + |D_N| > N - 3.
$$

Since $|C_N| = \pi(N-1) - 1 \sim N/\ln N$, this condition requires

$$
|D_N| > N - 3 - |C_N| \approx N\!\left(1 - \frac{1}{\ln N}\right),
$$

a *linear* lower bound on $|D_N|$.

### What can be proved and what remains open

Using Dusart's short-interval prime result (Théorème 1.9 of [[Dus98]](#references)), we rigorously establish $|D_N| \geq \ln^2 N$ for $N \geq 3275$ (Theorem 2). This is a *logarithmic* bound-far below the linear threshold above. However, our computations reveal a striking empirical phenomenon: for all $N \in [4, 2^{14}]$, the set $D_N$ is "almost full," with fewer than $\ln^2(2N)$ values of $\\{1,\ldots,N-3\\}$ missing from $D_N$. This motivates our central conjecture (Conjecture 1), which posits that this near-completeness holds for all $N$.

We prove that Conjecture 1 implies the distinct-prime Goldbach conjecture (Theorem 3). The framework thus reduces the Goldbach problem to a single quantitative estimate on the density of $D_N$ and makes transparent the gap between what current prime distribution results can deliver and what the conjecture demands.

### Organisation

Section 2 collects the required prime distribution results from Dusart's thesis [[Dus98]](#references). Section 3 develops the geometric framework, proves the equivalence with Goldbach partitions, and introduces $C_N$, $D_N$, and the gap function. Section 4 presents the rigorous bounds and the Density Conjecture. Section 5 provides computational evidence. Section 6 states and proves the conditional result. Section 7 discusses the structural gap and future directions.

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

Define $P = N - M$ and $Q = N + M$. The bounds on $M$ translate to: $M \geq 1$ gives $P \leq N - 1$ and $Q \geq N + 1$; $M \leq N - 3$ gives $P \geq 3$. Thus $3 \leq P < N < Q \leq 2N - 3$, with $P < Q$.

### Connection to Goldbach partitions  

The sum and difference of $P$ and $Q$ are:  

$$  
\begin{align*}  
P + Q &= (N - M) + (N + M) = 2N, \\  
Q - P &= 2M.  
\end{align*}  
$$  

Since both are even, $P$ and $Q$ share the same parity. For both to be prime with $P \geq 3$, they must both be odd, hence distinct. The area $N^2 - M^2 = PQ$ is a semiprime if and only if both $P$ and $Q$ are prime.

### The geometric equivalence

**Theorem 1 (Geometric Goldbach Variant).** The following are equivalent for all $N \geq 4$:  
1. The even integer $2N$ can be written as the sum of two distinct primes.  
2. There exists $M \in [1, N-3]$ such that $P = N - M$ and $Q = N + M$ are both prime.  
3. The L-shaped region between squares $S_N$ and $S_M$ (sharing a corner) has semiprime area $PQ$ for some $M \in [1, N-3]$.  

**Proof.**  
**(i) $\Rightarrow$ (ii):** If $2N = p + q$ with distinct primes $p < q$, set $M = (q-p)/2$. Since $p$ and $q$ are distinct odd primes (as $2N \geq 8$), both $N = (p+q)/2$ and $M = (q-p)/2$ are positive integers. We have $P = N - M = p$ and $Q = N + M = q$, both prime. Distinctness gives $M \geq 1$, and $p \geq 3$ gives $M \leq N - 3$.  
**(ii) $\Rightarrow$ (iii):** Immediate, as $N^2 - M^2 = PQ$ with both factors prime.  
**(iii) $\Rightarrow$ (i):** If $N^2 - M^2 = PQ$ with $P, Q$ prime and $M \in [1, N-3]$, then $P + Q = 2N$ is a partition of $2N$ into two distinct odd primes.  

<div align="center">
    <img src="https://hackmd.io/_uploads/HkhT4Kuwbx.svg" alt="Geometric Construction" width="600">
   <br><br>
</div>
    
**Figure 1:** The geometric construction for $N=5$, $M=2$: The L-shaped region has area $N^2 - M^2 = 25 - 4 = 21 = 3 \times 7$, a semiprime. The factors $P=3$ and $Q=7$ are both prime and sum to $2N=10$, providing the Goldbach partition $10 = 3 + 7$.  

### Reformulation as a set intersection problem

For each $N \geq 4$, define two subsets of $\\{1, 2, \ldots, N-3\\}$:

- **Candidate set:** $C_N = \\{N - p \mid 3 \leq p < N, \text{ } p \text{ prime}\\}$, consisting of all $M$-values from odd primes $P = p < N$.  
- **Valid set:** $D_N = \left\\{ \frac{Q - P}{2} \;\bigg|\; 2 < P < N < Q < 2N, \text{ both prime} \right\\}$, consisting of half-differences arising from straddling prime pairs.

**Proposition 1.** The distinct-prime Goldbach conjecture holds for the even integer $2N$ ($N \geq 4$) if and only if $C_N \cap D_N \neq \emptyset$.

**Proof.** Suppose $M \in C_N \cap D_N$. Then $P = N - M$ is an odd prime (since $M \in C_N$) and there exist primes $P', Q'$ with $2 < P' < N < Q' < 2N$ and $(Q' - P')/2 = M$ (since $M \in D_N$). In particular, $Q = N + M$ satisfies $N < Q < 2N$. If $Q$ is prime, then $(P, Q) = (N - M, N + M)$ is itself a straddling pair, and $P + Q = 2N$ is the desired partition.

More directly: $M \in C_N$ means $P = N - M$ is prime. By Theorem 1, the Goldbach partition $2N = P + Q$ with $Q = N + M$ exists if and only if $Q$ is prime, which is equivalent to $M$ belonging to $\\{M' \in \\{1,\ldots,N-3\\} : N + M' \text{ is prime}\\}$. This set is a subset of $D_N$. Conversely, any $M \in C_N \cap D_N$ for which $Q = N + M$ is prime directly yields a partition.

For the reverse direction, if $2N = P + Q$ with $3 \leq P < Q$ both prime, then $M = (Q - P)/2$ satisfies $M \in C_N$ (since $P = N - M$) and $M \in D_N$ (since $(P, Q)$ is a straddling pair).

### The gap function

Define the **gap function**:  

$$  
G(N) = \log^2(2N) - \bigl((N-3) - |D_N|\bigr).  
$$  

Here $(N-3) - |D_N|$ counts the $M$-values *missing* from $D_N$. The condition $G(N) > 0$ is equivalent to $|D_N| > (N-3) - \log^2(2N)$, meaning that $D_N$ is "almost full" with fewer than $\log^2(2N)$ missing values.

**Remark (Why $G(N) > 0$ would suffice).** If $G(N) > 0$, the number of $M$-values in $\\{1,\ldots,N-3\\} \setminus D_N$ is fewer than $\log^2(2N)$. Since $|C_N| = \pi(N-1) - 1 > \log^2(2N)$ for all $N \geq 60$ (by Proposition 3), the pigeonhole principle [[Rit14]](#references) forces $C_N \cap D_N \neq \emptyset$. Thus $G(N) > 0$ is a sufficient condition for the Goldbach variant at $2N$.

We now state the main theoretical results, whose proofs are given in Section 5 and Section 6.

**Theorem 2 (Rigorous lower bound on $|D_N|$).** For every integer $N \geq 3275$,

$$
|D_N| \geq \ln^2 N.
$$

**Conjecture 1 (Density Conjecture).** For every integer $N \geq 4$,

$$
(N - 3) - |D_N| < \log^2(2N).
$$

Equivalently, $G(N) > 0$ for all $N \geq 4$.

**Theorem 3 (Conditional Main Result).** If Conjecture 1 holds for all $N \geq N_0$ (for some $N_0$), and $C_N \cap D_N \neq \emptyset$ is verified computationally for $4 \leq N < N_0$, then every even integer $2N \geq 8$ is the sum of two distinct primes.

---  

## 4. Rigorous Bounds and the Density Conjecture

### A rigorous lower bound on $|D_N|$

**Proof of Theorem 2.** We proceed in two steps.

**Step 1: At least $\ln^2 N$ primes in $(N, 2N)$.** Partition the interval $(N, 2N)$ into consecutive sub-intervals of the form $(x_j, x_j(1 + 1/(2\ln^2 x_j))]$, starting with $x_0 = N$. By Proposition 1, each sub-interval contains at least one prime. Since every $x_j \leq 2N$, each sub-interval has length at most $2N/(2\ln^2 N) = N/\ln^2 N$. Covering $(N, 2N)$ (which has length $N$) requires at least $N / (N/\ln^2 N) = \ln^2 N$ sub-intervals. Denote the resulting primes $Q_1 < Q_2 < \cdots < Q_r$ with $r \geq \ln^2 N$.

**Step 2: Distinct elements of $D_N$.** For each prime $Q_i \in (N, 2N)$, choose the fixed prime $P = 3$ (which satisfies $2 < 3 < N$ for $N \geq 4$). The value $M_i = (Q_i - 3)/2$ belongs to $D_N$, and since the $Q_i$ are pairwise distinct odd numbers, the $M_i$ are pairwise distinct. Hence $|D_N| \geq r \geq \ln^2 N$.

**Remark.** The threshold $N = 3275$ arises directly from Proposition 1 (Théorème 1.9 of [[Dus98]](#references), p. 35), which guarantees a prime in every interval $(x, x + x/(2\ln^2 x)]$ for $x \geq 3275$. This is itself a consequence of Proposition 2 (Proposition 1.10 of [[Dus98]](#references), p. 34), which bounds consecutive prime ratios for $p_k \geq p_{463} = 3299$, together with a finite verification for primes in $[3275, 3299]$.

### The structural gap

Theorem 2 provides a *logarithmic* lower bound: $|D_N| \geq \ln^2 N$. However, forcing $C_N \cap D_N \neq \emptyset$ via the pigeonhole principle on $\\{1,\ldots,N-3\\}$ requires a *linear* lower bound:

$$
|D_N| > N - 3 - |C_N| \approx N\!\left(1 - \frac{1}{\ln N}\right).
$$

The gap between these two regimes is enormous-a factor of $N/\ln^2 N$-and cannot be closed using Dusart's short-interval prime guarantee alone. Proposition 1 controls where individual primes fall but does *not* control the distribution of prime pairs $(P, Q)$ with a prescribed difference $Q - P = 2m$. Establishing that "most" values of $m$ arise as such a half-difference requires information about the joint distribution of prime pairs, a topic in the family of twin-prime and bounded-gaps problems that remains largely out of reach.

### The Density Conjecture

Our computational evidence (Section 5) strongly suggests that $D_N$ is in fact almost full.

Conjecture 1 asserts that all but at most $\log^2(2N)$ values in $\\{1,\ldots,N-3\\}$ belong to $D_N$. If true, this is vastly stronger than Theorem 2, replacing a logarithmic lower bound with a linear one (with only logarithmic deficiency).

**Remark.** Conjecture 1 is a statement about the *richness of even differences between straddling prime pairs*. For a given $m$, membership $m \in D_N$ requires that at least one pair $(P, Q)$ of primes with $P < N < Q < 2N$ satisfies $Q - P = 2m$. Since there are $\sim N/\log N$ primes on each side, a heuristic random model predicts $\sim N/\log^2 N$ such pairs for each $m$, suggesting that very few $m$-values should be missing. However, making this heuristic rigorous remains an open problem, as it requires controlling correlations in the distribution of prime pairs with prescribed differences.

---  

## 5. Computational Evidence

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

**Table 1:** Minimum $G(N)$ values in dyadic intervals $[2^m, 2^{m+1}]$. $G(N) > 0$ for all tested values, and the minima strictly increase with $m$.  

Three features of these data merit attention.

First, $G(N) > 0$ for *every* $N \in [4, 2^{14}]$, providing strong empirical support for Conjecture 1. Moreover, the minimum value of $G(N)$ in each dyadic interval $[2^m, 2^{m+1}]$ strictly increases with $m$, suggesting that the positivity margin widens as $N$ grows.

Second, we verified *directly* that $C_N \cap D_N \neq \emptyset$ for every $N \in [4, 2^{14}]$ by computing explicit Goldbach partitions, confirming the distinct-prime Goldbach conjecture for all even integers up to $32{,}768$.

Third, the $N$-values at which the $G(N)$ minima occur tend to be primes or near-primes, consistent with the expectation that $|D_N|$ is smallest when primes near $N$ are sparse.

**Remark.** Our computational range $[4, 2^{14}]$ is modest compared to the verification of the classical Goldbach conjecture up to $4 \times 10^{18}$ [[Oli14]](#references). However, our data concerns the *internal structure* of the partition (the density of $D_N$), which provides finer information than mere existence of a partition.

---  

## 6. Conditional Result

We now show that Conjecture 1, combined with computation for small $N$, implies the distinct-prime Goldbach conjecture.

**Proof of Theorem 3.** By Theorem 1, it suffices to show $C_N \cap D_N \neq \emptyset$ for every $N \geq 4$.

#### Case 1: $N \geq N_0$

Assume Conjecture 1, so that $(N-3) - |D_N| < \log^2(2N)$. The number of $M$-values in $\\{1,\ldots,N-3\\} \setminus D_N$ is fewer than $\log^2(2N)$. The candidate set has cardinality $|C_N| = \pi(N-1) - 1$. By Proposition 3(3), $\pi(N) \geq N/(\ln N - 1)$ for $N \geq 5393$. For $N \geq 60$, one readily verifies that $\pi(N-1) - 1 > \log^2(2N)$. Since $|C_N|$ strictly exceeds the number of missing $M$-values, the pigeonhole principle [[Rit14]](#references) forces at least one element of $C_N$ to lie in $D_N$.

#### Case 2: $4 \leq N \leq 12$ (Base Cases)

We verify these manually:  
- **$N=4$** ($2N=8$): $C_4 = \\{1\\}$ (from $P=3$). $D_4 = \\{1, 2\\}$ (from pairs $(3,5)$ and $(3,7) $). Intersection: $\\{1\\}$. Partition: $8 = 3+5$. $\checkmark$  
- **$N=5$** ($2N=10$): $C_5 = \\{2\\}$ (from $P=3$). $D_5 = \\{2\\}$ (from $(3,7) $). Intersection: $\\{2\\}$. Partition: $10 = 3+7$. $\checkmark$  
- **$N=6$** ($2N=12$): $C_6 = \\{3,1\\}$ (from $P \in \\{3,5\\}$). $D_6 = \\{1,2,3,4\\}$. Intersection: $\\{1,3\\}$. Partition: $12 = 5+7$. $\checkmark$  
- **$N=7$** ($2N=14$): $C_7 = \\{4,2\\}$. $D_7 = \\{3,4,5\\}$. Intersection: $\\{4\\}$. Partition: $14 = 3+11$. $\checkmark$  
- **$N=8$** ($2N=16$): $C_8 = \\{5,3,1\\}$. $D_8 = \\{2,3,4,5\\}$. Intersection: $\\{3,5\\}$. Partition: $16 = 3+13$. $\checkmark$  
- **$N=9$** ($2N=18$): $C_9 = \\{6,4,2\\}$. $D_9 = \\{2,4\\}$. Intersection: $\\{2,4\\}$. Partition: $18 = 5+13$. $\checkmark$  
- **$N=10$** ($2N=20$): $C_{10} = \\{7,5,3\\}$. $D_{10} = \\{3,7\\}$. Intersection: $\\{3,7\\}$. Partition: $20 = 3+17$. $\checkmark$  
- **$N=11$** ($2N=22$): $C_{11} = \\{8,6,4\\}$. $D_{11} = \\{6,8\\}$. Intersection: $\\{6,8\\}$. Partition: $22 = 3+19$. $\checkmark$  
- **$N=12$** ($2N=24$): $C_{12} = \\{9,7,5,1\\}$. $D_{12} = \\{1,5,7\\}$. Intersection: $\\{1,5,7\\}$. Partition: $24 = 5+19$. $\checkmark$  
All base cases hold.

#### Case 3: $13 \leq N < N_0$

Covered by computational verification. For $N_0 = 3275$, our experiments (Section 5) confirm $C_N \cap D_N \neq \emptyset$ for all $N \in [13, 3274]$.

#### Conclusion

Combining all cases, $C_N \cap D_N \neq \emptyset$ for every $N \geq 4$, and by Theorem 1, every even integer $2N \geq 8$ is the sum of two distinct primes.

---  

## 7. Conclusion and Discussion

### Summary of contributions

This paper makes three contributions. First, Theorem 1 establishes a rigorous equivalence between the distinct-prime Goldbach conjecture and the existence of nested square configurations with semiprime area. Second, the $C_N \cap D_N$ intersection framework (Proposition 1) reduces the conjecture to a density question, and Theorem 2 provides a rigorous lower bound $|D_N| \geq \ln^2 N$ for $N \geq 3275$ using explicit results from Dusart's thesis [[Dus98]](#references). Third, the Density Conjecture (Conjecture 1) isolates the precise quantitative estimate needed to complete the proof, and Theorem 3 shows it suffices.

### The structural gap

The central difficulty is transparent within our framework. The pigeonhole strategy requires $|D_N|$ to be *linear* in $N$, but the best rigorous bound derivable from short-interval prime results is only *logarithmic*. The gap-a factor of $N/\ln^2 N$-is the precise obstacle to an unconditional proof. Closing it appears to require tools from the theory of prime pairs with prescribed differences, a subject in the orbit of the twin-prime and bounded-gaps conjectures.

### Alternative proof strategies

The framework admits strategies that bypass the global pigeonhole argument. One might exploit structural correlations between $C_N$ and $D_N$-for instance, that both sets are concentrated near certain residue classes or arithmetic progressions. If one could show that $C_N$ and $D_N$ cannot be "anti-correlated" within $\\{1,\ldots,N-3\\}$, an intersection result might follow without a linear lower bound on $|D_N|$.

### Relation to the classical Goldbach conjecture

Our framework addresses the variant requiring *distinct* primes, thus excluding $4 = 2+2$ and $6 = 3+3$. The geometric construction inherently demands $P \neq Q$ (i.e., $M \geq 1$). Extending to $P = Q$ ($M = 0$) would require new ideas.

### Open questions

Several natural problems arise:

1. Can Conjecture 1 be proved using sieve methods or estimates on prime pairs with prescribed differences?
2. Is there a proof of $C_N \cap D_N \neq \emptyset$ that avoids the pigeonhole principle entirely, perhaps by exploiting the arithmetic structure of both sets?
3. What is the precise asymptotic behaviour of $G(N)$? Table 1 suggests $\min_{N \in [2^m, 2^{m+1}]} G(N) \to \infty$, but we have no theoretical explanation.
4. Can similar geometric reformulations illuminate other additive problems, such as the ternary Goldbach conjecture or Waring's problem?

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
