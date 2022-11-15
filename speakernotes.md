# How to Create a LaTeX Report Without Losing Hair
Eirian Perkins

RezBas 2021

## Hour 1

# Introduction

- intro 
- I'm a LaTeX enthusiast
- my goal is to share all the tips I wish I had when I started my PhD
- I hope this is helpful

## Pre-Indtroduction

- What is LaTeX
    - LaTeX is a document preparation software system
    - widely used in academia
    - using LaTeX feels more like programming
- Why would I want to use it?
    - more control -- fine tune look and feel, use it with Git (version control), collaborate
    - distraction-free environment
    - reference mangament
    - once you know the tool, preparing a document is **FAST**

## Goals

In today's workshop, you will learn to...

- create an article or a book (thesis)
- manage references
- gain confidence debugging errors

## Caveats

- this is intended to be an intermediate-level workshop
- if you're not familar with LaTeX, don't panic
    - ask questions instead!
    - this will help others
- the template is a work in progress
    - I update it every year after getting feedback at ResBaz
    - Please help me improve it by asking for more examples

## Examples

- look at samples (compiled PDFs, e.g. solaR, PYR, minutes with Anna)
- intent: whet your appetite for learning
- (here's what you'll be able to do by the end of the session)

## Getting acquainted with Overleaf

- Everything I will be showing you today, you can do locally (without overleaf)
- If you'd like to learn how to do this, please come to my other LaTeX session
- working locally will help you get your work done more quickly, in an 
  environment with fewer distractions,
  - and enable more features (like minted, sagetex, and git)

Logging in 

- use your UoA login or, if you don't have one, create an account
- upload a zip or file by file to a directory
    confusing 
  - go to `https://github.com/eirianop/ResBaz2022_LaTeX_noHairLoss`
  - `download zip`
  - OS X - may have to turn it into a zip again
- Overleaf: create new project
  - upload zip



## Basic Structure of a LaTeX document
```
┌── preamble
└── body
```

- preamble is where you do your configurations
  - what kind of document do I want to make?
  - e.g. is it an article? is it a book?
  - what is the style like?
  - can I click on links?
  - what colours do I want?
  - what do my chapter headers look like?
- after you set up the configurations, then you have the body
  - the meat of the work, the actual content
  - I like the cognitive distinction between formatting and content,
    because it helps me focus when I write. \LaTeX{} helps provide
    a distraction-free environment
  - one reason writing docs in \LaTeX{} can go so much more quickly
    than in, say, MS Word. Your settings in the preamble will largely
    take care of the look and feel of the document.
- you can import files for your preamble, rather than dumping
  everything into your main .tex document
- you can split your settings into multiple files, if you like
- these are typically .sty or style files

## What we will cover today

- article class
- book class
- many other examples, but this is what we'll learn about today

```
┌─┬─ preamble
│ ├─┬─ document class
│ │ ├─── article
│ │ └─── book
│ └─── style
└─┬─ body
  ├─── title
  ├─── ToC
  ├─── main document
  ├─── appendices
  ├─── glossary
  └─── bibliography
```
Let's take a look at how this is structured in the code

- build the template
- there are many more things you can put in a document
- we will build a couple examples together today
- decided to cover the above based on: when I write a \LaTeX{}
  document, what do I do the most?
- `In addition, I will also show some cool features, including`
    - `TODO lists`
    - `timelines`
    - which I have implemented manually in our style template
- I will build this with you in a live demo, versus showing 
  all the code and saying "this is how it works"

---

# Recap

- open document.tex
- look at the pre-amble
- show how it is structured
  - images
  - pages
  - template 
  - main tex document and bibtex
    - my preamble and body are all in document.tex
    - all my chapters are in my `pages` directory

main tex document

- preamble
- document start (the meat of the document)
- table of contents
  - chapter imports
- glossary
  - currently commented out
  - %'s add comments
  - we'll get to this
- my appendices 
- my bibliography

easy as, right? That's all there is to it

