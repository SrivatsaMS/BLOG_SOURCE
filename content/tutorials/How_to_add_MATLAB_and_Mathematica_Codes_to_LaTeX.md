+++
title = "How to add MATLAB and Mathematica Codes to LaTeX"
date = 2019-12-06T20:14:03-07:00
description = "This is a post about Vatsa"
draft = false

type = ["posts","post"]
tags = [
    "HOW-TO",
    "latex",
    "MATLAB",
    "Mathematica",
]

categories = [
    "",
    "",
]
[author] 
 name = "Srivatsa" 
+++

It can be done by two ways. One by using ‘Listings’ package and other is by using ‘Listing with matlab-prettifier’. I prefer first method.

Place your .m (Matlab script) files in the same directory as .tex file.
> ## For MATLAB
>  
### 1. First method
```LaTex
\documentclass{article}
\usepackage[T1]{fontenc}
\usepackage{bigfoot} % to allow verbatim in footnote
\usepackage[numbered,framed]{matlab-prettifier}
\usepackage{filecontents}

\let\ph\mlplaceholder % shorter macro
\lstMakeShortInline"

\lstset{
  style              = Matlab-editor,
  basicstyle         = \mlttfamily,
  escapechar         = ",
  mlshowsectionrules = true,
}

\begin{document}

\lstlistoflistings  %Creates the table of content for your codes.
\lstinputlisting[caption = {Sample code from Matlab}]{sample.m}  %calling lstinputlisting

\end{document}
```
> ![Matlab in LaTeX file](https://i.imgur.com/RctZNJZ.png)
> 
> `Matlab Code in LaTeX file`

### 2. Second Method
```LaTex
\begin{lstlisting}[caption = {sample.m script calculates so and so (TITLE)}]
You paste your code here
\end{lstlisting}
```
------
---

> ## For Mathematica

Copy the following code to your LaTeX file. 

```LaTeX
\documentclass[11pt,english]{scrartcl}
\usepackage{babel}
\usepackage{beramono}
\usepackage[T1]{fontenc}
\usepackage[latin9]{inputenc}
\usepackage{color}
\usepackage{rotating, graphicx}

\definecolor{identifiercolor}{rgb}{.4,.6,.56}
\definecolor{stringcolor}{gray}{0.5}
\definecolor{inactivecolor}{rgb}{0.15,0.15,0.5}

\usepackage{listings}
\lstset{basicstyle={\footnotesize\def\fvm@Scale{.85}\fontfamily{fvm}\selectfont},
  breaklines=true,
  escapeinside={\%*}{*)},
  keywordstyle={\bfseries\color{inactivecolor}},
  stringstyle={\bfseries\color{stringcolor}},
  identifierstyle={\bfseries\color{identifiercolor}},
  language=Mathematica,
  otherkeywords={DiscretizeRegion},
  showstringspaces=false}
\renewcommand{\lstlistingname}{Listing}

\begin{document}

Here I tell Mathematica to make a wave function plot:
\begin{lstlisting}[extendedchars=true,language=Mathematica]
Block[
    Show[StreamPlot[{-3 x + -2 y, 5 x + 2 y}, {x, -3, 3}, {y, -3, 3}, 
PlotTheme -> Automatic, StreamColorFunction -> "BlueGreenYellow"], 
FrameLabel -> {{None, None}, {HoldForm[Option 5], None}}, 
PlotLabel -> HoldForm[Stream Plot for b], 
LabelStyle -> {FontFamily -> "CMU Serif", GrayLevel[0]}]
]
\end{lstlisting}
\begin{figure}[hbt!]
    \centering
    \includegraphics[width=0.75\columnwidth]{streamplots_gr4.eps}
    \caption{StreamPlot}
  \end{figure}

\end{document}
```
> ![Looks neat but not pretty enough](https://i.imgur.com/LzQXdCT.jpg)
> 
> `Mathematica looks neat but not pretty enough.`

You can always play around with the options to get the desired results.

Thanks for reading.
