+++
author = "Slow Motion"
title = "Probability"
date = "2021-10-28"
description = "TBD."
featured = false
tags = [
    "probability",
    "statistics"
]
categories = [
    "statistics"
]
series = ["statistics"]
aliases = ["statistics"]
thumbnail = "images/dice.png"
+++

This article offers theoretical description of Hidden Markov Model (HMM), examples, and code. To understand HMM, basic knowledge of statistics, 

<!--more-->

#### [1. Basic Rules](#basic-rules)
#### [2. Properties](#properties)
#### [3. Random Variables](#random-variables)
#### [4. Distributions](#distribution)
#### [5. Conditional Probability](#conditional-probability)

## Basic Rules

## Properties

1. The probability of an event E is defined as P(E) = [Number of favourable outcomes of E]/[ total number of possible outcomes of E].

2. The probability of a sure event or certain event is 1.

3. The probability of an impossible event is 0.

4. The probability of an event E is a number P(E) such that 0 ≤ P (E) ≤ 1. Probability is always a positive number.

5. If A and B are 2 events that are mutually exclusive, then P(A⋃B) = P(A) + P(B).

6. An elementary event is an event having only one outcome. The sum of the probabilities of such events of an experiment is 1.

7. The sum of probabilities of an event and its complementary event is 1. P(A) + P(A’) = 1.

8. P(A⋃B) = P(A) + P(B) – P(A⋂B).

9. P(A⋂B) = P(A) + P(B) – P(A⋃B) .

10. If A1, A2, A3 ,………, An are mutually exclusive events, then P(A1 ⋃ A2 ⋃ A3… ⋃ An) = P(A1) + P(A2 ) + ………. + P(An)

## Random Variables

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1
## H2
### H3
#### H4
##### H5
###### H6

## Distributions

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

## Conditional Probability

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use *Markdown syntax* within a blockquote.

#### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports supports them out-of-the-box.

   Name | Age
--------|------
    Bob | 27
  Alice | 23

#### Inline Markdown within tables

| Italics   | Bold     | Code   |
| --------  | -------- | ------ |
| *italics* | **bold** | `code` |

## Code Blocks

#### Code block with backticks

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
<!-- this line is extraneous 2Error from server (Forbidden): deployments.apps is forbidden: User "chiptest" cannot create resource "deployments" in API group "apps" in the namespace "default" -->
</html>
```

#### Code block indented with four spaces

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

#### Code block with Hugo's internal highlight shortcode
{{< highlight html >}}
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

## List Types

#### Ordered List

1. First item
2. Second item
3. Third item

#### Unordered List

* List item
* Another item
* And another item

#### Nested list

* Fruit
  * Apple
  * Orange
  * Banana
* Dairy
  * Milk
  * Cheese

## Other Elements — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
