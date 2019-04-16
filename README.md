# Cranfield Thesis Template

The purpose of this repository is to host the LaTeX style file required for writing documents in accordance with Cranfield thesis template guidlines, along with all the documentation required on how to use it.

The LaTeX style file is an update of Daniel Auger's unofficial Cranfield thesis .sty file (2014/08/05). Hence this is why the file is called cranfieldthesis2.sty, and still remains _unoffical_.

The motivation for updating the original sty file was to create a LaTeX style file that recreated (as best possible) the look, feel and structure of Cranfield's official Word thesis template.

# Installation

Installation of the style could not be easier:

1. [Download the cranfieldthesis2.sty file from this repo.](https://github.com/brandawg/Cranfield_Thesis_Template/blob/master/cranfieldthesis2.sty)
2. Place the file within your local working folder for your LaTeX document.
3. In the preamble add:  `\usepackage{cranfieldthesis2}`

And you're done.

# Preamble Setup [Basic]

In its most basic form the preamble can be set up as follows:

```
\documentclass[12pt]{book}

\usepackage{cranfieldthesis2}

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

# Title Page Set Up

Title page information required by the sty to generate the title pages is also added to the preamble.

This information is then run by the command `\maketitlepages` which is placed in the main document. See below for the complete setup.

```
\documentclass[12pt]{book}

\usepackage{cranfieldthesis2}

\title{Thesis Title}
\author{Christian Name \ Surname}
\date{April 2019}
\school{Defence and Security}
\centre{Centre for Electronic Warfare, Information and Cyber}
\degree{Ph.D}
\academicyear{2019}
\supervisor{Supervisor}
\copyrightyear{2019}
\fulfilment{}

\begin{document}

\maketitlepages

\end{document}
```

# Abstract
The next section of text required in the document is an abstract. Add the following after `\maketitlepages`.

```
\begin{abstract}
    \blindtext
    \section*{Keywords}
    Keyword 1; keyword 2; keyword 3.
\end{abstract}
```

# Contents Pages

## Automatically Generated Lists
Pregenerated contents pages can easily be added and removed depending on your needs. The sty contains 4 automatic lists:
1. Contents - Lists section headings etc.
2. Figures - Lists of Figures, including page numbers and captions.
3. Table - List of Tables, including page numbers and captions.
4. Code - List of codes/algorithms, including page numbers and captions.

Each is controlled through a seperate command and is placed after the abstract.

```
% Table of Contents
\sstableofcontents

% List of Figures
\sslistoffigures

% List of Tables
\sslistoftables

% List of Code/Algorithms
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

### List of Symbols
Symbols are added line by line.
```
\begin{listofsymbols}
	\symb{$\mathbf{A}$}{$m$}{Cartesian coordinate position.}
\end{listofsymbols}
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
The Cranfield thesis template recommends authoryear style, with citations placed in (parentheses). Or numeric references with citations placed in [parentheses].

In your preamble add the following, 
```
\usepackage[backend=bibtex, sorting=none, style=numeric, citestyle=ieee]{biblatex}
\usepackage[backend=bibtex, sorting=none, style=authoryear-ibid, citestyle=authoryear]{biblatex}
\addbibresource{BibTexCollection.bib}
```
Where BibTexCollection.bib is your BibTeX collection of references. Mendeley exports this directly.  

In your main text add the following where you would like your bibliography:

```
\printbibliography[title=\uppercase{bibliography}]
```

## Citation Command Examples 
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
\printbibliography[title=\uppercase{bibliography}]

\appendix

\chapter{First Appendix Chapter}
```

# Notes
- Arial font can be activated by using the command `\arialFont` in your preamble. 
