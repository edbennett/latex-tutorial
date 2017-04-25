---
title: "beamer"
teaching: 10
exercises: 0
questions:
- "How can we create presentation slides (like PowerPoint) using LaTeX?"
objectives:
- "See how the `beamer` package can be used to create presentation slides"
- "Demonstrate how bulleted and numbered lists can be created"
keypoints:
- "Use the `beamer` class to create a slide deck"
- "Use `\\frame` to create a slide"
- "Use `\\uncover` and `<>` brackets to build up slides."
- "Use `itemize` and `enumerated` for bulleted and numbered lists."
---

We are moving away from Microsoft Word for creating documents; can we also move away from
PowerPoint for creating presentations? Can we get the same high-quality equation formatting
that we have in our LaTeX reports in conference presentations?

Yes; the `beamer` package is designed to do just this.

## A new `beamer` document

Let's create a new presentation so that Mitsuha can present her research at a conference.
The beamer template provided by TexStudio is a little barebones, so let's work with the
following one instead:

~~~
\documentclass{beamer}

\title{Lorem ipsum dolor sit amet}
\author{Miyamizu Mitsuha}
\date{26 August 2016}

\begin{document}
\begin{frame}
	\maketitle
\end{frame}
\end{document}
~~~
{: .tex}

Just like in our report, we have defined the title, author, and date outside of the document,
and used `\maketitle` to create the title slide. This time however the `\maketitle` is inside
a `frame` environment; this environment is how we separate our document into individual slides.


## A typical frame

Let's create another frame now. We'll use the `\frametitle` command to add a title to the top
of the frame. Within the frame, we'll create a bulleted list of points.

> ## Bullets and numbering
>
> While we typically avoid bullet-point lists in reports, which should have a more flowing
> prose style, they are very useful to us when preparing presentation slides.
> Bulleted lists are created with the `itemize` environment, while numbered lists are created using
> the `enumerate` environment. Both can be nested; LaTeX will automatically adjust the symbols to
> distinguish the different levels. Within a list, use `\item` for each item you want to list.
{: .callout}

~~~
\begin{frame}
    \frametitle{Outline}

    \begin{itemize}
        \item Introduction
	\item Theory
	\begin{itemize}
	    \item Morbi euismod dolor nunc
	    \item Donec porta mi turpis
	\end{itemize}
	\item Experimental setup
	\item Results
	\item Conclusions
    \end{itemize}
\end{frame}
~~~
{: .tex}

Build and view, and you can see the bullet points changing size as the points become nested.

## Overlay specifications (making things appear)

Beamer lets you have content that doesn't show up straight away, in the same way you can make points
gradually appear in PowerPoint. To do this, we annotate objects with `<>` signs, with instructions
inside. The simplest is `<+->`, which means "do this on the next iteration of this frame".
We can attach this to a frame; change the `\begin{frame}` to

~~~
\begin{frame}[<+->]
~~~
{: .tex}

Now rebuild the document. You can see that what was one slide has become 7; one for each bullet
point as the frame builds up.

Let's add another frame, this time with some math on it.

~~~
\begin{frame}
	\frametitle{Morbi euismod dolor nunc}
	
	Id ipsum finibus auctor
	\begin{equation*}
	    m = \frac{e^2 \pi q}{3}
	\end{equation*}
	\begin{enumerate}
	    \item Class aptent taciti sociosqu
	    \item Torquent per conubia nostra
      	    \item Quisque eleifend rutrum sagittis
	\end{enumerate}
\end{frame}
~~~
{: .tex}

If we adjust the `\begin{enumerate}` to `\begin{enumerate}[<+->]`, then
the points appear one at a time. What about the initial text? We can use
`\uncover` to make this appear later. Add a `\uncover<4->{` before the
`\begin{equation*}`, and a `}` after the `\end{equation*}`.

Rebuild the document now. You can see that the equation is "covered up"
until after all of the other points are revealed---the `<4->` indicates
"display this thing from the 4th iteration of this frame onwards".

> ## Make your own
>
> Take the most recent lab report you wrote, and create a short beamer
> presentation based on it.
>
> Keep the words on the slide minimal; you don't want an audience to read,
> you want them to listen to you. The words are there as supporting structure.
> Plan to spend about 1 minute per slide.
{: .challenge}

## Themes

You aren't stuck with the default colours and fonts; Beamer lets you change them
all at once. For example, adding the following lines to the preamble will change
the colours to match those of a certain east coast US university, and the fonts
so that math is displayed using serif rather than sans serif fonts:

~~~
\usetheme{CambridgeUS}
\usefonttheme{professionalfonts}
~~~
{: .tex}

{% include links.md %}
