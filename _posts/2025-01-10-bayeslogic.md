---
layout: post
title: "Notes: Probability as a Generalization of Propositional Logic"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
hide_related_posts: true
---

According to most schools of Bayesianism, one should interpret the probability of a proposition as a measure of its plausibility. Within this framework, the two values of propositional logic, true and false, become the two extremes of probability, $p = 1$ and $p = 0$. And one can show that all arguments in propositional logic are in fact specific cases of the laws of probability.


As an example, take two of the most commonly encountered forms of argument in propositional logic: _modus ponens_ and _modus tollens_.  These are our classic Aristotelian syllogisms. Symbolically, they look like this[^1]:

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

Now, there exist several ways in which the truth tables of logical implications can be represented as statements about probabilities. For example, these two are _modus ponens_ and _modus ponens_ in miniature:

$$
p \to q \Longleftrightarrow P( q = \mbox{T}\mid p = \mbox{T}) = 1
$$

$$
p \to q \Longleftrightarrow P( p = \mbox{T}\mid q = \mbox{F}) = 0
$$


## Fallacies Unfallacied

Furthermore, in the language of probability, two fallacious forms of argument, known as _affirming the consequent_ and _denying the antecedent_ become valid when one lets the propositions take on probabilities other than 1 and 0. In their two-valued logic form, we have

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


When we convert these fallacies into valid probability statements, the major premise is again that $P( b = \mbox{T}\mid a = \mbox{T}) = 1$, which is just the probabilistic notation for $a \to b$, but the premises conclusions change from assertions of truth and falsity to ones of greater and lesser plausibility (we will use _a_ and _b_ instead of _p_ and _q_ so as to avoid confusion between the statement _p_ and the probability notation of _P_).

### _Valid Weak Form of Affirming the Consequent_
$$\begin{array}{rl}
    & P( b = \mbox{T}\mid a = \mbox{T}) = 1 \\
    & 0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1\\
    & b = \mbox{T}\\
    \hline{}
    \therefore & P( a = \mbox{T}\mid b = \mbox{T}) > P( a = \mbox{T}) 
  \end{array}$$

### _Valid Weak Form of Denying the Antecedent_
$$\begin{array}{rl}
    & P( b = \mbox{T}\mid a = \mbox{T}) = 1 \\
    & 0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1\\
    & p = \mbox{F}\\
    \hline{}
    \therefore & P( b = \mbox{F}\mid a = \mbox{F}) > P( b = \mbox{F}) 
  \end{array}$$

Both follow from Bayes' theorem; however, here we will only develop the first argument in detail. Bayes' theorem relates conditional probabilities in the following way:

$$
P( a = \mbox{T}\mid b = \mbox{T}) = \frac{P( b = \mbox{T}\mid a = \mbox{T})P( a = \mbox{T})}{P( b = \mbox{T})}
$$

Now, drawing from the premises of the argument, we can plug in 1 for $P( b = \mbox{T}\mid a = \mbox{T})$:

$$
P( a = \mbox{T}\mid b = \mbox{T}) = \dfrac{P( a = \mbox{T})}{P( b = \mbox{T})}
$$

And rearranging which, we have

$$
P( a = \mbox{T}\mid b = \mbox{T})P( b = \mbox{T}) = P( a = \mbox{T})
$$

And, according to the premises, $0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1$. So each term of the above equation must be positive, and our conclusion $P( b = \mbox{F}\mid a = \mbox{F}) > P( b = \mbox{F})$ follows because on the left side of the equation a positive number is being multipled by a number between 0 and 1 to produce the quantity on the right-hand side. In other words, in the last step of the argument, we are using the fact that a proper fraction of a positive number is less than that number.

## Bernoulli's Fallacy 

While the probabilistic framework does allow for weak syllogisms of this type that would be considered fallacies in two-valued logic, it also comes with its own fallacies, the most notorious being Bernoulli's fallacy, which owes its infamy to its privileged place at the center of frequentist statistics.


In short, Bernoulli's fallacy is the assertion that

$$
P(A = a \mid B = b) \approx 1 \Longleftrightarrow P(B = b \mid A = a) \approx 1 
$$

Or

$$
P(A = a \mid B = b) \approx 0 \Longleftrightarrow P(B = b \mid A = a) \approx 0 
$$

This fallacious line of reasoning arises in frequentist statistics whenever one attempts to draw conclusions about inferential probabilities from sampling probabilities. Take the isolated use of $p$-values as an example. A typical $p$-value argument takes the following form

$$
P(X > x \mid \Theta = \theta_{0}) \approx 0 \Longrightarrow P(\Theta = \theta_{0} \mid X > x) \approx 0
$$

On the left we have a small $p$-value, and on the right a statement that is more or less equivalent to the rejection of the null hypothesis. A familiarity with Bayes' theorem or with the definition of conditional probability should be enough to convince one of the fallaciousness of the argument: the ratio of $P(X > x)$ and $P(\Theta = \theta_{0})$ must be known before we can apply Bayes theorem and draw any valid conclusions about the inferential probability from the sampling probability.


## Sources
 * _Probability Theory: The Logic of Science_ by Edwin Jaynes

## Footnotes

[^1]: It is common to see the premises flipped, but it has always made more sense to me that the inferential rule (the major premise), being the more general statement, should precede the particular application of the minor premise.






