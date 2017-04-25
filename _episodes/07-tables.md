---
title: "Tables"
teaching: 15
exercises: 0
questions:
- "How are tables inserted into LaTeX documents?"
objectives:
- "Understand how to create table floats and tables in LaTeX"
- "Notice how numerical results are typically formatted in tables"
keypoints:
- "Tables are held in `table` floating environments, with captions."
- "`tabular` is used to create tables themselves"
- "`&` and `\\\\` are used to separate columns and rows"
- "Numbers and their uncertainties typically share a column."
---

## Table essentials

If you've read many scientific documents you'll have noticesd that tables,
like figures, sit outside the flow of the text, and have captions. This suggests
that just like for figures, we need to use floating environments for tables.
To separate them and make sure that they get their own series of numbers,
we use the `table` environment to create table floats.

Just like with figures, within this environment we need two things: a caption,
and the table itself. Conventionally table captions are placed above the table
rather than below; however, this varies from publication to publication, and 
when writing a journal article you should always check the style guidelines of
the journal before submitting.

> ## Don't screenshot your spreadsheets
>
> While you may feel that you already have your numbers in a table format in
> your spreadsheet software (e.g. Excel or Origin), a screenshot of this is not
> appropriate for a report. Reasons for this:
> 
> * This will use an image file for text data, reducing print quality,
>   increasing the file size, and preventing screen readers from reading the
>   text.
> * Column names (A, B, C, etc.) may be showing, and one or more may be highlighted.
>   In short, aspects of the spreadsheet software will be showing through to the
>   reader. This is a distraction from the data you are trying to present.
>   You want your data to be shown in the best possible light.
> * The visual appearance of the table will not match the rest of the document.
> * Uncertainties in a spreadsheet need their own column; in a table, they should
>   be combined with the value to which they refer. (See below.)
{: .callout}

We can create tables using the `tabular` environment. This has a required argument,
a series of characters specifying the column setup of the table. Allowed characters include:

* `l`: a left-aligned column
* `c`: a centre-aligned column
* `r`: a right-aligned column
* `|`: place a line between two columns

(Other options are available, but these are the main ones you'll need for now.)

Once we are in the `tabular` environment, we can start entering our data. We enter data
left-to-right, top-to-bottom, using the `&` symbol to separate columns, and `\\` to separate
rows. We can add horizontal lines by using `\hline`; multiples of these create multiple lines,
which can be useful e.g. beneath a header row.


## Consolidating numbers

When preparing your data in a spreadsheet, you will be used to putting your uncertainties into
their own columns, separate from the values to which they refer. However, when we are formatting
data for output, we have to consider what the most readable way to present them is. Most frequently
this will be using a single column for both data and uncertainty. You can use either of the conventional
notations: e.g. 1.238(45) or $$1.238\pm0.045$$. Using the former avoids having to create a math
environment, since you don't need the $$\pm$$ symbol. Note that we rarely want more than two significant
figures of uncertainty.

Other consolidations we can consider are factorising out common terms across columns, into the column
header. You will be most familiar with this in the context of units; you are used to placing units
in the column header rather than after every number. You can do the same thing with any powers of ten,
so that there is less visual clutter.

## Mitsuha's data

Mitsuha has copied and pasted some columns from Origin into `table.txt`. Origin pastes nicely into
plain text format, neatly arranging the data into columns, so all we need to do is:

* Format the column headers
* Separate the columns and rows
* Add the `table`, `tabular`, and `caption`, plus any lines we want
* Consolidate numbers for display

> ## Another table
> 
> Try the example in `table2.txt`.
{: .challenge}

{% include links.md %}
