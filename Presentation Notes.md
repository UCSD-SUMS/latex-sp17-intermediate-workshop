

# Introduction

## Preliminaries

- Create an account on [Sharelatex.com](https://www.sharelatex.com/) and log in to Projects page
- Navigate to the Github Repository: [Repository Link](https://github.com/UCSD-SUMS/latex-w17-intermediate-workshop)
- Grab a copy of the example document handouts, start looking through and thinking about what you'd like to cover
- Sit close to the front!

## Getting Started

- Introduce selves
- Mention that this is the first "intermediate" workshop and that feedback is appreciated

# Live Coding

- Start with blank document

- Add some packages - stuff you'll almost always want/need

  - `mathtools`: Combines many `amsmath` packages
  - `amssymb`: You'll inevitably need a weird symbol
  - `amsthm`: Nice math environments
  - `hyperref`: Hyperlink all the things
  - `float`: Mitigates the living hell of image placement

- We'll pull in more specific stuff as needed

- Let's write a theorem: the quadratic equation

  - Use `\textbf` for bold, manually number it
  - Do the same for 'proof'
  - Math mode review: `$$` `\[ \]`
    - Cue holy war!
    - `$$` common in many tex environments (e.g. Mathjax, used on Math SE/WO), good for quick hacks but can introduce subtle bugs/spacing issues
    - `\[ \]` Does some extra syntax checking, ams package just redefines this to be its own (super nice) `equation` environment
  - Write combined roots with `\pm`
  - Then use comma to separate the two roots
  - Replace comma with `\text{and}`
  - Show spacing using `\:`
    - Cover other types of spacing:
      - `\!` a little less
      - `\,` a little more
      - `\:` medium
      - `\;` a lot
        - Just `\ ` also
      - `\quad` so much space
      - `\qquad` wide open ranges
    - If you like operator spacing, define your own!
      - Binary (like $+$) or relational (like $<$)
      - `\mathbin` or `\mathrel`
      - ​

- Improving the theorem

  - Define `theorem` and `proof` environments: 
    `\newtheorem{theorem}{Theorem}`
  - First parameter: custom name you give this environment
  - Second parameter: What text is displayed (in bold by default)
  - Optional parameters: When to break the numbering
    - `section`: By default, theorems are ordered 1,2,3... across all sections. This restarts numbering at every section break
    - `theorem`: Attaches the counter to theorem environments instead, restarts every time there's a new theorem
  - Call like a normal environment with begin/end
  - Supply optional parameters for Important Theorems (tm)
    - `\begin{theorem}[Brouwer's Fixed Point Theorem]`
  - Can also use theorem* to turn off numbering
  - Note: Proof is built-in! Gives us the QED box too!
    - Change the QED symbol:
      `\renewcommand\qedsymbol{$\blacksquare$}`

- Show sgn function theorem

- Show colspan theorem

  - Use theorem and proof environments this time
  - Show `\operatorname{span}` , then `DeclareMathOperator`
  - Use pmatrix
  - Show cdots, vdots, ddots
  - Show left/right modifiers

- Fancy letters!
  `mathbb, mathcal, mathfrak, mathscr`

- Over-stuff
  `overline, overbrace, overset`

- Colors:
  `\usepackage[dvipsnames]{xcolor}`
  `{\color{MidnightBlue}2x}, {\color{BrickRed}2x}`

- Tabular Environments

  - Alignment options:`c, l, r`

- Beamer

  - Frames
  - Itemize within frames and number to generate "transitions"
  - pause command if you just want to write text
  - Blocks:
    - block, alertblock, examples

- Tikz

  - Start with `\draw` or `\fill` , end with `;`
    - These take params like color, thickness, etc
  - Lines: $(x_0, y_0) -- (x_1, y_1);$
  - Circles: $(x_0, y_0)$ circle (size pt);
  - Bezier: `\draw (-2,2) .. controls (-1,0) and (1,0) .. (2,2);`
    - Endpoints and control points
  - Ellipse: `\fill[blue!50] (2.5,0) ellipse (1.5 and 0.5);`
    - 2nd params are foci

- Macros
  `\newcommand{\ff}[2]{\mathbb{F}_{#1^{#2}}}`

  ​

# Code References

## Math Hackery

Column Space Theorem:

```latex
\DeclareMathOperator{\col}{col}
\DeclareMathOperator{\spn}{span}

...

\[
\operatorname{col}(A)=
\operatorname{col}\begin{pmatrix}
a_{11} & \cdots & a_{12}\\
\vdots & \ddots & \vdots\\
a_{m1} & \cdots & a_{mn}
\end{pmatrix}
=
\operatorname{span}\left\{
    \begin{pmatrix}
        a_{11}\\\vdots\\a_{m1}
    \end{pmatrix}
    , \, \ldots \, ,
    \begin{pmatrix}
        a_{1n}\\\vdots\\a_{mn}
    \end{pmatrix} 
\right\}\,.
\]
```

Align Environment:

```latex
\begin{align*}
(x+y)^3 &=(x+y)(x+y)^2\\
        &=(x+y)(x^2+2xy+y^2)\\
        &=x^3+2x^2y+xy^2+xy^2+2xy^2+y^3\\
        &=x^3+3x^2y+3xy^2+y^3\,.\tag*{\qedhere}
\end{align*}
```

Cases Environment

```latex
\[
\operatorname{sgn}(x):=
\begin{cases}
1   &\text{if $x>0$}\\
0   &\text{if $x=0$}\\
-1  &\text{if $x<0$\,.}
\end{cases}
\]
```

Overstuff

```latex
\[
a^m\cdot a^n
=
(\overbrace{a\cdots a}^{\text{$m$ factors}})\cdot (\overbrace{a\cdots a}^{\text{$n$ factors}})
\overset{(*)}{=}
\overbrace{a\cdots a\cdot a\cdots a}^{\text{$m+n$ factors}}
=
a^{m+n}
\,,
\]
```

Tabular Environments

```latex
\begin{center}
\begin{tabular}{ c | c | c }
 cell1 & cell2 & cell3 \\
 \hline
 cell4 & cell5 & cell6 \\  
 \hline
 cell7 & cell8 & cell9    
\end{tabular}
\end{center}
```

Tikz

```latex
\begin{tikzpicture}

% Lines
\draw[gray, thick] (-1,2) -- (2,-4);
\draw[gray, thick] (-1,-1) -- (2,2);

% Point
\filldraw[black] (0,0) circle (2pt) node[anchor=west] {Intersection point};
 
 % Bezier
 \draw (-2,2) .. controls (-1,0) and (1,0) .. (2,2);
 
 % Ellipse
 \fill[blue!50] (2.5,0) ellipse (1.5 and 0.5);
 
\end{tikzpicture}
```



## Tables

## Labels and Cross-Referencing

## Source Code

## Diagrams Using TikZ

## Customization

## Alternate Document Classes