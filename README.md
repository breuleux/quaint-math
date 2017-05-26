
# quaint-math

Simple and extensible math mode.

## Install

In your Quaint project directory, run the command:

    quaint --setup math


## Usage

The plugin defines three operators:

* `$+[...]` inserts math inline
* `$$ ...` displays one or more equations
* `$@ref` inserts a reference to an equation
* `<pattern> $=>$ <rule>` defines a substitution rule

`quaint-math`'s math syntax is simple, concise and powerful, but may
not cover everything you would want it to. Thankfully, you can embed
math that uses LaTeX syntax by surrounding it in {}s.


## Example

In this example, we define `a` and `b` so that they display as the
greek letters alpha and beta, and we alias `PX(x)` so that it displays
as the probability `P(X = x)`.

```
a $=>$ {\alpha}
b $=>$ {\beta}
PX(\x) $=>$ Prob(X = \x)

$$ Sum(a in S, PX(a) a^b)
```

This is equivalent to the following LaTeX:

```
$$ {\sum_{\alpha \in S} P(X = \alpha) \alpha^\beta}
```


## Syntax

**The syntax is still a work in progress.** More will be added as the need arises.

### Symbols

Certain common symbols can be written using a single word, without the
need for a backslash.

* `in` => `\in`
* `forall` => `\forall`
* `exists` => `\exists`
* `infty` => `\infty`

### Sums and limits

The functions `Sum`, `Prod`, `Int` and `Lim` all map to the
corresponding mathematical operators (sum, product, integral,
limit). They take one or more bounds, and a body. The three forms of
the call are illustrated for `Sum` below:

* `Sum(from, to, body)` => `\sum_{from}^{to} body`
* `Sum(from, body)` => `\sum_{from} body`
* `Sum(body)` => `\sum body`

### Grouping

* `[...]` is an invisible grouping, equivalent to `{...}` in LaTeX
  (although this is not coherent with LaTeX's syntax, this is coherent
  with Quaint's)
* `{...}` switches to LaTeX syntax.
* `[[...]]` displays square brackets.
* `[[[...]]]` is equivalent to `{\left\[...\right\]}`
* `{{...}}` displays curly brackets.
* `{{{...}}}` is equivalent to `{\left\{...\right\}}`
* `((...))` is equivalent to `{\left\(...\right\)}`

### Special operators

* `a / b` => `\frac{a}{b}`. You can write `a [/] b` if you want a
  literal slash character.
* `a_b` is a subscript.
* `a^b` is a superscript.