- show off again, that just with this one file, 
  you have this entire template (PDF)


---

# Example 1

What I want to do is some collaborative coding to do our first report

- pause for questions
- we don't need to rush

Scenario

- I'm a new PhD student and I have been given the task of performing
  a literature review

Goal

- create an electronic research notebook to log my progress
  - create a notes template for the articles I have read
  - `TODO: create a goals checklist to keep myself on task`
  - start populating it

First things

- start modifying the template I have
- decide if I want single column or multi-column
- decide if I want a report (no chapters) or a book (chapter)
- create a new file for each section (page) I want to include
  in my report

`copy 00_pagetemplate.tex to 01_literature_notes.tex`

- comment out subfiles in main tex document
- we don't need these anymore, was just a preview of things to come
- add our new file `\subfile{pages/01_literature_notes.tex}`

In my head I'm thinking, how do I want to structure my document?
What sections will I need? We can think this through in our 
`document.tex` at a higher level, because we're including chapters
here rather than explicit content.

- I want a notes chapter to capture what I've learned about existing 
  work. I'll be able to refer back to my notes as I'm writing my
  manuscript. I can add citations as I go so that I don't need to 
  keep all my references and the sources that stood out in my brain.
- I have my own "convention" here 
  - templates start with `00` (or, in this demo, `01`, `02`, etc.)
  - new files, with real content, start with `YYYY-MM-DD`
  - this helps me distintuish between content and templates
  - ...and lets me see, at-a-glance what progress I've made to date

Open our new files for editing

## 01_literature_notes.tex

- let's think of what would be a good format for writing up our notes

document.tex
```
\documentclass[openany,onecolumn,oneside,english]{memoir}
```

- I've chosen a memoir class
  - this is like a book, it has chapters, sections, subsections,
    and so on.
  - after this workshop, you should have a play around 
    with other document classes to see what is possible
- the items in square brackets are documentclass options
  - you can specify papersize and format and so on.
  - `openany` refers to which hand side of a page a new chapter opens
    to. The default behaviour is that chapters only open 
    on the right hand side.
  - `onecolumn` refers to how many columns are in our document
  - `oneside` refers to whether a document is single-sided or
    double-sided. Since I'm only viewing on the computer,
    one-sided looks more natural. Remember to change this for
    printing! You will leave enough space for the binding, which
    `twoside` helps with
- one thing to point out here
  - I make a conscious effort to document what the options I 
    select do. It is easy to forget and become disorganized.
    This is code. Document as a habit :) 


Now, to help us with our literature review, let's create a chapter 
template for notes on each of our references.
(modifying `01_literature_notes.tex`)

```
\documentclass[document.tex]{subfiles}
\begin{document}

\chapter{Literature Notes}

% make a template for each of my references
\section{template}

% summarize every article I've read
\subsection{Summary}

% questions specifically related to the article
\subsection{Questions}

% why is this relevant?
\subsection{How This Relates to my Research}

% Other important details
\subsection{New Vocabulary and Concepts}

\end{document}
```


At this point, let's preview what our notebook looks like 

- demonstrate how to compile in Overleaf
- I have my ToC
- I have my literature notes
- Oh! and I have an appendix!

Do I need an appendix at this point? Probably not.

- let's try to remove our appendix ourselves 
  (not recommended for medical emergencies)
- this is an example of debugging
- `ask participants where to look`
  - has anyone been able to do this in overleaf?
- answer: in our main tex document

Remove the following:

- \appendixpage
  - the single page that says Appendices
- \label{appendixpage}
  - this is a label we can refer to when making clickable links
  - really great for referring to sections, figures, etc.
  - we need a label for creating a hyperlink
- \subfile{pages/0A_appendices.tex}
  - the actual appendix chapter we want to remove

Recompile, now the document is compiling as expected
- also demo, compiling a single page
- one shortcoming is the chapter doesn't get renumbered
  - if you come to my other LaTeX session, I will show you
    how to get around this automagically!
  - but for now, we'll just live with it


