---
layout: post
title: "Bayesianism as a Generalization of Propositional Logic"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
hide_related_posts: true
---

According to a certain school of Bayesianism, we should interpret the probability of a proposition as a measure of its plausibility. Within this framework, the two values of propositional logic, true and false, become the two extremes of probability, $p = 1$ and $p = 0$. And in fact we can show that all arguments in propositional logic are in fact specific cases of the laws of probability.

As an example, take the two most fundamental forms of argument in propositional logic: modus ponens and the modus tollens.  These are our classic Aristotelian syllogisms. Symbolically, they look like this:

### _Modus Ponens_
$$\begin{array}{rl}
    & p \to q \\
    & p \\
    \hline{}
    \therefore & q
  \end{array}$$

### _Modus Tollens_
$$\begin{array}{rl}
    & p \to q \\
    & \neg q \\
    \hline{}
    \therefore & \neg p
  \end{array}$$

The key to translating these forms to arguments in the language of probability is to realize that logical implication, $ \to $