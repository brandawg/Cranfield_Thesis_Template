# Cranfield Thesis Template

The purpose of this repository is to host the LaTeX style file required for writing documents in the Cranfield Thesis template style and all the documentation required on how to use it.

The LaTeX style file is an update of Daniel Auger's unofficial Cranfield thesis .sty file (2014/08/05). Hence this is why the file is called cranfieldthesis2.sty, and still it remains unoffical.

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

# Bibliography

# Other Useful Packages