Alright, back to our template

- we decided we wanted to make a book, meaning we have chapters
  (unlike a report, that only goes up to sections)
- we created a new template file for each section
  - this will help getting us up and running quickly. 
    We can simply copy the template for each new reference
    we want to take notes on

Now that we have a template, I can demonstrate populating it

- first, we need to add a reference
- open `documentRef.bib`. It's in our main working directory
- we will be able to refer to a citation in any of our
  tex documents with a unique key. 
  - it's valuable to decide on a convention with naming
    keys. I believe this reduces my cognitive load when the
    key names are consistent and memorable
  - personally, I have an iPad where I do all my reading.
    How do I keep the documents I have there in sync with
    my bib document?
  - the way I do it is how I name my documents
  - first 3 letters of first author's last name
  - first 3 letters of second author's last name (if there is one)
  - and the year published
    - that's not always unique, so I may start adding  `a, b, c` 
      etc. to the end of keys
  - it took me a while to find a system that worked for me
    - find what works for you and stick to it

```
@article{JosArc2018,
  author           = {Cabeller, Armando and Garc\'ia-Dorando, Aurora}, 
  title            = {Allelic Diversity and Its Implications}, 
  journal          = {The Genetics Society of America}, 
  volume           = {195}, 
  pages            = {1373-1384}, 
  doi              = {my_great_doi},
  year             = {2013} 
}
```

author field

- `lastname, firstname and ...`
- there's no comma between author names
- `and` is the delimiter. This may be confusing initially
- the syntax for adding accented letters is a little funny
  - it's the same as LaTeX syntax
- my favorite reference for looking up accented letters
  - https://tex.stackexchange.com/questions/8857/how-to-type-special-accented-letters-in-latex

title

- the important thing to remember here is we need extra braces
  in order to get all caps
  - `{Allelic Diversity and Its Implications DNA}` will actually
    make DNA lower case, we need extra braces:
  - `{Allelic Diversity and Its Implications {DNA}}`

DOI

- remember to add this field
- omitting actual DOI here for brevity


```
@article{JosArc2018,
  author           = {Cabeller, Armando and Garc\'ia-Dorando, Aurora}, 
  title            = {Allelic Diversity and Its Implications}, 
  journal          = {The Genetics Society of America}, 
  volume           = {195}, 
  pages            = {1373-1384}, 
  doi              = {my_great_doi},
  year             = {2013} 
}
```

Bibliography
  - you can also use Zotero
    - https://www.nature.com/articles/d41586-022-03675-8 
    - as an example
    - export citation
    - bibtex or biblatex
    - you may have to fix it up, export is not perfect
    - so let's look at the different fields to understand them



Now, make a copy of our `01_literature_notes.tex` template

- e.g. 2021-11-21-JosArc2018.tex

```
\documentclass[document.tex]{subfiles}
\begin{document}

\chapter{Literature Notes}

\section{\citet{JosArc2018}}

\subsection{Summary}
fixation and differentiation are independent concepts

\subsection{Questions}
how can I learn all the maths
(is anyone laughing? are you all on mute?)

\subsection{How This Relates to my Research}
I want to investigate differentiation

\subsection{New Vocabulary and Concepts}

\end{document}
```

I will come back to new vocab in a moment, but first, I want to
do a preview

- if you get a questionmark for the section title, try 
  recompiling
- we can talk about changing the citation style later
  (this is different for natbib and BibLaTeX, depends on
  which tool you choose)

The thing is, it only tells me so much to have the author name
as the section title. It would be more informative if this instead
were the title of the work.

To figure out how to add this, I went to Google (as one does), and
Google told me to add 

```
\citetitle{JosArc2018}
```
 let's give that a go and see what 
happens...

- nothing meaningful shows up for my \citetitle command
- and I get a red X telling me `undefined control sequence`
- what the blazes does that mean?
  - we can click into `logs and output files` to learn more
  - `the control sequence at the end of the top line of your error message
    was never defined`

