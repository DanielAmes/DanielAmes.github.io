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


## Fallacies Unfallacied

Furthermore, in the language of probability, two fallacious forms of argument, known as _affirming the consequent_ and _denying the antecedent_ become valid when we let the propositions take on probabilities other than 1 and 0. In their two-valued logic form, we have

### _The Fallacy of Affirming the Consequent_
$$\begin{array}{rl}
    & p \to q \\
    & q \\
    \hline{}
    \therefore & p
  \end{array}$$

### _The Fallacy of Denying the Antecedent_
$$\begin{array}{rl}
    & p \to q \\
    & \neg p \\
    \hline{}
    \therefore & \neg q
  \end{array}$$


When we convert these fallacies into valid probability statements, the major premise is again that $P( q = \mbox{T}\mid p = \mbox{T}) = 1$, but the conclusions change from assertions of truth and falsity to ones of greater and lesser plausibility.

### _Valid Weak Form of Affirming the Consequent_
$$\begin{array}{rl}
    & P( q = \mbox{T}\mid p = \mbox{T}) = 1 \\
    & q = \mbox{T}\\
    \hline{}
    \therefore & P( p = \mbox{T}\mid q = \mbox{T}) > P( p = \mbox{T}) 
  \end{array}$$

### _Valid Weak Form of Denying the Antecedent_
$$\begin{array}{rl}
    & P( q = \mbox{T}\mid p = \mbox{T}) = 1 \\
    & p = \mbox{F}\\
    \hline{}
    \therefore & P( q = \mbox{F}\mid p = \mbox{F}) > P( q = \mbox{F}) 
  \end{array}$$

Both follow from Bayes' theorem. 

## Bernoulli's Fallacy 

While the probabilistic framework does allow for weak syllogisms of this type that would be considered fallacies in two-valued logic, it also comes with its own fallacies, the most notorious of which being Bernoulli's fallacy, which owes its infamy to its privileged place at the center of frequentist statistics.


In short, Bernoulli's fallacy is the assertion that

$$
P(A = a \mid B = b) \approx 1 \Longleftrightarrow P(B = b \mid A = a) \approx 1 
$$

Or

$$
P(A = a \mid B = b) \approx 0 \Longleftrightarrow P(B = b \mid A = a) \approx 0 
$$

This fallacious line of reasoning comes up in frequentist statistics, when one tries to draw conclusions about inferential probabilities from sampling probabilities. Take the isolated use of $p$-values as an example. A typical $p$-value argument takes the following form

$$
P(X > x \mid \Theta = \theta_{0}) \approx 0 \Longrightarrow P(\Theta = \theta_{0} \mid X > x) \approx 0
$$

On the left we have a small $p$-value, and on the right a statement that is more or less equivalent to the rejection of the null hypothesis. The least passing familiarity with Bayes' theorem or even with the definition of conditional probability should be enough to convince one of the fallaciousness of such an argument. According to Bayes' Theorem, $P(X > x)$ and $P(\Theta = \theta_{0})$ (or at least their ratio) must be known before we can draw any valid conclusions on the inferential probability from the sampling probability.


## Sources
 * _Probability Theory: The Logic of Science_ by Edwin Jaynes

## Footnotes

[^1]: It is common to see the premises flipped, but that has never made sense to me. To my mind it is reasonable that the inferential rule (the major premise), being the more general statement, should precede the particular application of the minor premise.






