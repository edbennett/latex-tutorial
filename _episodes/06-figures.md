---
title: "Figures"
teaching: 15
exercises: 0
questions:
- "How do I insert figures?"
objectives:
- "Understand how LaTeX treats figures"
- "Know how to insert figures and figure captions"
- "Know how to cross-reference to figures"
- "Know how to make figures fit on the page"
keypoints:
- "Make sure to use the `graphicx` package"
- "Use the `figure` environment to contain figures and captions"
- "Use `\\includegraphics` to place images"
---

You may have noticed when reading journal (or magazine) articles that 
images and their captions typically sit outside the main flow of the text. 
This means that a typical reader may read a paragraph split across two pages, 
that has a figure in the middle. We don't want to lay out these figures on the 
page by hand, so fortunately LaTeX will do this for us. The way it does this
is by using floating environments, or _floats_. You place your images and their
captions into this, and LaTeX decides where best to slot them in.

## Creating a figure float

To begin a figure float, use `\begin{figure}` (and include the corresponding
`\end{figure}`). Within the figure, we want to include our graphics. We do this
with the `\includegraphics` command, which is provided by the `graphicx` package.

> ## `pdflatex` supported figures
>
> `pdflatex` lets you use figures in PNG and PDF format.
> If you used plain `latex` instead, then you would need to use
> figures in PostScript format instead. Since these are not as convenient to
> generate, we choose to stick with `pdflatex`.
{: .callout}

We can now use `\includegraphics{`_filename_`}` to include a figure in _filename_.pdf
or _filename_.png. You can include the extension if you want to be specific, or omit it
if you prefer LaTeX to choose the file for you.

Once we have an image, we then need a caption. This is done with the `\caption` command.

Let's add an image to Mitsuha's results section now. Since LaTeX almost always puts
figures after the point you include them, we'll do this at the top of the results section.

Below the label at the top of the Results section, add the following code:

~~~
\begin{figure}
    \includegraphics{graph}

    \caption{A plot of lorem (in ipsum) against dolor (in sit) for amet and nonummy.}
\end{figure}
~~~
{: .tex}

Build and view the document now.


## Controlling the size of the image

Since the figure currently takes up an entire page, we'd like to make the image slightly
smaller so that LaTeX will fit some text on the page with it.

We do this with a keyword argument to `\includegraphics`, `width`. We can set `width` to
a number, or more usefully to a multiple of various lengths in LaTeX. We'll use a multiple
of the `\textwidth`, or the width of the text on the page.

~~~
\includegraphics[width=0.6\textwidth]{graph}
~~~
{: .tex}

Once this is done, the figure will shift to the left margin. To avoid this happening, centre align it
by adding `\begin{center}` before it, and `\end{center}` after it.


## Cross-referencing to figures

Since figures are not part of the flow of the text, we must make reference to them at the point(s) in 
the text when we want the reader to refer to them.
Just like sections and equations, to cross-reference to a figure, we add a `\label` in the caption,
and a `\ref` at the point we want to refer to it.

> ## Another example
>
> Add the image `diagram.pdf` to the Theory section, with an appropriate caption, and add a sentence
> at the start of the second paragraph calling it out.
> 
> > ## Solution
> >
> > ~~~
> > \section{Morbi euismod dolor nunc}
> > \begin{figure}
> > \begin{center}
> > \includegraphics[width=0.5\textwidth]{diagram}
> > \end{center}
> > \caption{A diagram showing a 3-dimensional lattice, highlighting lorem, ipsum, and dolor.}
> > \label{fig:diagram}
> > \end{figure}
> > As shown in figure \ref{fig:diagram}, ...
> > ~~~
> > {: .tex}
> {: .solution}
{: .challenge}

> ## Positioning the figure
>
> Add an optional argument to the figure: `\begin{figure}[t]`. Build and view the document.
> What changes? What if you change the `t` to a `b`, `h`, or `p`?
>
> > ## Answer
> >
> > You can request to position the figure `h`ere, at the `t`op or `b`ottom of the page, or on its
> > own `p`age. You can stack these to give a list of preferences. If you add a `!` before them,
> > then you demand that LaTeX obey above all other priorities; avoid doing this as it
> > means LaTeX has less flexibility to make the rest of your document look good.
> {: .solution}
{: .challenge}

{% include links.md %}