What we're being told, is that `\citetitle` doesn't exist. 
How is this possible? Did Google lie to us?

What's going on is, if we nip into our style file, we are using the package
`natbib`.

There's different packages for controlling our bibtex. 
I'm using `natbib` as an example here, why?
Because I was googling (as one does) to figure out how to 
add citations, and I found working examples.

This is a valid way to work through challenges in LaTeX.
But it turns out, there's multiple ways to accomplish 
a task, and sometimes I need to know a little bit more 
about what's happening "under the hood."

`natbib` is widely used. It's fast, and is a popular package.
However, it's not actively maintained, and has some limitations.
- great Q&A here
- https://tex.stackexchange.com/questions/25701/bibtex-vs-biber-and-biblatex-vs-natbib

More to the point, I don't know how I would pull out the title 
of a reference from natbib. So I want to use a different package.

Let's use `biblatex`, which does support the `\citetitle` command.

So taking a step back, when I went to Google, and I saw the 
recommendation for `\citetitle`, it was implicitly a recommendation 
for using `biblatex`.

- when we find answer on Q&A sites, we might be getting answers for 
  packages we're not using. So be aware of the requirements
- this advice will help you write professional reports without
  losing hair!!!
  
Let's use `biblatex`
  - remember anything in the curly braces is what you import
  - and anything in the square brackets are options
  - let's use `natbib=true` for compatibility with natbib
  - `style` has lots of options, for instance `apa`

```
\usepackage[style=numeric, natbib=true]{biblatex}
```

In the style file provided to you, you'll see I use the
`backend=biber` option. Biber is a replacement 
for the widely-used BibTeX software. 
 - It has expanded functionality and technical improvements 
   over BibLaTeX. For instance it offers
   full unicode support.
 - my personal recommendation is to use biber


Now that we've switched from `natbib` to `biblatex` we need to 
modify our `document.tex`. I have provided the necessary
`biblatex` commands in comments so that it's easy to 
switch out `biblatex` for `natbib`

- hint: search for `bibtex` in document.tex to find every 
  location that needs to be changed

Recompile, and check that we get the title as expected

---

## Ok, everyone take a deep breath


## Q&A

Let's pause for Q&A before taking a break

- anything you'd like more of?
- any questions?
- just press on after we finish?

## (stretch) Creating a TODO list

