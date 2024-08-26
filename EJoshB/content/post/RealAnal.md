---
title: 'Introductory Real Analysis and Topology Notes'
author: "Joshua Bautista"
date: 2024-08-26T22:37:00+08:00
categories:
  - Math
tags:
  - Higher Math
---
This was written from the perspective of a highschool math oly student, please don't expect anything too concrete.
## Setup and Definitions

A metric space is defined like groups are, over some set of points \(M\) and some distance function \(d\) called a *metric*. Formally \( d: M \times M \mapsto \mathbb{R}^+\) Any metric space has the following conditions for \(x,y,z\in M\):

- \(d(x,y) \geq 0\) with equality at \(x=y\)
- \(d(x,y) = d(y,x)\)
- \(d(x,y) \leq d(x,z) + d(z,y)\), so the triangle inequality holds.

The following are a list of definitions.

**A neighborhood**: For \(x \in M\) and real \(r\), the set of all points \(y\) such that \(d(x,y) < r\). This is denoted by \(M_r(x)\) and is called the \(r\)-neighborhood of \(x\).

**Convergence**: Given a sequence \(\{x_n\}_{n\geq1}\) in \(M\), we say that it converges to some point \(x\) if for every \(\epsilon>0\), \(d(x,x_n) < \epsilon\) for all sufficiently large \(n\). We can write \(\lim_{n \to \infty}x_n =x\).

**Limit Point**: A limit point is a point \(x \in M\) such that every neighborhood of \(x\) is nonempty. 

**Open**: A subset \(K \subseteq M\) is called *open* if every point in \(K\) has some neighborhood.

**Closed**: A subset \(K \subseteq M\) is called *closed* if for every converging sequence \((x_n)\) in \(K\), their limit is also in \(K\). In particular, every limit point of \(K\) is a point in \(K\). If the converse holds too then \(K\) is *perfect.*