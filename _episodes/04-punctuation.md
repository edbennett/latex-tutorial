---
title: "Punctuation"
teaching: 10
exercises: 0
questions:
- "What care do we need to take when punctuating?"
objectives:
- "Understand how to insert accented characters"
- "Know how to use symbols"
keypoints:
- "Accents are placed with an appropriate `\\` command before the character to get the accent"
- "Opening quotes are single or double backtick (`` ` ``) characters."
- "Common LaTeX commands can be prefixed with a `\\` to make them display as text"
---

Because of its heritage, there are a few idiosyncracies to be aware of when punctuating LaTeX.

## Accented characters

Because LaTeX was designed on computers that didn't support accented characters, it doesn't support
files containing them by default.

To insert an accented character, we insert a character representing the accent before the character we
want the accent to apply to. For example, to type an ö, we use \"o. The most common ones are:

* ç: ``\c c``
* é: ``\' e``
* ô: ``\^ o``
* ö: ``\" o``

> ## Support for accented characters
>
> The standard for text containing accents and other foreign language characters (e.g. Japanese)
> is called Unicode. (This is the same standard that brought emoji out of Japan.)
> If you swap `pdftex` for other renderers like LuaTeX or XeLateX, then you can get support
> for Unicode in your source files. The trade-off is that some packages work differently,
> and it isn't the default on most distributions. We're learning with `pdftex` because it
> is the simplest, most widely-used option, and because in English we'll rarely need to type
> accented characters.
{: .callout}

Mitsuha has written Poincare and Schrodinger in her report when she meant Poincaré and Schrödinger;
let's correct that now.

## Quotation marks

Because LaTeX can't tell when you want an opening vs a closing quoation mark, it relies on you to
tell it. When you pass it a `'` mark, it assumes that you mean a closing quote, and display it as such.
If you want an opening quote, then you must use `` ` `` instead. For double quotes, use two backticks.

Mitsuha has some quotations in her report that show using the wrong symbols; let's fix those.

## Dashes
The `-` symbol renders as a hyphen. This is good for hyphenated words (e.g. X-ray, $$g$$-factor, etc.), but
for sentences, we need dashes rather than hyphens. For an 'en dash' (used between numbers), use two hyphens.
For an 'em dash' (used between words), use three hyphens. These render as dashes of the appropriate width.

## Other symbols
Some common symbols have been co-opted by LaTeX to have a specific meaning. Generally in these cases we can
place a `\` before these and they will display correctly. For example, `\$` for a dollar sign (rather than
starting an equation), and `\&` for an ampersand.

LaTeX assumes that after a full stop, some extra space is wanted to separate sentences nicely.
However, in some cases you'll use a `.` for something other than ending a sentence. In these cases, you can
follow it with `\ ` instead (e.g. after e.g.), to show that you want a normal-width space. You can also use a `~`
in cases where you don't want LaTeX to break a phrase apart at the end of a line.
