# ZX-calculus Anki deck

An Anki deck for studying the ZX-calculus.

Download it [from Ankiweb](https://ankiweb.net/shared/info/132121405).

## Setup

To (re)create the deck using the desktop Anki app,
first download the [Edit LaTeX build process add-on](https://ankiweb.net/shared/info/937148547).
Then configure the add-on to use [`convert` from ImageMagick](https://imagemagick.org/script/convert.php) as follows on Linux and Windows:

```
{
    "pngCommands": [
        [
            "pdflatex",
            "-interaction=nonstopmode",
            "--shell-escape",
            "tmp.tex"
        ],
        [
            "convert",
            "-density",
            "200",
            "-trim",
            "tmp.pdf",
            "tmp.png"
        ]
    ],
    [ ... other stuff... ]
}

```

On MacOS, use `sips` instead:

```
{
    "pngCommands": [
        [
            "pdflatex",
            "-interaction=nonstopmode",
            "--shell-escape",
            "tmp.tex"
        ],
        [
            "sips",
            "-s",
            "format",
            "png",
            "tmp.pdf",
            "--out",
            "tmp.png"
        ]
    ],
    [ ... other stuff... ]
}

```

In Anki, under "Tools|Manage Note Types", for the `ZX-Calculus` note type, enter the following for the header:


```
\providecommand{\pgfsyspdfmark}[3]{}
\documentclass[convert={convertexe={convert}},border=2]{standalone}
\usepackage{amsmath}
\usepackage{tikz}
\usetikzlibrary{quantikz}
\usetikzlibrary{zx-calculus}
\pagestyle{empty}
\setlength{\parindent}{0in}

\newcommand{\ketbra}[2]{\ensuremath{\ket{#1}\!\bra{#2}}}

\begin{document}
```

And then this for the footer:

```
\end{document}
```

The notes should be processed by LaTeX automatically to produce the cards.
