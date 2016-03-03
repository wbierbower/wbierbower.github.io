---
layout: default
title: A Refresher on Markdown
permalink: /tutorials/tutorial_markdown.html
---

# A Refresher on Markdown

Markdown provides a clean and simple syntax for writing content to be parsed and translated into HTML.

The following is adapted from Daring Fireball's [Markdown  primer](http://daringfireball.net/projects/markdown/).

<!-- TOC depth:6 withLinks:1 updateOnSave:1 orderedList:0 -->
**Table of Contents**

- [Block Quotes](#block-quotes)
- [Phrase Emphasis](#phrase-emphasis)
- [Lists](#lists)
- [Links](#links)
- [Images](#images)
- [Code Highlighting](#code-highlighting)
- [Math](#math)
- [Other Resources](#other-resources)
<!-- /TOC -->

## Block Quotes

{% highlight text %}

> block quote
>
> second paragraph of block quote

{% endhighlight %}

> block quote
>
> second paragraph of block quote

## Phrase Emphasis


{% highlight text %}

- *Italics*
- **Bold**
- __Bold2__

{% endhighlight %}

- *Italics*
- **Bold**
- __Bold2__

## Lists

{% highlight text %}

**Unordered**

- one
- two
- three

**Ordered**

1. one
2. two
3. three

{% endhighlight %}

**Unordered**

- one
- two
- three

**Ordered**

1. one
2. two
3. three

## Links

{% highlight text %}

[A link](http://www.google.com)

{% endhighlight %}


[A link](http://www.google.com)

<!-- [link with kramdown](url){:target="_blank"} -->

## Images

{% highlight text %}

![alt text](./path/to/image "title")

![alt text with id][id]

# with kramdown
![alt text](./path/to/image "tile"){: width="300px" }

{% endhighlight %}


![alt text](./path/to/image "title")

![alt text with id][id]

![alt text](./path/to/image "tile"){: width="300px" }

## Code Highlighting

{% highlight text %}

jekyll's liquid template tags make this one difficult to keep as text.

between tags: use 'highlight <lang>' and 'endhighlight'

{% endhighlight %}


{% highlight python %}
def print_hi(name)
  print "hi,", name

>>> print_hi('there')
'hi, there'

{% endhighlight %}



## Math

{% highlight text %}

This is an inline math statement: $$sin(x^2)$$

This is a block statement

$$sin(x^2)$$

{% endhighlight %}


This is an inline math statement: $$sin(x^2)$$

This is a block statement

$$sin(x^2)$$

## Other Resources

- [GitHub Flavord Markdown](https://help.github.com/articles/github-flavored-markdown/)
- [kramdown (used by Jekyll)](http://kramdown.gettalong.org/)

[id]: './path/to/image' "title"