(if we don't have time, can cover in 2nd example)

Sometimes we'd like a feature that's not supported out of the box.
Let's suppose we want to create a TODO list, for setting goals and 
keeping focus.

- how can we create such a list?
- for me, a good first step is to google around and see if I can learn 
  what other people have done
- so, after some googling, I found this answer:
- https://tex.stackexchange.com/a/313337

Modifying our style file

- We could copy the code and paste it in our document.tex preamble
- if we want to keep document.tex neat and tidy, a better place to 
  put this code is inside our style
- (actually, I have already done this for you)
- go to line 150
- I won't overwhelm you with the implementation details here, the 
  main point is that we can add commands and keep them tidy
- another important point is to leave yourself minimum working 
  examples (MWEs) so that you know how to use these commands
- I have shown this in the comments

Let's expand out our page template

```
\section{Daily Goals}
\begin{todolist}
  \item[\done] frame the problem
  \item write solution 
  \item profit
\end{todolist}
```

Or maybe we decided not to profit

```
  \item[\wontdo] profit
```

---

## Break

`10 minute break`

---

# Hour 2

Welcome back!

- In the first hour, we put together a template for a research notebook

Quick overview of what we've learned so far

- we went over the basic structure of a LaTeX document
  - main 2 components: preamble and body
    - (show preamble in `document.tex`)
    - (show `.sty` file, where we can set up other 
    configurations, *and* keep them organised)
    - (emphasize taking notes and organizing `\usepackage`)
  - body
    - we kept it simple in `document.tex`
    - ...by including documents in our `pages` directory
    - That way, our `document.tex` _describes_ the look and feel of
      our work
    - rather than being cluttered with a mix of content
- we went through our first scenario
  - I am a new PhD student, and I want to keep a research notebook
    (e.g. initially for my literature review).
  - here's a schematic of what we built so far

```
┌─── preamble
└─┬─ body
  ├─── title
  ├─── ToC
  ├─── main document
  ├─── appendices
  └─── bibliography
```

Remember we have to `recompile` to see updates

- let's compile again to stay up to date with our changes
  - recall, in the last hour we learned about different bibtex back end
    options (the tool used to make bibliography sources available to 
    your tex documents)
  - we switched from natbib to biblatex, because biblatex provides
    more features
  - whichever you use is up to you
  - ...but if you're getting insights on LaTeX from google searches,
    you need to make sure you know which packages are required for
    the examples you come across
  - let's go ahead and change our section name
  - `\section{\citetitle{JosArc2018}}`
    - this will make it easier for me (as a researcher) to go back and
      look at the different topics I took notes on
    - we can also use `\citefield`
    - key name is the first argument
    - field is the second argument
    - example:
    - `\section{\citefield{JosArc2018}{title}}`
    - `\section{\citefield{JosArc2018}{journaltitle}}`

And, back to our 01_literature_notes.tex

```
\documentclass[document.tex]{subfiles}
\begin{document}

\chapter{Literature Notes}

\section{\citep{JosArc2018}}
\section{\citetitle{JosArc2018}}
\section{\citefield{JosArc2018}{journaltitle}}

\subsection{Summary}
fixation and differentiation are independent concepts

\subsection{Questions}
how can I learn all the maths
(is anyone laughing? are you all on mute?)

\subsection{How This Relates to my Research}
I want to investigate differentiation

\subsection{New Vocabulary and Concepts}

\end{document}
```

Some other concepts

- making bulleted lists
- (compile example)

```
\subsection{New Vocabulary and Concepts}
\begin{itemize}
  \item{demes}
  \item{allelic differentiation}
\end{itemize}
```

we can also make enumerated lists:

- (compile example)
- these are built-in features
- unlike our `\todolist` which we implemented manually

```
\subsection{New Vocabulary and Concepts}
\begin{enumerate}
  \item{demes}
  \item{allelic differentiation}
\end{enumerate}
```

Now...

- Here I'm capturing new vocab and concepts
- ...but it would be great if I had a snapshot page that 
  gave me a summary of all of it
- Putting all of these concepts into a glossary would serve this purpose

Calling this out

- this is a part in particular I am not claiming to be an expert
- there's 5 different ways to set up glossaries.
  - I picked the one that was easiest to set up
    - this is `option 1` in the user manual
  - ...but the trade off is a longer compile time
  - I did this mostly for local development purposes
    - overleaf takes care of a lot of details for us
    - we don't have to go in depth here
    - (`plug`) if you'd like to learn how to do everything on your 
      desktop, without overleaf, please check out my second session
      on Friday
- To reiterate: I'm showing you here what I got working. 
  - Don't be afraid to play around on your own and try other methods
  - User manual is here: https://mirror.aut.ac.nz/CTAN/macros/latex/contrib/glossaries/glossaries-user.html#tab:options

Some background / rationale

- most examples I've seen online dump glossary definitions into the
  main tex preamble
- if we want to keep our `document.tex` neat and tidy, it would be
  better to have a dedicated file (or files) with 
  our glossary definitions.
- I placed my definitions into a `glossary.sty` file because that
  tells me, the file _must_ be imported in the preamble
- since I went with `option 1`, there are some actions that _must_
  be done in the preamble.
  - I am not sure if there's a more conventional way to do `option 1`
    and import glossary definitions.


glossary set up

- `glossary.sty` is inside our `pages` directory
  - I know it's a style, but it made more sense to me, 
    cognitively, to put it in pages since it will 
    get print out later
  - recall: we put our other style inside template
- in `document.tex` make sure to do: 
```
\usepackage{pages/glossary}
```
- and also, at the end of the file, print the glossary by uncommenting:
```
\printnoidxglossary[nonumberlist, sort=word]
```

Next, open `glossary.sty`

```
\usepackage[toc,nopostdot,style=indexgroup]{glossaries}
% \glstoctrue adds glossaries to the table of contents
% use \glstocfalse otherwise
%
% nopostdot -- suppress the default post description dot
%
% style=indexgroup adds the letters above each section 

\glstoctrue
\makenoidxglossaries

\newglossaryentry{key}{
  name={The Name},
  description={
    The description of the entry
  }
}
```

- notice here we're using `\makenoidxglossaries`
- this is what we have to do for `option 1`

Notice I have a template entry

- I'm all about making templates so that I can copy/paste them later

```
\newglossaryentry{deme}{
  name={deme},
  description={
    a local group of individuals that interbreed with each other
  }
}
```

Now we can go back to our `01_literature_notes.tex` page and 
make our list of new vocab more interactive

```
\subsection{New Vocabulary and Concepts}
\begin{enumerate}
  \item{\gls{demes}}
  \item{allelic differentiation}
\end{enumerate}
```

`(should get an error)`

- ask participants what went wrong?
- some error about 'demes' has not been defined
- ... ?!?!
- change `demes` to `deme` and try again :) 

