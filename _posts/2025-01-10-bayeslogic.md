---
layout: post
title: "Notes: Probability as a Generalization of Propositional Logic"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
hide_related_posts: true
---

According to a certain school of Bayesianism, we should interpret the probability of a proposition as a measure of its plausibility. Within this framework, the two values of propositional logic, true and false, become the two extremes of probability, $p = 1$ and $p = 0$. And we can show that all arguments in propositional logic are in fact specific cases of the laws of probability.


As an example, take the two most fundamental forms of argument in propositional logic: _modus ponens_ and _modus tollens_.  These are our classic Aristotelian syllogisms. Symbolically, they look like this[^1]:

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

Now, there exist several ways in which the truth table of logical implication can be represented as statements about probabilities; for example, these two are _modus ponens_ and _modus ponens_ in miniature:

$$
p \to q \Longleftrightarrow P( q = \mbox{T}\mid p = \mbox{T}) = 1
$$

$$
p \to q \Longleftrightarrow P( p = \mbox{T}\mid q = \mbox{F}) = 0
$$


We can also put so-called inductive syllogisms into the language of probability. These are the types of arguments that people actually can make use of in the real world. $\mbox{\color{red}{Red}}$
## Footnotes

[^1]: It is common to see the premises flipped, but that has never made sense to me. To my mind it is reasonable that the inferential rule (the major premise), being the more general statement, should precede the particular application of the minor premise.






