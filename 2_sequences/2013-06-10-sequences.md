#Hacker School Analysis Seminar - Sequences

##Attribution

Much of the content is closely adapted from [Elementary Analysis: The Theory of Calculus](http://books.google.com/books/about/Elementary_Analysis.html?id=ZDaSnKr_k5sC) by Kenneth Ross. This book, or others on mathematical analysis, should be consulted for further inquiry.

## Useful Properties

### Triangle Inequality

###Claim:
_$|a + b| \le |a| + |b|$ for all $a,b \in \mathbb{R}$._

####Proof:
See Ross text.

### Archimedean Property

#### Claim: 
_If $a>0$ and $b>0$, then there exists $n \in \mathbb{N}$ such that $na > b$._

In essence, this states that no matter how small of an $a$ and how large of a $b$ we choose, we can always find an integer multiple of $a$ that will exceed $b$.

#### Proof:

Suppose, by way of contradiction, that the Archimedean property fails. Then there exists $a>0$ and $b>0$ such that $na \le b$ for all $n in \mathbb{N}$. By definition, $b$ is then an upper bound on the set $S = \{na : n \in \mathbb{N}\}$. 

Using the completeness axiom, let $s_0 = \sup S$. Since $a > 0$, we have $s_0 < s_0 + a$, so $s_0 - a < s_0$. Since $s_0$ is the least upper bound of $S$, $s_0 - a$ cannot be an upper bound of $S$. This implies that there exists an $s = n_0 a \in S$ such that $s_0 - a < n_0 a$ for some $n_0 \in \mathbb{N}$. Adding $a$ to each side of the inequality, we get $s_0 < (n_0 + 1) a$. Since $n_0 + 1 \in \mathbb{N}$, $(n_0 +1) a \in S$, and so $s_0$ is not an upper bound for $S$. Contradiction. $\mathbb{QED}$.


### Denseness of $\mathbb{Q}$

#### Claim:
_If $a,b \in \mathbb{R}$ and $a<b$, then there exists a rational number $r \in \mathbb{Q}$ such that $a < r < b$._

#### Pseudo-Proof:

We need to show that $a < \frac{m}{n} < b$ for some $m,n \in \mathbb{N}$, where $n > 0$. Thus, we need

$$ an < m < bn $$

Since $b-a > 0$, the Archimedean property shows that there exists an $n \in \mathbb{N}$ such that $n(b-a) > 1$. Thus, $bn - an > 1$, and so it is _fairly evident_ that there exists an $m$ between $an$ and $bn$, so our claim holds. (Actually _proving_ that this $m$ exists is a bit more delicate, see page 24/25 in Ross for more detail.)

## Sequences

Formally, a _sequence_ is a function from $\{ n \in \mathbb{Z}: n \ge m\}$, where $m$ is usually 0 or 1, into $\mathbb{R}$. However, it is customary to write $s_n$ rather than $s(n)$, and is also convenient to write $(s_n)_{n=m}^{\infty}$, $(s_m, s_{m+1}, s_{m+2})$, or, when $m = 1$, $(s_n)_{n \in \mathbb{N}}$. 

### Examples (1)

(a). Consider the sequence $(a_n)_{n \in \mathbb{N}}$ where $a_n = \frac{1}{n^2}$. This is the sequence $(1, \frac{1}{4}, \frac{1}{9}, \frac{1}{16}, \frac{1}{25}, ...)$. Formally this is the function with domain $\mathbb{N}$ with value $\frac{1}{n^2}$ for each $n$. The _set_ of values is $\{1, \frac{1}{4}, \frac{1}{9}, \frac{1}{16}, \frac{1}{25}, ...\}$.

(b). Consider the sequence $(b_n)_{n = 0}^{\infty}$ where $b_n = (-1)^n$. The sequence is $(1,-1,1,-1,...)$, however its _set_ of values is $\{-1,1\}$.

It's important to distinguish between a sequence and its set of values, and we will always use parentheses $( \ )$ to signify a sequence and braces $\{ \ \}$ to signify a set.

(c). Consider the sequence $(c_n)_{n \in \mathbb{N}}$ where $c_n = (1 + \frac{1}{n})^n$. This is the sequence $(2, (\frac{3}{2})^2, (\frac{4}{3})^3, (\frac{5}{4})^4, ...)$, or approximately

$$ (2, 2.25, 2.3704, 2.4414, 2.4883, 2.5216, 2.5465, 2.5658, ...). $$

$c_{100}$ is approximately 2.7048, and $c_{1000}$ is approximately 2.7169.

(d.) Consider the sequence $(d_n)_{n \in \mathbb{N}}$ where $d_n = \pi^{n-1}$. This is the sequence $(\pi^0, \pi^1, \pi^2, \pi^3, ...)$, or approximately

$$ (0, 3.1416, 9.8696, 31.0063, ...). $$

$d_{100}$ is approximately $5.1878 \times 10^{49}$ and $d_{1000}$ causes an OverflowError in Python.

### Limits

The _limit_ of a sequence $(s_n)$ is a real number which the values $s_n$ are "close" to for large values of $n$. In example (a), the values are "close" to 0 for large $n$, and in example (c), the values are close to Euler's constant, $e$, for large $n$. However, example (b) doesn't seem to get close to any number, but instead jumps between $-1$ and $1$. As we'll see in the following definition, a _limit_ will require the sequence values to be close to the limit value for _all_ large $n$, so neither $1$ or $-1$ will be limits of $(c_n)$.

#### Definition (1):

A sequence $(s_n)$ of real numbers is said to _converge_ to the real number $s$ if and only if for every $\epsilon > 0$ there exists a number $N$ such that $|s_n - s| < \epsilon$ for all $n > N$.

#### Definition (2):

A sequence $(s_n)$ of real numbers is said to _diverge towards $\infty$_ if and only if for every $M \in \mathbb{R}$ there exists a number $N$ such that $s_n > M$ for all $n > N$.

#### Definition (3):

A sequence $(s_n)$ of real numbers is said to _diverge towards $-\infty$_ if and only if for every $M \in \mathbb{R}$ there exists a number $N$ such that $s_n < M$ for all $n > N$.

### Examples (2)

We will now prove a couple of the above examples (1).

(a.) We aim to prove that $\lim_{n \to \infty} a_n = 0$, so we must show that there exists $N in \mathbb{N}$ such that for all $n >N$, $|a_n - 0| < \epsilon$ for all $\epsilon > 0$.

Let $\epsilon > 0$ be given. Now, define $N = \left \lceil \frac{1}{\sqrt{\epsilon}} \right \rceil $. Then for all $n > N$, 

$$|a_n - 0| = a_n = \frac{1}{n^2} < \frac{1}{N^2} = \frac{1}{\left \lceil \frac{1}{\sqrt{\epsilon}} \right \rceil^2} \le \frac{1}{\left (\frac{1}{\sqrt{\epsilon}} \right )^2} = \frac{1}{\left (\frac{1^2}{\sqrt{\epsilon}^2} \right )} = \left( \sqrt{\epsilon} \right)^2 = \epsilon.$$

$\mathbb{QED}$.

The relevant function (in python) would be:

    from math import sqrt, ceil
    def example_a(epsilon):
        N = int(ceil(sqrt(epsilon)))
        return N

(d.) We aim to prove that $\lim_{n \to \infty} d_n$ diverges towards $\infty$, so we must show that for all $M \in \mathbb{R}$ their exists $N \in \mathbb{N}$ such that $d_n > M$ for all $n > N$.

Let $M \in \mathbb{R}$ be given, and note that if $M \le 1$ and we show that $d_n > 1$ for all $n \in \mathbb{N}$, then $d_n > M$ as well. So let $\hat{M} = \max(M,1)$, and define $N = \lceil \log_{\pi} \hat{M} \rceil $. Then for all $n > N$,

$$ d_n = \pi^n > \pi^N = \pi^{\lceil \log_{\pi} \hat{M} \rceil} \ge \pi^{ \log_{\pi} \hat{M} } = \hat{M} =  \max(M,1) \ge M. $$

$\mathbb{QED}$.

The relevant function (in python) would be:

    from math import pi, log, ceil
    def example_d(M):
        M = max(1,M)
        N = int(ceil(log(M,pi)))
        return N


### Exercises

(1) Write out the first five terms of the following sequences.

  (a). $a_n  = \frac{n}{n+1}$
  
  (b). $b_n = 2^{-n}$
  
  (c). $c_n = n!$
  
  (d). $d_n = 1 + \frac{2}{n}$
  
  (e). $e_n = \frac{6n^2+7}{4n^2 - 9}$
  
  (f). $f_n = (-1)^n n$
  
  (g). $g_n = \frac{n^3+4}{7n^2 - 13}$
  
  (h). $h_n = \sin(n \pi)$
  
  (i). $i_n = \frac{1}{n} \cos(n)$
  
  (j). $j_n = \cos(n)$

(2) For each sequence above, determine whether it converges, diverges to $\pm \infty$, or doesn't converge/diverge, and if so give it's limit. Proofs are not required.

(3) For each sequence above that converges (or diverges to $\pm \infty$), find the mathematical function for $N$ given $M$ or $\epsilon$.

(4) For each sequence above that converges (or diverges to $\pm \infty$), write a function in a programming language of your choice for $N$ given $M$ or $\epsilon$.

(4) For each sequence above that converges (or diverges to $\pm \infty$), prove that it converges to the limit (or diverges to $\pm \infty$).









