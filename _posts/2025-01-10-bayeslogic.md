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
    & a \to b \\
    & a \\
    \hline{}
    \therefore & b
  \end{array}$$

### _Modus Tollens_
$$\begin{array}{rl}
    & a \to b \\
    & \neg b \\
    \hline{}
    \therefore & \neg a
  \end{array}$$

Now, there exist several ways in which the truth tables of logical implications can be represented as statements about probabilities. For example, these two are _modus ponens_ and _modus ponens_ in miniature:

$$
a \to b \Longleftrightarrow P( b = \mbox{T}\mid a = \mbox{T}) = 1
$$

$$
a \to b \Longleftrightarrow P( a = \mbox{T}\mid b = \mbox{F}) = 0
$$


## Fallacies Unfallacied

Furthermore, in the language of probability, two fallacious forms of argument, known as _affirming the consequent_ and _denying the antecedent_ become valid when one lets the propositions take on probabilities other than 1 and 0. In their two-valued logic form, we have

### _The Fallacy of Affirming the Consequent_
$$\begin{array}{rl}
    & a \to b \\
    & b \\
    \hline{}
    \therefore & a
  \end{array}$$

### _The Fallacy of Denying the Antecedent_
$$\begin{array}{rl}
    & a \to b \\
    & \neg a \\
    \hline{}
    \therefore & \neg b
  \end{array}$$


When we convert these fallacies into valid probability statements, the major premise is again that $a \to b$, which in probabilistic notation becomes $P( b = \mbox{T}\mid a = \mbox{T}) = 1$, but we now take the statements _a_ and _b_ to be uncertain, and the conclusions change from assertions of truth and falsity to ones of greater and lesser plausibility.

### _Valid Weak Form of Affirming the Consequent_
$$\begin{array}{rl}
    & P( b = \mbox{T}\mid a = \mbox{T}) = 1 \\
    & 0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1\\
    \hline{}
    \therefore & P( a = \mbox{T}\mid b = \mbox{T}) > P( a = \mbox{T}) 
  \end{array}$$

### _Valid Weak Form of Denying the Antecedent_
$$\begin{array}{rl}
    & P( b = \mbox{T}\mid a = \mbox{T}) = 1 \\
    & 0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1\\
    \hline{}
    \therefore & P( b = \mbox{F}\mid a = \mbox{F}) > P( b = \mbox{F}) 
  \end{array}$$

As an example of the first argument, let us imagine that we walk outside and notice that the ground is wet. Now, our assumption is that the ground will always be wet immediately following a rain storm, or, in probabilistic language, that 

$$P(\mbox{Wet Ground} = \mbox{T} \mid \mbox{Recent Rain Storm} = \mbox{T}) =1$$

The argument tells us that under this assumption, the plausibility of a recent rainstorm given the information that the ground is wet should be greater than if we did not have any information: 

$$
P( \mbox{Recent Rain Storm} = \mbox{T}\mid \mbox{Wet Ground} = \mbox{T}) > P( \mbox{Recent Rain Storm} = \mbox{T})
$$

## Proof of the Validity of the Weak Form of Affirming the Consequent

The validity of these arguments follows from Bayes' theorem; however, here we will only develop the first of the two arguments in detail. Bayes' theorem relates conditional probabilities of binary statements in the following way:

$$
P( a = \mbox{T}\mid b = \mbox{T}) = \frac{P( b = \mbox{T}\mid a = \mbox{T})P( a = \mbox{T})}{P( b = \mbox{T})}
$$

Now, drawing from the premises of the argument, we can plug in 1 for $P( b = \mbox{T}\mid a = \mbox{T})$ on the right-hand side, giving us

$$
P( a = \mbox{T}\mid b = \mbox{T}) = \dfrac{P( a = \mbox{T})}{P( b = \mbox{T})}
$$

And rearranging which, we have

$$
P( a = \mbox{T}\mid b = \mbox{T})P( b = \mbox{T}) = P( a = \mbox{T})
$$

And, according to the premises, $0 < P( a = \mbox{T} ), P( b = \mbox{T} ) < 1$, so each term in the above equation must be positive, and our conclusion, $P( a = \mbox{T}\mid b = \mbox{T}) > P( a = \mbox{T})$, follows from the fact that a proper fraction of a positive number is less than that number.

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

This fallacious line of reasoning arises in frequentist statistics whenever one attempts to draw conclusions about inferential probabilities from sampling probabilities[^2]. Take the isolated use of $p$-values as an example. A typical $p$-value argument takes the following form

$$
P(X > x \mid \Theta = \theta_{0}) \approx 0 \Longrightarrow P(\Theta = \theta_{0} \mid X > x) \approx 0
$$

On the left we have a small $p$-value, and on the right a statement that is more or less equivalent to the rejection of the null hypothesis. A familiarity with Bayes' theorem or with the definition of conditional probability should be enough to convince one of the fallaciousness of the argument: the ratio of $P(X > x)$ and $P(\Theta = \theta_{0})$ must be known before we can apply Bayes theorem and draw any valid conclusions about the inferential probability from the sampling probability.


## Sources
 * _Probability Theory: The Logic of Science_ by Edwin Jaynes

## Footnotes

[^1]: It is common to see the premises flipped, but it has always made more sense to me that the inferential rule (the major premise), being the more general statement, should precede the particular application of the minor premise.

[^2]:A sampling probability is the probability of obtaining data given certain assumptions about the data-generating mechanism, such as the parameters of a distrbution that the data are assumed to have been drawn from. An inferential probability, the converse, is the probability that an assumption about the data-generating mechanism is true given the data that have been observed. 





