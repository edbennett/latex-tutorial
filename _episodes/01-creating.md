---
title: "Creating a document"
teaching: 10
exercises: 0
questions:
- "How do we create a new LaTeX document?"
objectives:
- "Create a new report from a template."
- "Set the title and author."
- "Compile the document."
keypoints:
- "Start with a template"
- "Prioritise structure over formatting"
- "Compile to view the formatted output"
---

LaTeX is a language for creating scientific documents. In fact it might be better to call it
__the__ language for creating scientific documents; much its syntax has been borrowed by
other environments, in particular where creating anything involving mathematical expressions
concerned.

Writing a LaTeX document is a little like writing a computer program, or a web page: you write
your text, marked up with commands to specify its structure. You then compile this with a
LaTeX interpreter, and it generates an output file that you can view on screen or print---
most typically a PDF file. As such, just like with programming languages,
there is a wide variety of programs available for writing
LaTeX code, from bare text editors to feature-rich development environments.
Today we will be using TexStudio for this purpose.

## Starting TexStudio

TexStudio is installed on the ISS desktop system under Specialist Apps > College of Science >
Computer Science > LaTEX. Double-click it, and it will launch. The first time it launches on a machine
it will need to install itself, which may take a few minutes. If you use open-access PCs for
writing LaTeX, you may want to always use the same one, so that you don't have to wait
every time.

On your own machine, once installed, TexStudio is available from your application launcher.


## Using a template

Every dedicated LaTeX editor comes with a suite of templates to work from. Even most long-time LaTeX
users don't remember how to create a blank document from scratch, so there's no shame in starting a
new document from a template. Every editor's templates are slightly different; some are more intricate
than others, but all follow the same basic format of filling in the blanks to get a document ready
to begin working on.

Select File > New from template... to get a list of templates that TexWorks provides. We're going to use
the `Report` template for now. Double-click it to start a new report. The following code comes up:

~~~
\documentclass[]{report}


% Title Page
\title{}
\author{}


\begin{document}
\maketitle

\begin{abstract}
\end{abstract}

\end{document}
~~~
{: .tex}

> ## Other classes
> 
> For shorter documents you generally want to use the `Article` class instead.
> The `Scrreport` class gives a different style for the same structure.
> You can create PowerPoint-style presentations using the `Beamer` class.
{: .callout}

> ## Online templates
>
> Sometimes the basic templates that your editor provides will be insufficient.
> For example, for a PhD thesis there is a lot of pro-forma material at the front
> that you don't want to write out from scratch. For this you can download pre-prepared
> templates online. A template for a Swansea thesis is available [here]({{page.root}}/files/thesis-template.zip)
>
> Another example would be the `a0poster` class, which lets you create large-format
> scientific posters to present at conferences (and elsewhere). TexStudio doesn't give
> you a template fot this; however, various are available to download online.
{: .callout}


## The LaTeX language

Looking at the code the template gives you, you can see a few things about the LaTeX language.
It has commands that start with a backslash `\`, and which take arguments specified in curly 
braces `{}`. On the first line you also see some square brackets, `[]`, which allow optional
arguments to be specified. Comments begin with a `%`, and end at the end of the line.
Specific commands we see:

* `\documentclass` specifies which "class" of document you will create. This sets all kinds of
  options inside LaTeX, including whether the document has chapters, what text sizes and fonts
  are used, the document's margins, etc. As well as the class, optional arguments can be given
  to override the defaults for some of these 
* `\title` and `\author` specify what their names suggest.
* `\begin` and `\end` start and end particular environments. Here we see that we can start and end
  the document, and the abstract. We will see more of these as we go through the tutorial. 
  Notice that the title and author are specified before we begin the document, in a space known
  as the "preamble".
* \maketitle takes the title and author as set above, and creates a title area. It also includes
  the date, and in the case of the `report` class, also adds a page break to create a title page.

> ## Why not type the title and author in the document?
>
> LaTeX can do all sorts of things with the title and author, such as put them in a running header
> or footer. To do this, it needs to know them.
> 
> This highlights an important part of the way of thinking you need to keep in mind when writing
> LaTeX: you tell it the structure of the document, and it handles the formatting for you.
> If you had formatted the name and author by hand with bolds and font sizes, then LaTeX couldn't
> do that magic for you.
{: .callout}


## Filling in the blanks

For the purposes of this tutorial, I'll assume the identity of Miyamizu Mitsuha, who is writing a report
about Lorem Ipsum Dolor Sit Amet.

> ## What is this gibberish?
>
> It is conventional in publishing to use this nonsense Latin-looking text ("lorem ipsum" text) as a placeholder when the
> final text is not available. This allows the shape of the final design to be seen (rather than having
> large blank spaces where text should be), without having incorrect text distracting from the design.
> Unlike a simple sample sentence repeated, it doesn't have patterns that would cause visual distractions.
> Since we are focusing on formatting rather than report writing in this tutorial, we use lorem ipsum
> text so that our attention isn't split between the English text and the LaTeX syntax.
> Where necessary, the occasional English sentence will be thrown into the mix for clarity.
{: .callout}

Fill in the empty curly braces with the following details:

* Author: Miyamizu Mitsuha
* Title: 

## Compiling the document

To view the output so far, hit the Build & View button ![the double green triangle](../fig/buildview.png) on the menu bar.
This will compile the document to PDF, and open a preview pane showing the output on the right.

Scrolling down, we see that the abstract is missing; we need to add some text. To do this, download
[this files]({{page.root}}/files/files.zip) and extract it. Copy and paste the contents of `abstract.txt` between the
`\begin{abstract}` and `\end{abstract}` elements. Now recompile the document and see the abstract appear.

> ## Other document classes
>
> Try switching out `report` for `scrreport`, and recompiling. What difference does this make to your document?
> What about `article`?
> 
> Switch back to `report` before continuing.
{: .challenge}

> ## Getting rid of the date
>
> Frequently we don't want to have a date on the front of the document. LaTeX gives us a `\date` command
> to set what date should be displayed. Use that now to remove the date from the front cover. Think
> about where in the source file it should be placed.
{: .challenge}

{% include links.md %}
