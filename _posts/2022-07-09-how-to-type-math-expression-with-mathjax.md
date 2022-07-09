---
title: How to type Math Expression with MathJax
author: huynhtancuong
date: 2022-07-09 11:50:00 +0300
categories: [Blogging, Tutorial]
tags: [mathjax, latex, math expression]
math: true
mermaid: true
---

This post is to show how to write math expression by using MathJax syntax , you can also use it as an example of writing. Now, let's start looking at MathJax and expressions.

## What is MathJax? 

MathJax is a javascript display engine for rendering TEX or MathML-coded mathematics in browsers without requiring font installation or browser plug-ins. Any modern browser with javascript enabled will be MathJax-ready.

## Some basic syntax

To type a math expression, surround the expression like below:

$$\text{\$expression\$}$$

The `~` acts as a space in Mathjax expression.
Surround the expression by two `$` will make the expression center:
 
$$x~y$$

```
$$x~y$$
```


## Examples 

### Sum

$$
\sum_{i=0}^{n^3} i^3=\frac{n(n+1)}{2}
$$

```
$$
\sum_{i=0}^{n^3} i^3=\frac{n(n+1)}{2}
$$
```

### Alpha symbol

$$
\alpha^2+\beta^2=\gamma^2
$$

```
$$
\alpha^2+\beta^2=\gamma^2
$$
```

$$
\Gamma^2+\Omega^2 = \Delta^2
$$

```
$$
\Gamma^2+\Omega^2 = \Delta^2
$$
```

### Logarit

$$
x_3^5 = log_3(34)
$$

```
$$
x_3^5 = log_3(34)
$$
```

### Small ()

$$
\left( expression \right)
$$

```
$$
\left( expression \right)
$$
```


### Square root

$$
\left(\frac{\sqrt{xyz}}{b} = \sqrt{a}\right) 
$$

```
$$
\left(\frac{\sqrt{xyz}}{b} = \sqrt{a}\right) 
$$
```

### Big ()

$$
\biggl( ~ \bigr) ~ \biggr)
$$

```
$$
\biggl( ~ \bigr) ~ \biggr)
$$
```

$$
\bigcup \bigcap \int_x^3 \iiiint \idotsint
$$

```
$$
\bigcup \bigcap \int_x^3 \iiiint \idotsint
$$
```

### Fraction

$$
\cfrac{s}{a}
$$

```
$$
\cfrac{s}{a}
$$
```

$$
\sqrt[3]{x^3} = |x|
$$

```
$$
\sqrt[3]{x^3} = |x|
$$
```

### Limit

$$
\lim_{x \to 0}{(x+4)}
$$

```
$$
\lim_{x \to 0}{(x+4)}
$$
```

### Trigonometry

$$
\sin^2 \theta + \cos^2(\theta) = 1
$$

```
$$
\sin^2 \theta + \cos^2(\theta) = 1
$$
```

### Less, equal, greater

$$
2 \lt 3;~ 3 \leqslant 3; ~ 3 \neq 2
$$

```
$$
2 \lt 3;~ 3 \leqslant 3; ~ 3 \neq 2
$$
```

$$
-b \pm \sqrt{b^2 - 4ac} \over 2a 
$$

```
$$
-b \pm \sqrt{b^2 - 4ac} \over 2a 
$$
```

### Times

$$
x \times y 
$$

```
$$
x \times y 
$$
```

$$
x \to y; x \rightarrow y; x \leftarrow y; x \Leftarrow y; x \mapsto y; x \land y ; x \lor y
$$ 

```
$$
x \to y; x \rightarrow y; x \leftarrow y; x \Leftarrow y; x \mapsto y; x \land y ; x \lor y
$$ 
```

$$
x \star y; x \ast y; x \oplus y; x \circ y; x \approx y; x \sim y ; x \forall y; x \top y; 
$$

```
$$
x \star y; x \ast y; x \oplus y; x \circ y; x \approx y; x \sim y ; x \forall y; x \top y; 
$$
```

### Infinity

$$
\infty
$$

```
$$
\infty
$$
```


### Derivative

$$\partial x \over \partial y$$ 

```
$$\partial x \over \partial y$$ 
```

$$
a \equiv c \pmod b 
$$

```
$$
a \equiv c \pmod b 
$$
```

$$
a_1 + \ldots \cdots a_n
$$

```
$$
a_1 + \ldots \cdots a_n
$$
```

$$
cos\phi ~ cos\epsilon ~ 
$$

```
$$
cos\phi ~ cos\epsilon ~ 
$$
```

### \quad
Instead of using `~~~`, we can use `\quad`.

$$
a \quad b 
$$

```
$$
a \quad b 
$$
```

### Pure text

$$
\text{hihihi}
$$

```
$$
\text{hihihi}
$$
```

### Widehat 

$$
\widehat{xy}
$$

```
$$
\widehat{xy}
$$
```

### Vector 

$$
\overrightarrow{v} + \overrightarrow{w} = 1
$$

```
$$
\overrightarrow{v} + \overrightarrow{w} = 1
$$
```

### Differential equation

$$
\dot x + \ddot x = 0
$$

```
$$
\dot x + \ddot x = 0
$$
```

$$
\{x\}
$$

```
$$
\{x\}
$$
```