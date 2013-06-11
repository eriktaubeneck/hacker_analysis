#Hacker School Analysis Seminar - Sequences

##Attribution

Much of the content is closely adapted from [Elementary Analysis: The Theory of Calculus](http://books.google.com/books/about/Elementary_Analysis.html?id=ZDaSnKr_k5sC) by Kenneth Ross. This book, or others on mathematical analysis, should be consulted for further inquiry.

## Useful Properties

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

### Examples

(a). Consider the sequence $(a_n)_{n \in \mathbb{N}}$ where $a_n = \frac{1}{n^2}$. This is the sequence $(1, \frac{1}{4}, \frac{1}{9}, \frac{1}{16}, \frac{1}{25}, ...)$. Formally this is the function with domain $\mathbb{N}$ with value $\frac{1}{n^2}$ for each $n$. The _set_ of values is $\{1, \frac{1}{4}, \frac{1}{9}, \frac{1}{16}, \frac{1}{25}, ...\}$.

(b). Consider the sequence $(b_n)_{n = 0}^{\infty}$ where $b_n = (-1)^n$. The sequence is $(1,-1,1,-1,...)$, however its _set_ of values is $\{-1,1\}$.

It's important to distinguish between a sequence and its set of values, and we will always use parentheses $( \ )$ to signify a sequence and braces $\{ \ \}$ to signify a set.

(c). Consider the sequence $(c_n)_{n \in \mathbb{N}}$ where $c_n = (1 + \frac{1}{n})^n$. This is the sequence $(2, (\frac{3}{2})^2, (\frac{4}{3})^3, (\frac{5}{4})^4, ...)$, or approximately

$$ (2, 2.25, 2.3704, 2.4414, 2.4883, 2.5216, 2.5465, 2.5658, ...). $$

$c_{100}$ is approximately 2.7048, and $c_{1000}$ is approximately 2.7169.

### Limits

The _limit_ of a sequence $(s_n)$ is a real number which the values $s_n$ are "close" to for large values of $n$. In example (a), the values are "close" to 0 for large $n$, and in example (c), the values are close to Euler's constant, $e$, for large $n$. However, example (b) doesn't seem to get close to any number, but instead jumps between $-1$ and $1$. As we'll see in the following definition, a _limit_ will require the sequence values to be close to the limit value for _all_ large $n$, so neither $1$ or $-1$ will be limits of $(c_n)$.

#### Definition:

A sequence $(s_n)$ of real numbers is said to _converge_ to the real number $s$ if and only if for every $\epsilon > 0$ there exists a number $N$ such that $n>N$ such that $|s_n - s| < \epsilon$ for all $n > N$.