recompile

- now `deme` is clickable 
- (show off glossary page)
- (show off table of contents)
- may have to compile again for Glossary to show in ToC

table of contents

- notice that Glossary starts on page G1
- ...Bibliography starts on B1
- Let's take a peak at how we've done this -- it's not a default
  behaviour
- (`open document.tex`)
  - point out `\Renumber{G}`
- `\Renumber` isn't something that comes out-of-the-box with LaTeX
- I've defined it, it's in our `sty` file, so you can use it
  - let's take a peak
  - what I want to show you is, you can start making your own 
    macros
  - there's plenty of examples here, please have a play around
    and send me feedback after the session

How `\Renumber` works

- create a `\newcommand` taking `1` argument
- clear the page
- reset the page counter to 1
- make the new page start with whatever argument we've passed in
  - if we look again at `document.tex` we pass in letters
  - e.g. `\Renumber{G}`
  - look also at PDF preview ToC


Let's do one more glossary example

- I want to show off something I think is a common mistake
- (`open 01_literature_notes.tex`)

```
\subsection{New Vocabulary and Concepts}
\begin{enumerate}
  \item{\gls{demes}}
  \item{alldiff}
\end{enumerate}
```

- now reopen `glossary.sty` and add a definition

```
\newglossaryentry{alldiff}{
  name={allelic differentiation},
  description={
    The aspect of population structure relateing to Wright's 
    absolute differentiation.
  }
}
```

- (has everyone taken an intro to LaTeX?)
- (if not, I want to point out that if you add a linebreak 
  by pressing the enter key, it has no impact on the output.
  It just stops you from having one very very long line of text in 
  your editor. You need to add a blank line between lines of text
  for it to be meaningful to LaTeX, e.g. starting a new paragraph)

<!--
Let's see what happens if we use quotation marks, e.g.
```
    "absolute differentiation."
```
-->


---

# Questions?

---

# Example 2

In our first example, we created a template we could use for a research
notebook or a thesis. 

- I emphasized creating templates that I can quickly copy and 
  modify
- The entire set-up we've seen is a template
- ...and we can create other kinds of documents with it

## Scenario 2

- I am a first year PhD student
- I want to record minutes for my supervisor meetings
  so that we can track my progress and reflect upon
  discussions and agreements
- I don't want to write a whole book for this!
  - Chapters don't really make sense
  - I want to give a 1 or maybe 2-page summary

Goal

- create a minutes template
- start populating it
- use a "draft" watermark until my 
  supervisor has had a chance to review the minutes

First steps

