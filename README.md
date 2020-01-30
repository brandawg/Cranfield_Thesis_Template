# Cranfield (Unofficial) LaTeX Thesis Template
The purpose of this repository is to host the style files required for writing documents in LaTeX in accordance with Cranfield thesis template guidlines, along with all the documentation required on how to use it.

The motivation for updating the original sty file was to create a LaTeX style file that recreated (as best possible) the look, feel and structure of Cranfield's official Word thesis template, but still allowed for the flexibility, control and performance that LaTeX offers.

- Latest update to style file: **30/01/2020**.
- Latest update to example file: **30/01/2020**.
- Latest update to documentation: **30/01/2020**.


# Installation
Installation of the style could not be easier:

1. [Download the cranfieldthesis.sty file from this repo.](https://github.com/brandawg/Cranfield_Thesis_Template/blob/master/cranfieldthesis.sty)
2. Place the file within your local working folder for your LaTeX document.
3. In the preamble add:  
```
\usepackage{cranfieldthesis}
```

And you're done.

# Preamble Setup [Basic]
In its most basic form the preamble can be set up as follows:

```
\documentclass[12pt]{book}

\usepackage{cranfieldthesis}

\begin{document}

\end{document}
```

The documentclass used as a base style is the standard LaTeX book class. In its current form, the document produced will default to  double sided printing, hence blank pages which may appear at the end of some sections to guarantee that the Chapter headings appear always appear on a left hand page. To switch to a single sided document see below,

```
% Double Sided Printing
\documentclass[12pt]{book}

% Single Sided Printing
\documentclass[12pt, oneside]{book}
```

# Compiling the Document
As with most latex documents, `pdflatex` is the recommended compiler to producing a pdf from your .tex script.

## Recommended Build Orders:
1. Basic Preamble Set Up: `pdflatex`.
2. Basic Preamble + TOC: `pdflatex` -> `pdflatex`.
3. Basic Preamble + TOC + Bibliography (Bibtex Backend): `pdflatex` -> `bibtex` -> `pdflatex` -> `pdflatex`.
4. Basic Preamble + TOC + Bibliography (Biber Backend): `pdflatex` -> `biber` -> `pdflatex` -> `pdflatex`.

# Title Page Set Up
Title page information required by the sty to generate the title pages is also added to the preamble.

This information is then run by the command `\maketitlepages` which is placed in the main document. See below for the complete setup.
```
\documentclass[12pt]{book}

\usepackage{cranfieldthesis2}

\title{Thesis Title}
\author{First Name \ Surname}
\date{January 2020}
\school{Defence and Security}
\centre{Centre for Electronic Warfare, Information and Cyber}
\qualification{Doctor of Philosophy}
\academicyear{2020}
\supervisor{Supervisor}
\copyrightyear{2020}
\fulfilment{}

\begin{document}

\maketitlepages

\end{document}
```

# Abstract
The next section of text required in the document is an abstract. Add the following after `\maketitlepages`.
```
\begin{abstract}

\end{abstract}
```
Your abstract can then be typed between the `\begin` and `\end` commands.

# Contents Pages
## Automatically Generated Lists
Pregenerated contents page lists can easily be added and removed depending on your needs. The `.sty` contains 5 automatic lists:
1. Contents - Lists section headings etc.
2. Figures - Lists of Figures, including page numbers and captions.
3. Table - List of Tables, including page numbers and captions.
4. Algorithms - List of Algorithms, including page numbers and captions.
5. Code - List of code snippets, including page numbers and captions.

Each is controlled through a seperate command and is placed after the abstract.
```
% Table of Contents
\sstableofcontents

% List of Figures
\sslistoffigures

% List of Tables
\sslistoftables

% List of Algorithms
\sslistofalgorithms

% List of Code
\sslistofcode
```

## Manually Generated Lists
User manually created lists are used for symbols and abbreviations.

### List of Abbreviations
Abbreviations are added line by line.
```
\begin{listofabbreviations}
    \abbrev{EWIC}{Centre for Electronic Warfare, Information and Cyber}
\end{listofabbreviations}
```
The command `\abbrev` has the following inputs:
```
\symb{Abbreviation}{Description}
```

### List of Symbols
Symbols are added line by line.
```
\begin{listofsymbols}
	\symb{$A$}{$m$}{Cartesian coordinate position.}
\end{listofsymbols}
```
The command `\symb` has the following inputs:
```
\symb{Symbol}{Unit}{Name}
```

### List of Publications
Publications are added line by line.
```
\begin{listofpublications}
  \pubhead{Use \pubhead to group publictions, e.g: Journals, Conferences etc.}
  \pub{My publication citation}
\end{listofpublications}
```

Example usage:
```
\begin{listofpublications}
  \pubhead{Journals}
   \pub{B. Corbett, D. Andre and M. Finnis, \textit{Through-wall detection and imaging of a vibrating target using synthetic aperture radar}, in Electronics Letters, vol. 53, no. 15, pp. 991-995, 2017.}
\end{listofpublications}
```


# Line Spaceing
Cranfield does not set a mandatory line spacing size. They recommend that 1.5 is sometimes easier for reviewers, however we all know 1.25 looks much nicer.

Line spacing height needs to be set by the user in this template. This is done through the `\setstretch{}` function. Add the following line of code after you have added all you introductory pages (TOC, lists etc.) and therefore before the main content of the thesis starts.
```
\end{listofpublications}

\setstretch{1.25}

\chapter{First Chapter}\label{chap:one}
```

# Referencing
For in-document referencing of figures, sections, equations etc. The [cleveref](https://ctan.org/pkg/cleveref?lang=de) package has been loaded with all common names predefined in the sty file. 

The cleveref package is used as it allows for automatically producing a label name and number. Unlike the standard `\ref` package which only produces the number. The package automatically identifies what object one is referencing and chooses the label accordingly. It is used in the sty file as follows,
```
\usepackage{cleveref}
%\crefname{object}{singular}{plural}
\crefname{table}{table}{tables}
\Crefname{table}{Table}{Tables}
\crefname{figure}{figure}{figures}
\Crefname{figure}{Figure}{Figures}
\crefname{equation}{equation}{equations}
\Crefname{equation}{Equation}{Equations}
\Crefname{chapter}{Chapter}{Chapters}
\crefname{chapter}{Chapter}{Chapters}
\Crefname{section}{Section}{Sections}
\crefname{section}{Section}{Sections} 
```
cleveref is used though the `\cref` or `\Cref` command. Lower case `\cref` will generate a lower case label and an upper case `\Cref` will generate a capitalised label.

## Examples of cleveref
Figure referencing:
```
\begin{figure}[h!]
  \centering
  \rule{20pt}{20pt}
  \caption{My figure}
  \label{fig:myfig1}
\end{figure}

Reference lowercase figure: \cref{fig:myfig1}\\
Reference uppercase figure: \Cref{fig:myfig1}
```
Produces the output: _Reference lowercase figure: figure 1.1. Reference uppercase figure: Figure 1.1_

Reference Range of items:
```
\begin{align}
  y&=a_1x+b_1\label{eq:1}\\
  y&=a_2x+b_2\label{eq:2}\\
  y&=a_3x+b_3\label{eq:3}\\
  y&=a_4x+b_4\label{eq:4}
\end{align}

Range example: \crefrange{eq:1}{eq:4}
```
Produces the output: _Range example: equations (1.1) to (1.4)_

Mixed References:
```
\begin{align}
  y&=a_1x+b_1\label{eq:1}\\
  y&=a_2x+b_2\label{eq:2}\\
  y&=a_3x+b_3\label{eq:3}\\
  y&=a_4x+b_4\label{eq:4}
\end{align}

\begin{figure}[ht]
  \centering
  \rule{0.5\linewidth}{0.1\linewidth}
  \caption{My figure}
  \label{fig:myfig1}
\end{figure}

Mixed references example: \cref{eq:1,eq:3,eq:4,fig:myfig1}.
```
Produces the output: _Mixed references example:equations (1.1), (1.3) and (1.4) and figure 1.1._

# Bibliography
The Cranfield thesis template recommends either *author-year* style, with citations placed in (parentheses) or *numeric* references with citations placed in [parentheses].

In your preamble add the following, 
```
\usepackage[backend=bibtex, sorting=none, style=numeric, citestyle=numeric]{biblatex}
\usepackage[backend=bibtex, sorting=none, style=authoryear-ibid, citestyle=authoryear]{biblatex}
\addbibresource{BibTexCollection.bib}
```
Where `style=` refers to the in-text appearance of the citation and `citestyle=` is the bibligraphy citation. 

Here, BibTexCollection.bib is your BibTeX collection of references. Mendeley exports this directly.  

In your main text add the following where you would like your bibliography:
```
\printbibliography[title=BIBLIOGRAPHY]
```
If you wish for your bibliography heading to be visible in the Table of Contents add the following to the `printbibliography` line:
```
\printbibliography[heading=bibintoc,title=BIBLIOGRAPHY]
```
For users who wish to organise the output files produced from running `pdflatex`, the `bibtex` backend used when setting up `biblatex` will no longer work. Instead we can user `biber` for the backend, Simply amend the `\usepackage{}` function for `biblatex`. All useage of `biblatex` remains the same:
```
\usepackage[backend=biber, sorting=none, style=numeric, citestyle=numeric]{biblatex}
```

If you wish to remove URL, doi and ISBN components from your citation apperance within the typset bibliography, use the following respectively within the `\usepackage[...]{biblatex}` command:
```
\usepackage[backend=biber, sorting=none, style=numeric, citestyle=numeri, doi=false, isbn=false, url=false]{biblatex}
```
This technique can be expanded for all standard `.bib` database files that `biblatex` uses.

## Citation Command Examples 
Cheat sheet of _cite_ commands for biblatex is avaliable [here](https://github.com/brandawg/Cranfield_Thesis_Template/blob/master/biblatex-cheatsheet.pdf). _([Link to Source](http://tug.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf))_

If numeric style is desired, change `\parencite` to `\cite`.

Single citation in parantheses: 
```
\parencite[p.~102-104]{_bibtex key_}.
```

Multiple citations: 
```
\parencites[p.~102-104]{_bibtex key 1_}[p.~77-98]{_bibtex key 2_}. 
```

Simple combined citations:
```
\parencite{_bibtex key 1_, _bibtex key 2_}.
```

No authors displayed, just year citation:
```
\parencite*{_bibtex key 1_}.
```

Footnote citation:
```
\footcite{_bibtex key 1_, _bibtex key 2_}.
```

Further exmaples can be found using in the [biblatex documentation](_http://mirror.ox.ac.uk/sites/ctan.org/macros/latex/contrib/biblatex/doc/biblatex.pdf_)

# Appendix
Appendicies traditionally change the numeration of the chapter headings contained within the appenix to be latin characters (A,B,C,...) instead of numbers (1,2,3,...).

This can be done with the command `\appendix`. Place the command before you want to start your first Appendix chapter. In the case of Cranfield thesis guidlines, this usually this comes after you have printed your bibliography.
```
\printbibliography[title=BIBLIOGRAPHY]

\appendix

\chapter{First Appendix Chapter}
```

# Font Selection
- Three font families can be used within the template: Roman, Sans Serif and Mono.
- Cranfield's offical template supports the use of Sans Serif (Arial style fonts).
- Use *one* of the following commands in your preamble to select your font:
```
\romanFont
\arialFont
\monoFont
```

# Page Numbering
This is undefined in the Cranfield thesis template, but a nice addition which can be enabled in the LaTeX template is the usage of Roman numerals for page numbering of all pages before the main body of text. Therefore, the main body of text starts count from _1_.

To enable Roman numeral page numbering simply use the following line of code after the `\maketitlepages` command.
```
% Form Title Pages
\maketitlepages

% Sets page numbering to roman for all pages before main body.
\pagenumbering{Roman}
```

To switch back to Arabic numbering, use following after your first chapter has been defined. 
```
\chapter{First Chapter}\label{chap:one}

% Sets page numbering to standard arabic for all pages in main body.
\pagenumbering{arabic}
```
This code was taken from the `example.tex` file within this repo.

# Notes
- Quotation marks can be defined in two ways. The latex default: ` ``hello'' `, and ` "hello" ` from csquotes.

# Contact
Users are welcome to post issues/suggestions/comments on this repoistories _Issues_ page. Pull requests are also welcome.

# Thanks
Thanks to all who have been involved in putting this template together, especially Akhil who has helped substantially in testing and organising the features this template required.
