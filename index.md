---
title       : Slidify 
subtitle    : Great(?) Presentations from R Markdown
author      : Robert J. Walls
job         : University of Massachusetts
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}

--- .segue .quote .dark

<q> Who doesn't like to start out a presentation with a quote? </q>

--- bg: yellow

## Simple Code Blocks

Slide 2 text
 - bullet?
 
### Another title?

Hello thar.

*** pnotes

I need to focus on the following
 - key point
 - other key point
 - clever anecdote

---


## Using ggplot


```r
library(ggplot2)
ggplot(diamonds, aes(carat, price)) + geom_hex()
```

<img src="figure/unnamed-chunk-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" style="display: block; margin: auto;" />


Use `echo=FALSE` to hide the code block on your slide.

---

## Equations
The Arithmetic mean is equal to $\frac{1}{n} \sum_{i=i}^{n} x_{i}$, or the summation
of n numbers divided by n.

$$ H(X)=-\sum_{i}{P(x_i) log_b P(x_i)} $$

---

## Python!

Use fenced code blocks to render Python code with syntax highlighting.

```python
def hello():
  '''
  Such a boring function
  '''
  print 'hi!'
  
if __name__ == '__main__':
  hello()
```

--- .segue .dark

## Segue Slide

---

## Getting Started with Slidify

You have to use Hadley's `devtools` package to download and install Slidify from Github.

```r
library(devtools)
install_github('slidify', 'ramnathv')
install_github('slidifyLibraries', 'ramnathv')
```

It is simple to create a new presentation.

```r
library(slidify)

#Create a new presentation called 'mydeck'
author('mydeck')
```

Slidify does much of the setup work for you (including creating the github repo). 
You just need to edit the `index.Rmd` file!

---

## Publishing your Presentation

When you are ready to share your handiwork.

```r
# Generate the Deck
slidify('index.Rmd')

# Publish it to github
publish(user='rjwalls', repo='SlidifyTest', host='github')
```

Puts the presentation at <http://rjwalls.github.com/SlidifyTest>. Note that you need to setup your [Github SSH keys](https://help.github.com/articles/generating-ssh-keys).  

Can also use Rpubs or Dropbox.

---

## Slidify Philosophy

Separate the content writing from the its rendering.

---

## RMarkdown

### You can use all of the features you love in Rmarkdown including:
 - bullets

### As well as numbered lists:
 1. Thing 1
 2. Thing 2
 
### Animated lists:
> - This is probably specific to IO2012
> - Point 2
 
*Italicized* and **bold** font. Or maybe not...

---

## Tables

Column 1  | Column 2
----------|---------
Foo       | Bar
Blah      | Blah
Bing      | Bang


---

## IO2012 

The default slide framework is `io2012` from Google's 2012 I/O developer conference.

Adds some nice presenter features
 - Pressing 'h' highlights code snippets
 - Pressing 'p' toggles speaker notes (if they're on the current slide)
 - Pressing 'f' toggles fullscreen viewing
 - Pressing 'w' toggles widescreen
 - Pressing 'o' toggles overview mode
 - Pressing 'ESC' toggles off these goodies

---

## Tables from a Data.frame


```r
library(plyr)

df <- diamonds[seq(1, 5), ]
df <- with(df, cbind(price, carat, cut, clarity))

# Make the header
header <- paste(colnames(df), collapse = " | ")
dashline <- paste(rep(c("---"), length(colnames(df))), collapse = " | ")

# Add the data
data <- aaply(df, 1, paste, collapse = " | ")
```


---

## Tables from a Data.frame


```r
cat(header, dashline, data, sep = "\n")
```

price | carat | cut | clarity
--- | --- | --- | ---
326 | 0.23 | 5 | 2
326 | 0.21 | 4 | 3
327 | 0.23 | 2 | 5
334 | 0.29 | 4 | 4
335 | 0.31 | 2 | 2


Make sure to set `results='asis'`.

---

--- bg:url(successkid.jpg)

## Slide with a Background Image 

---


## Useful Links
 - [R Markdown Examples](https://gist.github.com/jeromyanglim/2716336)
 - [Slidify](http://slidify.org/)
 - [I/O 2012 Template](https://code.google.com/p/io-2012-slides/)

---


