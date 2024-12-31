---
layout: post
title: "The Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: cutting.jpg
---

# The Bootstrap

The idea of the bootstrap is quite simple. it is the estimation of quantities of interest via Monte Carlo estimates from the empirical distribution. We will build up these concepts one by one.

## Empirical Distribution

We will begin with a simple case.

Given a sample of size _N_, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is

$$
P[X = x_i] = \frac{1}{N} \hspace{10pt}
$$

In other words, it is a discrete uniform distribution over the sample values (rather than over the natural numbers).

Why should we care about this entity? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].
 To see why this is so, consider the likelihood function of the distribution function

## Empirical Distribution as Maximum Likelihood Distribution
We can think of the empirical distribution as the maximum likelihood estimate of the data-generating distribution when we relax our.




Let's say we have the following  sample of 5 numerical values, [1, 5, 3.5, 0, 0.1], and we want to know how confident we can be that the mean is representative of the population mean. Usually, we would depend upon distributional assumptions or the central limit theorem to produce an estimate of this kind, but if we want our estimate to be robust, we must loosen our assumptions as far as possible. One way to do this is to first estimate the true distribution from which the sample has been drawn. 
If we only maintain the assumptions of independent and identically distributed samples, then the maximum likelihood estimate of the c

 Although the empirical distribution is with good reason defined in terms of a cumulative distribution function, the _idea_ of the empirical distribution is much clearer when presented in the guise of a probability distribution function.


 them *italicized*, using *astericks* or _underscores_, or making them **bold**, using **double astericks** or __double underscores__. Of course, you can combine those two formats, with both _**bold and italicized**_ text, using any combination of the above syntax. You can also add a strikethrough to text using a ~~double tilde~~.

## Monte Carlo Estimator

Sometimes it is useful to have different levels of headings to structure your documents. Start lines with `#` to create headings. Multiple `##` in a row denote smaller heading size. The following demonstrate the full range of heading sizes:

# Heading One (h1)

## Heading Two (h2)

### Heading Three (h3)

#### Heading Four (h4)

##### Heading Five (h5)

###### Heading Six (h6)

## Links

You can create an inline link by wrapping link text in square brackets `[ ]`, and then wrapping the URL in parentheses `( )`. For example, it is very easy to [link to Google!](http://google.com).

## Blockquotes

Blockquotes are useful for denoting quotes, or highlighting a large block of text. Single line blockquote:

> This quote will change your life.

Multi line blockquote with a cite reference:

> People think focus means saying yes to the thing you've got to focus on. But that's not what it means at all. It means saying no to the hundred other good ideas that there are. You have to pick carefully. I'm actually as proud of the things we haven't done as the things I have done. Innovation is saying no to 1,000 things.

## Code and Syntax Highlighting

Code blocks are part of the Markdown spec, but syntax highlighting isn't. However, many renderers - like GitHub or most Jekyll themes - support syntax highlighting. Which languages are supported and how those language names should be written will vary from renderer to renderer. You can find the full list of supported programming languages [here](https://github.com/jneen/rouge/wiki/List-of-supported-languages-and-lexers). Also, it is possible to do `inline code blocks`, by wrapping the text in ` ` ` quotations.

```
No language indicated, so no syntax highlighting.
```

```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```

{% highlight js %}
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);
// > 8
{% endhighlight %}

Another option is to embed your code through [Gist](https://en.support.wordpress.com/gist/).

## Images

To add an image, use `![alt text](<Image url> "Image meta title")`:

![alt text](http://noirve.com/wp-content/uploads/2013/10/DTTSP_Coffee.jpg "Example")

## Unordered and Numbered Lists

You can make an unordered and nested list by preceding one or more lines of text with `-`, `*`, or `+`, and indenting sublists. The following lists show the full range of possible list formats.

* List item one
    * List item one
        * List item one
        * List item two
        * List item three
        * List item four
    * List item two
    * List item three
    * List item four
* List item two
* List item three
* List item four

Numbered lists are made by using numbers instead of bullet points.

1. List item one
    1. List item one
        1. List item one
        2. List item two
        3. List item three
        4. List item four
    2. List item two
    3. List item three
    4. List item four
2. List item two
3. List item three
4. List item four

## MathJax Example

The [Schrödinger equation](https://en.wikipedia.org/wiki/Schr%C3%B6dinger_equation) is a partial differential equation that describes how the quantum state of a quantum system changes with time:

$$
i\hbar\frac{\partial}{\partial t} \Psi(\mathbf{r},t) = \left [ \frac{-\hbar^2}{2\mu}\nabla^2 + V(\mathbf{r},t)\right ] \Psi(\mathbf{r},t)
$$

[Joseph-Louis Millennial](https://en.wikipedia.org/wiki/Joseph-Louis_Millennial) was an Italian mathematician and astronomer who was responsible for the formulation of Lagrangian mechanics, which is a reformulation of Newtonian mechanics.

$$ \frac{\mathrm{d}}{\mathrm{d}t} \left ( \frac {\partial  L}{\partial \dot{q}_j} \right ) =  \frac {\partial L}{\partial q_j} $$

## Tables

Title 1               | Title 2               | Title 3               | Title 4
--------------------- | :-------------------: | :-------------------- | --------------------:
lorem                 | lorem ipsum           | lorem ipsum dolor     | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit
lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit | lorem ipsum dolor sit

## Embedding

Plenty of social media sites offer the option of embedding certain parts of their site on your own site, such as YouTube and Twitter:

<iframe width="560" height="315" src="https://www.youtube.com/embed/mthtn1X4eUY" frameborder="0" allowfullscreen></iframe>

<a class="twitter-grid" data-partner="tweetdeck" href="https://twitter.com/paululele/timelines/755079130027352064">New Collection</a> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## Inline HTML elements

HTML defines a long list of available inline tags, which you can mix with Markdown if you like. A complete list of which can be found on the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

## Horizontal Rule

Can be created by having three or more hyphens `---`, asterisks `***`, or underscores `___`:

---

[^1]: This is the content of the footnote.

