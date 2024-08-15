---
title: Bijections Are Funny
author: Joshua Bautista
date: '2024-08-12'
categories:
  - Math
tags:
  - Olympiad Problems
  - Combinatorics
  - ISL
---
A personal favorite style of problem of mine are problems that can seem very scary but admit pretty cute/short bijection solutions, so here's a short collection of a couple of them I did recently, with a bit of motivation and a very handwavy explanation of them.
******
On the easier side we have a C1 from the 2014 IMO Shortlist. The statement is as follows:

[IMO Shortlist 2014 C1](https://artofproblemsolving.com/community/c6h1113183p5083543) Let \(n\) points be given inside a rectangle \(R\) such that no two of them lie on a line parallel to one of the sides of \(R\). The rectangle \(R\) is to be dissected into smaller rectangles with sides parallel to the sides of \(R\) in such a way that none of these rectangles contains any of the given points in its interior. Prove that we have to dissect \(R\) into at least \(n + 1\) smaller rectangles.

![Moving Points](/2014C1.png)

The idea here is to fix some disection and pair up each point to a unique rectangle. We'll move the points as far left or down on the corresponding segment that it's on, as it turns out we can match each point to the rectangle that's directly above or to the right of said point. Assume otherwise, then either

  1. there are two red points on the same edge, by the problem this is obviously untrue
  2. the two red points are on the left and bottom edge of some rectangle, but then the dissection of \(R\) will have some 270 degree angle inside of it, which clearly can't happen.

******
This next problem is less cute but appears to have more substance. The following is the 6th problem in the 2010 USA TST for the IMO, reduced to a graph theory statement.

[USA TST 2010/6](https://artofproblemsolving.com/community/c6h358772p1960068) Show that the number of dominating subsets of a graph is odd.

![Moving Subsets](/10USATST6.png)

The best way to prove is directly! But first an annoying setup. Let \(V\) be the set of vertices, and \(A\) be some dominating set. Consider the __maximal__ subset of vertices \(B \subseteq A\) such that for each vertex \(b \in B\), then \(b\) shares a vertex with some vertex in \(V/A\).

Now here's the bijection, pair up the dominating sets \(A\) and \(A/B \cup V/A\) (swapping the blue set for the red set above). Note that every dominating set gets paired except for \(V\), so there must be an odd number of dominating sets.

