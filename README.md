# R Markdown paper template using `bookdown`

## Setup

- Install the `rmarkdown` and `bookdown` R packages
- Make sure to have a working TeX distribution installed locally (or install the `tinytex` R package)
- Fork this repository to start your paper repository

## Usage recommendation

### Overview

This repository contains an R Project. The `text` subfolder contains `Rmd` containing RMarkdown text. Markdown can be compiled to a variety of formats using `pandoc` via the `rmarkdown` package. The main difference between regular Markdown and RMarkdown is that RMarkdown is able to parse (amongst others) `R` code (inline and in code chunks) and display it's results directly in the output format. In this particular project `bookdown` is used on top of `rmarkdown`. `bookdown` extends the Rmarkdown syntax and e.g. allows the RMarkdown input to be spread out across multiple files.

For further information, see the following resources:

- Markdown: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
- Pandoc: https://pandoc.org/MANUAL.html
- RMarkown: https://bookdown.org/yihui/rmarkdown/
- Bookdown: https://bookdown.org/yihui/bookdown/


### General pandoc/knitr workflow

A regular Markdown file that is to be converted using `pandoc` consists of a YAML header that is separated from the main text by `---`. The YAML header can be used to set meta variables, that are then passed on by `pandoc` to a template, this may be a HTML, .docx, LaTex (or a variety of other formats) file. Usually, the title and authors can be set in the YAML header. The available variables vary by template (see https://pandoc.org/MANUAL.html#templates, https://pandoc.org/MANUAL.html#default-files for the default values). When compiling a Markdown template using markdown, the YAML header variables are filled in their respective places in the template and the text is used as the main text body (e.g. `document` environment in LaTeX). To produce a PDF file, simply click the 'knit' button the top menu bar in RStudio or simply run `bookdown::render_book('index.Rmd')` in the console with the working directory set to the main project directory.

For Rmarkdown, `pandoc` compilation is invoked using `knitr`. It combines the R code present in the RMarkdown and `pandoc` compilation. R code can be used in a variety of ways in a RMarkdown file (see https://bookdown.org/yihui/rmarkdown-cookbook/r-code.html).


### Project text setup and recommended workflow

The main project folder contains the following file and folders:

- `index.Rmd`: main Rmarkdown file contains the YAML header and the setup code chunk that sets options for all code chunks of the document. For general text editing, you will not need to change anything here.
- `_bookdown.yml`: contains additional options for the `bookdown` package
- `_book`: output folder that is created when knitting the Rmarkdown files (do not commit these files to the repository)

The `text` folder contains the follwing files:

- `preamble.tex`: contains LaTeX code that is inserted in the preamble of the LaTeX file when compiling to/via LaTeX
- `...`: individual text files/section that are read according to their file name in ascending order when compiling the RMarkdown source. It is recommended to start filenames with a number (e.g. `01_`) to allow for easy handling of the order of text files.

The setup code chunk in `index.Rmd` contains a setup code chunk. It is generally advisable to create all variables, objects etc outside the RMarkdown code chunks to keep things tidy and use the code chunks mainly for displaying the created results etc. I.e., the setup code should source, load or create all data used in the RMarkdown files.

### Advanced

To customize the behavior of the 'knit' button, see https://bookdown.org/yihui/rmarkdown-cookbook/custom-knit.html.
