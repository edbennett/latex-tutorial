---
title: "Equations"
teaching: 20
exercises: 0
questions:
- "How can we create equations in LaTeX?"
- "How can we make reference to these equations elsewhere in the document?"
objectives:
- "Learn to create both inline and display equations"
- "Understand when each should be used"
- "Learn how to use packages to extend LaTeX's functionality"
keypoints:
- "Equations can be created with the `equation`, `equation*`, and `align` environments, and with `$` signs."
- "Any time you refer to a mathematical symbol, it should be in an equation, most frequently inside `$` signs."
- "Use `\\eqref` to refer to equation numbers within the text."
---

LaTeX's equation tools are arguably the greatest reason for LaTeX's popularity, and are widely imitated. They
are implemented directly in MathJax, a tool used for typesetting equations on the web, and in that guise are used
on thousands of websites, including large ones like Wikipedia. Many of the commands are also implemented in
Microsoft Word's equation tools as AutoCorrects. There are no other equation tools anywhere near as widely
supported and used.

LaTeX divides equations into two categories:

* **Inline** equations: These appear within the flow of a line of text, and are squashed vertically
  to fit while causing minimal disruption to the surrounding paragraph. These are appropriate when
  inserting a short formula or equation, and when referring to individual mathematical symbols
* **Display** equations: These are given their own line, and so can take up more vertical space. They
  can have numbers. These are best suited to longer formulae and all but the shortest equations.



## Inline equations

Let's open a new blank `article` to use as a scratch area. Inline equations are placed in between `$` signs;
everything between two of these is seen to be in "math mode", where a set of commands not previous accessible
become usable. Adjust the new article so that it contains the following:

~~~
\documentclass[]{article}

%opening
\title{}
\author{}

\begin{document}

A mass $m$

\end{document}
~~~
{: .tex}

Now build and view it. Notice that the $$m$$ appears in italic font; this is because LaTeX knows it is a mathematical
symbol. Let's build this up to instead have `m    =1+2`. Build and view this, and you can see that LaTeX has once again
ignored the spacing we placed in the source code, and chosen the most appropriate spacing for the equation entered.

Going back to the main document, look for the `% FIX THIS` comment, and adjust the lines so that the symbols referenced
are in equation environments as we need them to be.

### Superscripts and subscripts

As you might expect, superscripts and subscripts are added using `^` and `_` respectively. However, these only apply
to the next character; if you need more than one character to be superscripted (or subscripted), then you need to
surround the group with curly braces. These can be nested, so you can have constructions like `e^{x^2 + y^2}`.

Let's do this now; find the `% inline equation` comment, and correct the equation to display properly.

### Standard functions

If we try to use a standard function, e.g. sin, we see that it looks like we are trying to multiply the
individual letters $$s$,, $$i$$, and $$n$$. Since this isn't what we want, we precede the `sin` with a `\`
to instead make it a command. This makes it display in the upright formatting that we expect.

### Greek

