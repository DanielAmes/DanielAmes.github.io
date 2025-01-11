---
layout: post
title: "Notes: Probability as a Generalization of Propositional Logic"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
hide_related_posts: true
---

According to a certain school of Bayesianism, we should interpret the probability of a proposition as a measure of its plausibility. Within this framework, the two values of propositional logic, true and false, become the two extremes of probability, $p = 1$ and $p = 0$. And we can show that all arguments in propositional logic are in fact specific cases of the laws of probability.


As an example, take the two most fundamental forms of argument in propositional logic: _modus ponens_ and _modus tollens_.  These are our classic Aristotelian syllogisms. Symbolically, they look like this[1]:

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

The key to translating these forms of arguments into the language of probability is to realize that the probabilistic analogue of logical implication is conditional probability:

$$
p \to q \Longleftrightarrow P( q = \mbox{T}\mid p = \mbox{T}) = 1
$$

Then to show that in the language of probability that _modus tollens_ is still a valid form of argument, we just apply Bayes' theorem and the complement rule. The premises become $P( q = \mbox{T}\mid p = \mbox{T}) = 1$ and $P(q = \mbox{F}) = 1$, and the conclusion is $P( p = \mbox{T}\mid q = \mbox{F}) = 0$. By Bayes' rule:

$$P( p = \mbox{T}\mid q = \mbox{F}) = \frac{P( q = \mbox{F}\mid p = \mbox{T})P(p = \mbox{T})}{P(q = \mbox{F})}$$

$$
= P( q = \mbox{F}\mid p = \mbox{T})P(p = \mbox{T})
$$

Then, by the complement rule,

$$
P( p = \mbox{T}\mid q = \mbox{F}) =  (1 - P( q = \mbox{T}\mid p = \mbox{T}))P(p = \mbox{T})
$$

$$ 
= (1 - 1)P(p = \mbox{T})
$$

$$ 
= 0
$$

Another example is the rule of the contrapositive, which bears a degree of resemblance to the _modus tollens_ argument. The rule states

$$
p \to q \Longleftrightarrow \neg q \to \neg p 
$$

And in probabilistic terms, this becomes

$$
P( q = \mbox{T}\mid p = \mbox{T}) = P( p = \mbox{F}\mid q = \mbox{F}) 
$$

Again, we use Bayes' rule and the complement rule

## Jaynes

But these examples are mere hints at the revolution in thinking that comes from the view of probability and its laws as the most general and most complete q

; but before we do so, we will demonstrate why the laws of probability are the only possible possible set of rules that fulfill 

In _Probability Theory: The Logic of Science_, Edwin Jaynes builds up the laws of probability as the only possible rules that fulfill a certain 



## Footnotes

[1] It is common to the order of the premises of these arguments flipped, but that has never made sense to me. To my mind it is reasonable that the inferential rule (the major premise), being the more general statement, should precede the particular application of the minor premise.