- how to re-use our template?
- use an `article` document class
  - articles don't have chapters
  - modify `document.tex`:
```
\documentclass[openany,onecolumn,oneside]{article}
```

- modify `00_pagetemplate.tex` 
  - remove `chapter`
  - replace it with `section` 
- copy `00_pagetemplate.tex` to `02_minutes.tex`
- only include `02_minutes.tex` subfile from main document.tex
- compile from `document.tex`
  - look for the red `X` errors (yellow `!` are warnings)
  - we need to fix these (remove the code, along with the ToC)
  - this is one thing I don't like about overleaf
  - ...it generates a PDF even if you have errors
  - if you built a PDF locally, the entire compilation would fail
- if you plan to share your LaTeX project with others, you 
  need to correct any errors that pop up. Be on the look out.

Now we are ready to start making our minutes template

## Minutes template

```
\documentclass[document.tex]{subfiles}
\begin{document}

\section{Minutes Template}

\end{document}
```

(mention I would copy to YYYY-MM-DD.tex) and start modifying:

```
\documentclass[document.tex]{subfiles}
\begin{document}

\section{Progress}
My ResBaz progress so far: we have completed the first activity.
The second activity is still in progress.

\section{Discussion}
I might not remember every detail from this session, but
now I understand how to structure my project so that it's tidy,
and I will try my best to read any error messages Overleaf shows me.

\section{Agreements}
I will have a go modifying this template after the session is over

\end{document}
```

I could reformat this document a bit, so that I can see my 
progress at-a-glance with a TODO list

```
\section{Progress}
\begin{todolist}
  \item[\done]  first activity
  \item second activity (in progress)
\end{todolist}

```

Refer to notes below on how `todolist` works

---

## Creating a TODO list

Sometimes we'd like a feature that's not supported out of the box.
Let's suppose we want to create a TODO list, for setting goals and 
keeping focus.

- how can we create such a lsit?
- for me, a good first step is to google around and see if I can learn 
  what other people have done
- so, after some googling, I found this answer:
- https://tex.stackexchange.com/a/313337

Modifying our style file

- We could copy the code and paste it in our document.tex preamble
- if we want to keep document.tex neat and tidy, a better place to 
  put this code is inside our style
- (actually, I have already done this for you)
- go to line 150
- I won't overwhelm you with the implementation details here, the 
  main point is that we can add commands and keep them tidy
- another important point is to leave yourself minimum working 
  examples (MWEs) so that you know how to use these commands
- I have shown this in the comments

Let's expand out our page template

```
\section{Daily Goals}
\begin{todolist}
  \item[\done] frame the problem
  \item write solution 
  \item profit
\end{todolist}
```

Or maybe we decided not to profit

```
  \item[\wontdo] profit
```

---

So now we've finished up our meeting notes

- but we haven't got feedback yet from our advisor 
- let's send it out as a draft
- `modify sty file to add watermark`

That's our second demo done.

---

# Q&A session

I would like to open it up for Q&A

- otherwise, I have some other tips and 
- examples I have prepared

---

# Some other tips to prevent hair loss

- quotes -- ``quote'' versus "quote"
- no mathmode in references
  - (actually, this works in overleaf -- it shouldn't)
  - (will need to click into output log)
  - (always check for errors, they don't always pop up nicely for you)
  - .
  - try using \beta in a reference title
  - will get cryptic error message -- missing $ inserted
  - need \textbeta{} instead
- a tour of the `sty` file
  - main focus wasn't to go through every detail in here
    ...so I've mostly left it out of the tutorial
  - it's here for you to add on to
  - I try to keep it organized with little comment headers
  - you will thank yourself for leaving examples and comments 
    as you modify this file
- some cool stuff
  - the timeline template 
  - creating reference links
  - (be sure to add label)
  - combine these in an example...

```
\timeline{ResBaz}        {\nameref{chap:rezbas}}
```

- can go through template examples
  - listings
  - minted
  - table
  - subcaption