Greek letters we access with a `\` and then the name of the letter. Both uppercase and lowercase letters are available,
with the exception of those that look exactly like Latin letters. So `\pi` gives us a lowercase $$\pi$$, while `\Pi` gives
us a capital $$\Pi$$. Similarly, $$\infty$$ is `\infty`.

### Fractions and surds

We also have access to fractions, `\frac{}{}`, where the first set of curly braces contain the numerator, and the
second the denominator. We also have `\sqrt{}`, which gives a square root above the contents of the curly braces.

### $$N$$-ary operators

`\sum`, `\int`, and `\prod` should be used for summations, integrals, and products respectively. Add limits using
superscripts and subscripts. These look like symbols for now; in the next section we will see how they differ.
Limits work in the same way; use `\lim` with a subscript.

### Upright text

SI units are generally displayed in upright text, to distinguish them from mathematical symbols. For example, while
$$\mathrm{nm}$$ is nanometres, $$nm$$ could be the product of the two numbers $$n$$ and $$m$$, perhaps a number and a
mass. Similarly, if you want to label a variable with a piece of text (e.g. radial and tangential components of velocity
$$v_{\mathrm{rad}}$$ and $$v_{\mathrm{tan}}$$), these would want to be upright to show that they are text.
If we need to get upright text in a math environment, we can use `\mathrm` to get it.

## Display equations

We create numbered display equations using `\begin{equation}...\end{equation}`. Unnumbered display equations can be created
using `equation*` instead of `equation`. You can choose to number every display equation, or only those you refer to
elsewhere in the document; the important thing is to be consistent about this. It is somewhat more common to number every
display equation; this makes life easier for anyone else referencing your report.

Make sure not to leave blank lines before and after the display equation, since it forms part of the flow of the paragraph.
This is especially important where you have a comma before it, or a lowercase letter (e.g. "where") after it.

The syntax for display equations is otherwise identical to inline equations. The differences appear in the output;
fractions are no longer squashed to fit on the line, but rather the numerator and denominator each take up as much
space as numbers not in a fraction. Similarly, integrals, sums, and products stand taller, and their limits shift
to a more pleasing location.


### Brackets

When we put brackets around a fraction, the result isn't particularly pleasing---the fraction is significantly
taller than the bracket that should enclose it. To fix this, add a `\left` before the opening bracket, and a `\right`
before the closing bracket. Now these will grow as much as necessary to fit their contents.

These don't have to be matched---you can open a round bracket and close a square one. If you want to have an opening
but no closing bracket (or vice-versa), use `\right.` (or `\left.`).

In addition to round and square brackets, you can use `|` for magnitude, `\{` and `\}` for curly braces,
and `\langle` and `\rangle` for angle brackets (e.g. expectation values).

Let's add a display equation to the document now. Place the following equation in place of the comment `% ADD DISPLAY EQUATION HERE`:

$$\frac{\sum_i p_i O(C_i)}{\sum_i p_i} = \langle O \rangle = \lim_{N\rightarrow \infty} \frac{1}{N} \sum_{i=1}^{N} O(C_j)$$


### Multi-line equations

When an equation has multiple steps that need to be on separate lines, we use `align` instead of `equation`.
This lets us use line breaks, `\\`, to start new lines within the equation. Then, we can use `&` to indicate the
alignment point. Typically we will put `&` immediately before the `=` sign (or the inequality sign in the case of
an inequality). If more than one `&` is present on a line, then LaTeX creates two or more columns of equations.

Let's try and make this equation fit into the document nicely:

$$\langle O \rangle = \frac{\int O(x) e^{-\beta ' H(x)}dx}{e^{-\beta' H(x)} dx} = \frac{\int O(x) e^{-(\beta ' - \beta)H(x)} E^{-\beta H(x)}dx}{\int e^{-(\beta'-\beta)H(x)}e^{-\beta H(x)}dx} = \frac{\left\langle O(x)e^{-(\beta'-\beta)H(x)}\right\rangle}{\left\langle e^{-(\beta'-\beta)H(x)}\right\rangle}$$

## Cross-referencing equations

We normally place cross-references to equation numbers in round brackets. Doing this by hand can get tedious, so
LaTeX gives us a separate command, `\eqref`, to do this. However, this is a command invented by the American
Mathematical Society (AMS), and isn't a built-in part of LaTeX. As such we need to import one of AMS's packages
to define the command for this.

We're going to use the `amsmath` package, which we do using the `\usepackage` command. This is done in the preamble.
Just like cross-referencing chapters, we place a `\label` in the equation, and then use `\eqref` when we want to
use the number.


> ## Practice
>
> The only way to get better at writing equations in LaTeX is with practice.
> Get the following equations working in a sample document.
>
> 1. $$r = \sqrt{x^2 + y^2}$$
> 2. $$\partial_x = \frac{\partial}{\partial x}$$
>    
>    (Hint: `\partial`)
> 3. $$\frac{\delta (xy)}{xy} = \sqrt{\left(\frac{\delta x}{x}\right)^2 + \left( \frac{\delta y}{y}\right)^2}$$
> 4. $$r_n = \left(\sum_i x_i^2\right)^{\frac{1}{2}}$$
> 5. $$\mathbf{r} = x\hat{\mathbf{i}} + y\hat{\mathbf{j}} + z\hat{\mathbf{k}}$$
>
>    (Hint: `\mathbf`, `\hat`)
> 6. $$a_\mathrm{radial} = \frac{v_\mathrm{tangential}^2}{r}$$
> 7. $$R_{\mu\nu} - \frac{1}{2}Rg_{\mu\nu} + \Lambda g_{\mu\nu} = \frac{8\pi G}{c^4} T_{\mu\nu}$$
> 8. $$\begin{align}
  \nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} &
  \nabla \cdot \mathbf{B} &= 0 \\
  \nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} &
  \nabla \times \mathbf{B} &= \mu_0 \left( \mathbf{B} + \varepsilon_0 \frac{\partial \mathbf E}{\partial t}\right)
\end{align}$$
>    
>    (Hint: `\cdot`, `\varepsilon`)
>
> > ## Answers
> > 
> > 1. `$r = \sqrt{x^2 + y^2}$`
> > 2. `$\partial_x = \frac{\partial}{\partial x}$`
> > 3. `$\frac{\delta (xy)}{xy} = \sqrt{\left(\frac{\delta x}{x}\right)^2 + \left( \frac{\delta y}{y}\right)^2}$`
> > 4. `$r_n = \left(\sum_i x_i^2\right)^{\frac{1}{2}}$`
> > 5. `$\mathbf{r} = x\hat{\mathbf{i}} + y\hat{\mathbf{j}} + z\hat{\mathbf{k}}$`
> > 6. `$a_\mathrm{radial} = \frac{v_\mathrm{tangential}^2}{r}$`
> > 7. `$R_{\mu\nu} - \frac{1}{2}Rg_{\mu\nu} + \Lambda g_{\mu\nu} = \frac{8\pi G}{c^4} T_{\mu\nu}$`
> > 8. ` `
> > 
> > ~~~
> > \begin{align}
> > \nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} &
> > \nabla \cdot \mathbf{B} &= 0 \\
> > \nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} &
> > \nabla \times \mathbf{B} &= \mu_0 \left( \mathbf{B} + \varepsilon_0 \frac{\partial \mathbf E}{\partial t}\right)
> > \end{align}
> > ~~~
> > {: .tex}
> {: .solution}
{: .challenge}

{% include links.md %}
