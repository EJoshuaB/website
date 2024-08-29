---
title: 'Introductory Real Analysis and Topology Notes'
author: "Joshua Bautista"
date: 2024-08-26T22:37:00+08:00
categories:
  - Math
tags:
  - Higher Math
---
Simply notes from an oly guy.
## Metric Spaces

A metric space is defined like groups are, over some set of points \(M\) and some distance function \(d\) called a *metric*. Formally \(d: M \times M \mapsto \mathbb{R}_{\geq 0}\) Any metric space has the following conditions for \(x,y,z\in M\):

- \(d(x,y) \geq 0\) with equality at \(x=y\)
- \(d(x,y) = d(y,x)\)
- \(d(x,y) \leq d(x,z) + d(z,y)\), so the triangle inequality holds.

Note that this is enough to imply that \(d\) is a continuous function in \(M\) by using the triangle inequality ‘on a line.’

---

The following are a list of definitions, for the most part they are intuitive by the name alone?

**A neighborhood (or a ball)**: For \(x \in M\) and real \(r\), the set of all points \(y\) such that \(d(x,y) < r\). This is denoted by \(M_r(x)\) and is called the \(r\)-neighborhood of \(x\). If there’s a difference to a ball I literally cannot tell.

**Convergence**: Given a sequence \(\{x_n\}_{n\geq1}\) in \(M\), we say that it converges to some point \(x\) if for every \(\epsilon>0\), \(d(x,x_n) < \epsilon\) for all sufficiently large \(n\). We can write \(\lim_{n \to \infty}x_n =x\).

**Open**: A subset \(A \subseteq M\) is called *open* if every point in \(K\) has some neighborhood contained entirely in \(M\). Note that \(K\) being a subset as one of the reasons this definition makes sense.

**Continuous**: A function \(f: M \to N\) is defined as continuous if for every \(p \in M\) and \(\epsilon >0\) there exists \(\delta > 0\) such that \(d_1(x,p)<\delta \implies d_2(f(x),f(p))<\epsilon\) where \(d_1\) and \(d_2\) are the respective distance functions.

From this we can note that \(\lim_{n\to \infty}f(x_n) = f(x)\). Furthermore if \(f\) if bijective and \(f^{-1}\) is *also continuous* then \(M \sim N\) are homeomorphic

**Cauchy Sequence**: A sequence \((x_n)_{n\geq 1}\) is *Cauchy* if \(d(x_m,x_n) < \epsilon\) for sufficiently large \(m,n\).

**Complete**: \(M\) is complete if every Cauchy sequence converges.

**Limit Point**: A limit point is a point \(x \in A\) such that every neighborhood of \(x\) is nonempty in \(A\). Additionally, any limit point can be thought of as the ‘limit of some converging sequence,’ hence the name. These definitions are equivalent because we can construct a converging sequence from the first definition.

**Closed**: A subset \(A \subseteq M\) is called *closed* if for every converging sequence \((x_n)\) in \(A\), their limit is also in \(A\). In particular, every limit point of \(A\) is a point in \(A\). If the converse holds too then \(A\) is *perfect.*

**Bounded**: \(M\) is *bounded* if the distance between any two points in \(M\) is bounded. If \(M \subseteq N\) then it’s sufficient that for some point \(n \in N\) and any \(m \in M\) we have \(d(n,m) < C\) for constant \(C\).

**Totally Bounded**: \(M\) is *totally bounded* if \(M\) can be covered by finitely many \(\epsilon\)-neighborhoods for any epsilon. In particular, this implies \(M\) is bounded by the triangle inequality.

**Dense**: \(N \subset M\) is dense if every point in \(M\) is either in \(N\) or a limit point of \(N\). 

---

### Theorems and all that pt.1

From our definition of an open set, we can actually arrive at an equivalent definition of continuous

> \(f\) is a continuous function iff every open set’s preimage is open.
> 
- If we have continuity then for every open set it is sufficient to consider the neighborhood of an arbitrary point, and noting the preimage of that neighborhood is also inside the open set.
- If we have the fact that every open set’s preimage is open then consider the preimage of a neighborhood of some point. This is also a neighborhood by the assumption and since this works for any arbitrary point this implies continuous.

> Open and closed are two sides of the same coin. In particular, \(A \subseteq M\) is open iff it’s complement \(B = M/A\) is closed.
> 

By name this is intuitive, but by the definitions this is harder to see. The proof one way can easily be backtracked to show the other, so we will show that if \(A\) is open then \(B\) is closed.

Let \(x\) be a limit point of \(B\). FTSOC assume \(x \in A\), then \(\exists \epsilon\) such that \(N_{\epsilon}(x) \subset A\), but this contradicts the fact that \(x\) is a limit point of \(B\), so every limit point of \(B\) is in \(B\). We are done.

![OpenClosed](/OpenClosed.png)

> Banach Fixed Point Theorem: If \(M\) is a complete metric, then any continuous function \(T: M \to M\) such that \(d(T(x),T(y)) \leq qd(x,y)\) for some fixed \(q \in [0,1)\) and all \((x,y) \in M^2\) has exactly one fixed point.
> 

First note that there is at most 1 fixed point, because otherwise their distance would be invariant under \(T\). Now for arbitrary \(x\) define the sequence \(x_1 = x\) and \(x_{n+1} = T(x_n)\) for all \(n \geq 1\). Note that

$$d(x_n, T(x_n)) = q^{n-1}d(x_1,T(x_1))$$

so \((x_n)\) is in fact Cauchy. Since \(M\) is complete this sequence converges. That point is our desired fixed point.

---

### Examples that I liked

**Example 1.** Prove that a function \(f: \mathbb{R} \to \mathbb{R}\) that is strictly increasing must be continuous at some point.

The idea is to considering some interval \([a,b]\). Heuristically, if \(f\) is strictly increasing and not continuous anywhere then there would be ‘too many instantaneous jumps to fit on a finite interval.  Assume FTSOC it’s not continuous anywhere. Take \(\delta_x < f(y) - f(x)\) for every \(y > x\) where \(\delta_x\) is maximal. 

---

## Topological Spaces

Imagine we take metric spaces, and throw out the metric 🤯. A topology \(\Gamma\) is defined over a set of points \(X\) as essentially a set of open sets that follow the property:

- \(X\) and the empty set are in \(\Gamma\)
- the union of any subset of \(\Gamma\) is in \(\Gamma\)
- the intersection of any finite subset of \(\Gamma\) is in \(\Gamma\)

For this reason, our definition of a continuous function, closed sets and homeomorphic are the same.

---

**Hausdorff**: A topological space \(X\) is *Hausdorff* if any two points in \(X\) have some non-intersecting open neighborhoods.

**Subspace**: We can define a subspace \(S \subseteq X\) by taking \(K \cap S\) for \(K \subseteq X\) as the open subsets.

**Connected**: A space is *connected* if \(\exists\) nontrivial open sets that are closed. Define disconnected similarly.

**Path**: A path is a continuous function between two points, in particular we take \(f: [a,b] \to X\) for some non-trivial interval. Notably, a space is *path connected* if any two points have a path between them.

**Homotopy**: A path homotopy on \(f,g: [a,b] \to X\) is a continuous function \(\mathcal{P}: [a,b] \times [a,b] \to X\) on the space between the two paths. In particular \(\mathcal{P}(0,x) \in f\) and \(\mathcal{P}(x,0) \in g\). 

![PathHomotopy](/PathHomotopy.png)

**Simply Connected**: A space is simply connected if any two paths are homotopic.

**Basis**: A basis of a topological is a set of open sets, of which every other open set is the union of some.