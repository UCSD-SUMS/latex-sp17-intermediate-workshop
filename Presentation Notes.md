# Latex Workshop Notes

These notes detail the process we will be going through in order to write and compile incrementally more complex LaTeX documents during the workshop.

Pause between each numbered section to ensure that everyone is caught up. Try to take a break at the 1 hour mark.

## Useful Links

* General Purpose
    * [TexZilla](https://fred-wang.github.io/TeXZilla/): A REPL for Math expressions
    * [Detexify](http://detexify.kirelabs.org/classify.html): Find commands for unknown symbols.
    * [Equation Editor](https://www.codecogs.com/latex/eqneditor.php) GUI for generating code for more complicated expressions
    * [Table Generator](http://www.tablesgenerator.com/): GUI for designing tables that generates copy-pastable source code
    * [CTAN](https://www.ctan.org/pkg): Hosts Latex packages, descriptions, and downloads.
* For installing/using Latex on your local machine:
    * [MikTeX](https://miktex.org/): A Latex "distribution", includes compiler and some packages
    * [Texmaker](http://www.xm1math.net/texmaker/): A Latex IDE
* [Online Markdown Editor](https://jbt.github.io/markdown-editor): The markdown editor used for this document

## Preliminaries
- Create an account on [Sharelatex.com](https://www.sharelatex.com/) and log in to Projects page
- Navigate to the Github Repository: [Repository Link](https://github.com/UCSD-SUMS/latex-w17-workshop)

------
# Graphics: 
Do this in a new project! Copy-paste most things to emphasize that some of these are worth saving as snippets, instead of remembering every detail.

## Overview

**main.tex**
```latex
\usepackage{graphicx}
...

\section{Introduction}
\begin{figure}[]
    \centering
    \includegraphics[width=4cm]{image1}
    \label{fig:img1}
    \caption{Homotopy groups of spheres}
\end{figure}

\begin{align}
  f(x) &= (x+a)(x+b) \\
  &= x^2 + (a+b)x + ab
\end{align}
```

## Talking Points

- We've built a pretty fully-featured document so far. But since these last few bits are slightly more complex, we'll do it in a new project.
- Setting up the new project:
  - **Start a new blank project**
  - Search Google for an image (png or jpg preferably), download it, then upload it into your project
  	- I chose the term "homotopy" and got 
![Image of Yaktocat](https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/Homotopy_of_pointed_circle_maps.png/220px-Homotopy_of_pointed_circle_maps.png)
  - Rename the image **"image1.png", "image1.jpg"**, or whatever file type you found.


- The Figure environment
  - *The* way to include images in your documents, but this process can be very fiddly!
  - Most of what we type into Latex is a *suggestion* to the Latex compiler of where things go and how they should be placed.
  - Images can be very complex - differing sizes/shapes, aspect ratios, alignment, how they flow with text...there are many variables to consider
  - So by default, your images *may* not show up exactly where you put them in the text!
  - **Insert figure code, note bad image placement**
  - **Add `h` option to figure to force better placement**
  
- The align and align\* environments
	- **Provided by amsmath**
	- Useful for for showing a series of calculations
	- Also good for making multiline math line up
	- Many other "aligned" environments behave like this one (tables, arrays/matrices, etc)
	- User ampersands to denote 'anchors' where columns should line up\
		- Must have the same number in each row!
	- **Insert align code**
	- **Demonstrate align\***

- The Tikz package
  - A *very* brief overview, so people know it exists
  - Useful CS (graphs, trees), EE (circuits, control systems), Math (commutative diagrams). 
  - Relatively simple, but also very powerful/extensive. Has a learning curve though.
  - **Do not live code, just show diagram.tex after it's compiled**
