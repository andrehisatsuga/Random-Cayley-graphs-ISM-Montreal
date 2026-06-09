## Cayley graphs

Given a group $\Gamma$, and a symmetric set $S\subseteq\Gamma$ (i.e. $x\in S\Rightarrow x^{-1}\in S$), the ==Cayley graph== $\operatorname{Cay}(\Gamma,S)$ is defined as follows:
$$V = \Gamma\,, \qquad E = \{\{x,y\}:xy^{-1}\in S\}$$
The ==random Cayley graph== $\operatorname{Cay}_p(\Gamma)$ is defined, given $0<p<1$,  as $\operatorname{Cay}(\Gamma, S)$ where each pair $\{s,s^{-1}\}$ ($s\neq e$) is included in $S$ independently at random with probability $p$. 

What is the typical behaviour of the clique number of $\operatorname{Cay}_p(\Gamma)$?

**Proposition** (Alon, Orlistky 1995): 
	There exists an absolute constant $C$ such that, for any group $\Gamma$ of order $N$, then $$\omega(\operatorname{Cay}_{\frac12}(\Gamma))\leq C(\log N)^2$$
Pf Sketch (...)
 
 

**Claim:** For any $A\subseteq\Gamma$, there exists $B\subseteq A$ such that: $$|B| = \Theta\big(\sqrt{|A|}\big)$$  $$|B^{-1}B|\geq \delta\cdot|B|^2$$where $\delta$ is an absolute constant.

To prove the Claim:
	We consider the multiplicative energy: For $X\subseteq\Gamma$,
		$$E(X)\coloneqq \#\{(x_1,x_2,x_3,x_4)\in X^4: x_1^{-1}x_2 = x_3^{-1}x_4\}$$
	For $q\in\Gamma$, let $r_X(q) = \#\{(x,y)\in X^2: q = x^{-1}y\}$ . Then
	$$E(X) = \sum_{q\in\Gamma}(r_X(q))^2\geq\frac{(\sum r_X(q))^2}{\#\{q:r_X(q)>0\}} = \frac{|X|^4}{|X^{-1}X|}$$
	If $E(X) = O(|X|^2)$, then $$|X^{-1}X|\geq\frac{|X|^4}{E(X)}\geq\frac{|X|^4}{C|X|^2} = \delta|X|^2$$
**Exercise:** Show that for any $A\subseteq\Gamma$, there exists $X\subseteq A$ such that $|X| = \Theta\big(\sqrt{|A|}\big)$, and $E(X) = O(|X|^2)$.

## Other results

Ben Green and Rob Morris showed that clique numbers of random Cayley graphs behave similar to random graphs $G(n,p)$, in the cyclic case $\Gamma = \mathbb{Z}/N\mathbb{Z}$: 

**Theorem** (Green 2005)   $\omega(\operatorname{Cay}_{\frac{1}{2}} (\mathbb{Z}/N\mathbb{Z})) = \Theta(\log N)$  w.h.p.
**Theorem** (Green, Morris 2015)   $\omega(\operatorname{Cay}_{\frac{1}{2}} (\mathbb{Z}/p\mathbb{Z})) = (2+o(1))(\log p)$  w.h.p.

The main theorem we will prove generalizes Green's result for arbitrary groups.

**Theorem** (Conlon, Fox, Pham, Yepremyan) 
	For any group $\Gamma$, the following holds with high probability: $$\omega(\operatorname{Cay}_p(\Gamma)) = O_p(\log N\log\log N)\qquad(\text{where }N=\Gamma)$$
## Proof of the main theorem

### Random entangled graphs

Given a coloring $c:E(K_n)\to [r]$, we consider the random graph $G_p(c)$ obtained by choosing to include each color class with probability $p$, independently. (i.e. take all edges of the chosen colors to be the edges of $G_p(c)$)

**Note:** The random Cayley graph is a random entangled graph, where we color each edge $\{x,y\}\in E(K_N)$ with the pair $\{xy^{-1}, yx^{-1}\}$. 
### $\Delta$-bounded colorings

A coloring is $\Delta$-bounded if every vertex is incident to no more than $\Delta$ many edges of the same color.

**Note:** The coloring associated to random Cayley graphs is 2-bounded: we can only have edges $\{x,y\}$, $\{x,z\}$ of the same color if $\{xy^{-1},yx^{-1}\} = \{xz^{-1},zx^{-1}\}$, which can only happen if $y=z$ or $y = xz^{-1}x$. 

In light of this, in order to prove the main theorem, it is enough to show the following:

**Theorem.** If $c$ is a $\Delta$-bounded coloring of $K_N$, then w.h.p. we have $$\omega(G_p(c)) = O_{p,\Delta}(\log N\log\log N)$$
To prove this theorem, we will use the first moment method together with the following counting lemma.

**Lemma.** There exists $C>0$ such that, for any $K>0$, and any $\Delta$-bounded coloring $c:E(K_N)\to [r]$, the number $M$ of subsets $A\subseteq \big[N\big]$ of size $n$, such that the number of colors in $K_N\big[A\big]$ is at most $Kn$, satisfies $$M\;\leq\; N^{C\Delta K\log N}\cdot(C\Delta K)^n$$ 