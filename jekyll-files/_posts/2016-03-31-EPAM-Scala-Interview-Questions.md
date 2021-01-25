---
layout: post
title: "2016-03-31-EPAM-Scala-Interview-Questions"
date: 2016-04-01 08:00:00
categories: interview
---

## Scala Interview Questions


```scala
1. pattern matching and functional composition

https://twitter.github.io/scala_school/pattern-matching-and-functional-composition.html

scala compose partial functions
scala> val fComposeG = f _ compose g _
fComposeG: (String) => java.lang.String = <function>

scala> fComposeG("yay")
res0: java.lang.String = f(g(yay))


andThen
andThen is like compose, but calls the first function and then the second, g(f(x))

scala> val fAndThenG = f _ andThen g _
fAndThenG: (String) => java.lang.String = <function>

scala> fAndThenG("yay")
res1: java.lang.String = g(f(yay))

2. map

3. implicit parameters

4. [T] T+  T- usage?

```