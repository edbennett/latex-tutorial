---
title: "Citations"
teaching: 15
exercises: 0
questions:
- "How can we manage sources that we want to cite?"
- "How do we insert citations in LaTeX?"
- "How do we create bibliographies in LaTeX?"
objectives:
- "Demonstrate how to create bibliographic databases, bibliographies, and citations"
keypoints:
- "Create a bibliographic database in BibTeX, using a reference manager"
- "Create a bibliography using `\\bibliography`"
- "Add citations with `\\cite`"
---

Citations are a vital part of any scientific document. Fortunately, LaTeX has tools to
make life easier for us. We are going to make use of BibTeX, a language for formatting
bibliographic databases for use with LaTeX, which means we don't have to write out the
citations by hand; instead, we fill in details of each publication, and BibTeX generates
the citation in the requested format for us. This then means that if we change citation
format, then we don't need to recreate each citation by hand.

## Preparing a bibliographic database

Fortunately, we don't need to learn a second language when we're already learning LaTeX,
since we can use a BibTeX editor to create our database for us. Most frequently we won't
even need to create the entries by hand, since there are many bibliographic databases
online, which will give us BibTeX to put into our database. The two most prominent examples
for us are:

* [Google Scholar](http://scholar.google.com), which searches all academic publications it can find
* [INSPIRE](http://www.inspirehep.net), specific to particle physics, which indexes only
  publications in high-energy physics, but has more precise and consistent information.

If you are citing published journal articles, these frequently also offer citations in
BibTeX format from the journal's own website.

We are going to make use of JabRef to prepare our databases. On the ISS desktop systems,
this is found in the same place as TexStudio; under the Computer Science section of the
application launcher. If you use a  Mac, you might prefer to use BibDesk instead.
After opening JabRef, we create a new database, and then start adding sources to it.

## Some sources for Mitsuha

We are going to add three sources for Mitsuha: one from Google Scholar, one from INSPIRE,
and one that we create by hand. Let's create one by hand first. Since we used a website
to generate the sample text used in the report, we should cite this. We hit the '+' button
to add a new source, and choose to create a Misc source. We need the following elements:

* Bibtexkey: lipsum (you could choose any key you wanted here, provided you use it consistently)
* Author: lipsum.com
* Title: Lorem Ipsum Generator
* Howpublished: `\url{http://www.lipsum.com}`
* Note: Accessed 2017-03-20

> ## Citations and quotations
>
> Note that if in reality we had copied the entire text of a report from one source,
> we would need to enclose the entire report in quotation marks, and it would not be considered
> your own work for assessment. This is not what we want to do. Please make sure to write
> the contents of your report yourself, and only include short quotations, if and when it is
> appropriate. Note also that even non-quoted material should be cited if you have referred to 
> it when preparing a particular section.
{: .callout}

From [INSPIRE](http://www.inspirehep.net), find the paper with the following title: "Large mass hierarchies from 
strongly-coupled dynamics", as published in JHEP. Notice the "BibTeX" button towards the
bottom of the search result. Click it, and copy the text. Then open JabRef, and click your
first entry in the top pane. Press Ctrl+V to paste, and a new entry is added to the list.

Now open [Google Scholar](http://scholar.google.com), and search for X-Ray Diffraction.
The first entry is a book by Bertram Warren. Let's include this in our database. Go to "Cite" beneath the abstract,
and select "BibTeX". Copy and paste the text into JabRef in the same way we did for
the INSPIRE citation.

Now save this database to a file, `references.bib`.


## Placing citations in your document

Placing citations is simply a matter of using the `\cite` command, with the cite key as
an argument in curly braces.

> ## Multiple citations at once
>
> If you include multiple cite keys in the curly braces, separated by commas,
> then multiple citations will turn up in your document.
{: .callout}

Let's place a citation in the introduction to lipsum.com. Add `\cite{lipsum}` at the end of
the first paragraph.

> ## Citing an image
>
> The diagram placed in the theory section was derived from a textbook figure.
> Place a citation to Warren's book at the end of the caption.
{: .challenge}


## Generating the bibliography

If you were to build the document at the moment, you would get errors, as you are placing
citations but have not told LaTeX which bibliographic database to use.

Add the following two lines to the bottom of the file to tell LaTeX to use an unsorted
bibliography, and to use the `references.bib` file that we created as a source to create
a bibliography:

~~~
\bibliographystyle{unsrt}
\bibliography{references}
~~~
{: .tex}

Since we have added a `\url`, we also need to include a package to define this command. Add
the following line to top of the preamble (before you load the other packages):

~~~
\usepackage{hyperref}
~~~
{: .tex}

Build and view the document now. Notice that only the source(s) that we have cited are
included in the bibliography.

> ## Another figure, another citation
>
> If you click through from INSPIRE to arXiv, you can download the full source for the paper,
> including all figures. Pick a figure, and incorporate it into the theory section of Mitsuha's
> report, including an appropriate caption and citation.
{: .challenge}

> ## natbib
> 
> [`natbib`](http://merkel.texture.rocks/Latex/natbib.php) is a package that enhances some aspects
> of bibliographies and citations; for example,
> it can include arXiv links included in the database, and can arrange it that when you cite a
> lot of articles at once, you get a dash for a range rather than a comma-separated list
> (e.g. [5-12] instead of [5, 6, 7, 8, 9, 10, 11, 12]).
> 
> Adjust your report so it uses `natbib`, whilst still keeping the numbered citation format that
> we use in Physics.
>
> > ## Hint/Solution
> >
> > Add this line to the preamble:
> > 
> > ~~~
> > \usepackage[square,numbers,sort&compress]{natbib}
> > ~~~
> > {: .tex}
> {: .solution}
{: .challenge}



{% include links.md %}
