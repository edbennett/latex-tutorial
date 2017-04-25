---
title: "Structuring your document"
teaching: 10
exercises: 0
questions:
- "How can we add structure to the content we place in a LaTeX document?"
objectives:
- "Understand where to use `\\chapter`, `\\section`, `\\section*`, etc."
- "Know how to create a table of contents"
keypoints:
- "There is a hierarchy of subdivisions in a document, from `\\chapter` to `\\section` to `\\subsection` to `\\subsubsection`."
- "Tables of contents and other cross-references can be generated automatically by LaTeX."
---

We have a document that renders to a PDF; now we'd like to impose some structure on it. 
Of course, we can't add structure to a document without some content to give structure to. 
Open up `source.txt` and copy and paste it into the document, just above the `\end{document}`. 
Build this document now; you can see we get a sea of paragraphs, just dying for us to give them some
structure. Before we do this, though, we should notice something about the paragraphs.

On the left, you can see that there are numerous line breaks present, but they do not appear
in the finished document on the right. In fact LaTeX ignores any single line breaks, since 
they are frequently present to improve how the source code appears in a text editor rather than
having anything to do with the final structure of the document. To create a paragraph break,
you can see that we need to use two successive newlines.

Notice also that some groups of words in the source code have more than one space between them. 
Looking at the corresponding sections in the preview, no such funky spacing appears. This is because
LaTeX takes full responsibility for spacing your document; when it comes to spaces between words,
LaTeX knows best. One or more spaces is an indication to LaTeX that there should be a gap between words,
but LaTeX decides how big it needs to be. This then means that you can use spaces in your source file for 
other purposes, such as lining up content nicely or indenting subsidiary blocks.


## Creating structure

In a project report, we typically want to divide the document into chapters, which in turn divide into
sections. (In a shorter report we might only want to use sections, in which case the `article` class 
would be more appropriate.) While you might start reaching for the font size and bold buttons, we 
want to avoid doing this in LaTeX---there are significantly easier and more powerful options available
to us.

To create a chapter heading, we can use the \chapter command, with the heading as its only argument. 
In the `report` class, chapters are numbered 1, 2, 3, etc. (This is similar to using the Heading 1 style
with outline numbering enabled in Microsoft Word, if you are familiar with this.) A new chapter
also starts a new page.

Mitsuha has indicated where she wants to have chapter breaks in her document with a comment, `% NEW CHAPTER`. 
Let's go through and add chapter titles at each point that this comment is seen. Once this is done, we 
Build and view the document to check that everything works.

Before:

~~~
% NEW CHAPTER
Introduction

Nulla porttitor sapien tellus...
~~~
{: .text}

After:

~~~
\chapter{Introduction}

Nulla porttitor sapien tellus...
~~~

> ## Build and view regularly
> 
> The usual editing cycle of a LaTeX document is to add a few paragraphs or make a few changes to the document,
> then build and view to check that it still builds. Any errors that arise are fixed, and then the cycle
> begins again.
{: .callout} 

A section heading works the same way, using the `\section` command. In the `report` class, sections are 
numbered x.1, x.2, x.3, etc., where x is the number of the current chapter. New sections don't get their 
own new page. Let's go through and add section headings wherever Mitsuha has placed a `% NEW SECTION` 
comment. Build and view again once this is done.

If we wanted, we could have further subdivisions, `\subsection` and `\subsubsection`, which work in the same
way.

## Tables of contents

We'd frequently like to include a table of contents in our documents, especially once they start getting long, 
so that the reader knows where to find things. This is one area where LaTeX makes our lives really easy.
We can create a table of contents using the `\tableofcontents` command. Place this just after the abstract, 
so it is the first thing in the document proper. 

Build and view this, and you see that LaTeX automatically lays out the table of contents to highlight the 
structure of the document, with subdivisions indented within their parents---sections within chapters,
subsections within sections. This is automatically generated when we build the document, so we don't 
have to go through collating page numbers.


## Cross-references
Frequently we will want to refer to other parts of the document, a process called _cross-referencing_. 
Historically to do this we had to work out the numbers and enter them by hand, updating them if the 
structure of the document changed. LaTeX, however, has our back on this.

We will need two commands here, `\label` and `\ref`. `\label` creates a label, or a location to which 
we can refer. We place this at the point in the document we want to be able to make reference to, defining
a name we will use to refer to it. Normally we place this directly under the relevant heading. 
Then, at the point we want to reference that material, we use `\ref`, 
using the same name, and LaTeX inserts the number of that element.

Mitsuha would like to refer to each chapter in her introduction; search for `xxx` to find the elements to replace. 
Let's add a `\label` on each chapter, containing a summary of its title, and then add `\ref`s to the introduction. 
Build and view to check that it works.

> ## How LaTeX does it
> 
> Notice that we have placed the references to the label here before the relevant labels. Since LaTeX works
> through the document top to bottom, you might think that this wouldn't work. In fact, what LaTeX does here
> is to run twice, firstly for an initial attempt at the layout, saving a list of the things if doesn't know, 
> then on a second pass, filling in the blanks. Should this change any numbers, then it saves these and 
> performs a third pass to correct these.
> 
> If you run LaTeX by hand from the command line, you will need to notice when LaTeX requests to be run again.
> When you use TexStudio, it does this automatically for you.
{: .callout}

> ## References to sections
> 
> References to sections work very similarly to references to chapters. Search for `yyy` to find a chapter that 
> introduces all of the sections within it. Insert `\label`s and `\ref`s in appropriate places to make these
> work. What differences are there to referencing chapters?
{: .challenge}

## More divisions

### Unnumbered divisions

Sometimes you need to have divisions or headings without numbers; for example, normally a References section
won't have a number on it. For this, we use a `*` after the command; for example `\chapter*` creates a 
chapter-level division without giving it a number.

Such divisions also won't appear in the table of contents.

### Appendices

Appendices are treated in exactly the same way as normal chapters. At some point in your document, you decide
that you no longer want chapters, but instead appendices. Here you place the `\appendix` command, and from this 
point forward, all `\chapter` commands instead create appendices.

Let's do this for Mitsuha's document; in general the Conclusions will be the final section of body, so 
the subsequent discussions must be appendices. Insert the `\appendix` command immediately before the next
`\chapter` after the Conclusions, and build and view.

{% include links.md %}
