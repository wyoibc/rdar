---
title: Reproducible Methods in Research and Teaching
date: September 16, 2019
---

### A Workshop by Vikram E. Chhatre & Nicolas A. Blouin

Test for contributing changes to your repository

<br><br>

## How to Prepare for this Workshop


We highly recommend following this tutorial to adequately prepare for the workshop.  Before or during the workshop, it will **not** be possible to provide any assistance in installing either base software or needed packages.  If you do not have necessary software or lack basic skills in using it (*See the section on Required Basic Proficiency below*), you will not be able to work through this workshop.  We apologize in advance for being blunt on this matter and hope to provide an optimal learning experience.


Every operating system is different and so is the environment it provides in order for software to run without issue.  For this reason, it is important that you have full privileges for running and modifying the software on your computer.  **Please ensure that you have administrative privileges**.  If you are using an institution owned laptop and your IT is reluctant to give you admin control, then please seriously consider bringing a laptop that you own.


The entire workshop and its documentation will be posted at [github.com/wyoibc/rdar](https://github.com/wyoibc/rdar).  To avoid paper waste, we will not be printing copies and we urge you to not do so as well.



## 1. Software to be Installed

### (a) R - The Statistical Data Analysis and Programming Language

- Follow the link to your operating system and install the latest version [CRAN Mirror at UC Berkeley](https://cran.cnr.berkeley.edu/) unless you already have it.  As of this writing, the latest version was ``3.6.1`` nicknamed ``Action of the Toes``.


### (b) R-Studio

Is graphical front-end for the R programming language - one that we will use during the workshop.  Download the [Desktop version here](https://www.rstudio.com/products/rstudio/download/#download).


### (c) A Text Editor

If you have a favorite text editor (Notepad doesn't count, though Notepad++ does), then you are all set.  Otherwise, we highly recommend ``Vim``.

- On Mac OSX, the best way to install Vim is through the [Homebrew Package Manager](https://brew.sh).  Install both commandline ``vim`` and GUI ``macvim``.  

- For Windows, access download link [on this page](https://www.vim.org/download.php).

- Alternatively, on Windows you may also use Notepad++


### (d) Git, the Version Control System

- On Mac OSX, Git is available by default.  Try ``git --version`` in a terminal session.  It should spit out something like the following:

```bash
git --version

git version 2.20.1 (Apple Git-117)

```

- For Windows, obtain Git from [this link](https://git-scm.com/download/win)


### (e) Pandoc Document Converter

[Pandoc](https://pandoc.org) is a versatile document converter which we will need during the second half of our workshop.  Installation links are avilable [on this page](https://pandoc.org/installing.html).


### (f) Essential R Packages

The base version of the R programming language installs basic packages for statistical analysis.  In addition, you will need several other packages.  For the purposes of this workshop, getting the [Tidyverse](https://tidyverse.org) group of packages should be sufficient.  If we need additional packages during the workshop, we can install those on the fly.

In either R-Studio or in R terminal session, simply type the following to install the tidyverse group:

```r

install.packages("tidyverse")


```

**Alternatively**, you can get them from GitHub:

```r

require(devtools)

devtools::install_github('hadley/tidyverse')


```

This will install the following packages:

- ggplot2
- dplyr
- tidyr
- readr
- purrr
- tibble
- stringr
- forcats


### (g) Get Yourself a Free GitHub Account

We will interact with GitHub throughout the workshop so you will need a free account with this service.  Sign up for a new account on [this page](https://github.com/join?source=header-home).  



## 2. Required Basic Proficiency

Because this is not a beginner workshop, we will not have time to cover any introductory lessons in using R.  Certain amount of proficiency is expected in R, RStudio and text editing.  Below, we provide some examples of the tasks we expect you to be able to do comfortably when you attend the workshop.

### (a) Skills in R and RStudio

- **Basic Operations**: R-Studio interface and what each window within the GUI is showing you

- **Package Management**: Ability to install packages from repositories such as

	- The **C**omprehensive **R** **A**rchive **N**etwork ([CRAN](https://cran.r-project.org))

	- [GitHub](https://github.com) source code repositories

	- [Bioconductor](https://bioconductor.org) packages

- **File Management**: Opening flat text data files in various formats such as tab-delimited (``.txt``) or comma-delimited (``.csv``) and storing them as objects in R's memory.  Saving data frames to hard disk as plain text files.

- **Data Wrangling**: Various methods of interfacing with your data objects

	- The ``object[1:10,1:5]`` coordinate system of accessing specific positions within data

	- The ``object$colname`` operator

	- Basic math operators such as ``mean``, ``min``, ``max``, ``summary`` etc.

	 
- **Graphics**: Basic skills in plotting

	- Histograms, scatterplots and basic plotting functions (see ``?plot()`` for details)

	
- **Finding Help**: 

	- R has comprehensive help documentation which can, in most cases be accessed with ``?function_name``.


### (b) Skills in Using Text Editors

- Opening new or existing files, editing, saving and closing them

- Perform search and replace functions on the entire file

 


### (c) Getting Help on Online Communities 

- Package-specific help forums

- R-Users Official [mailing lists](https://www.r-project.org/mail.html)
	
- [Stackexchange](https://stackexchange.com) and [Stackoverflow](https://stackoverflow.com)

- [How to ask good question and get useful answers](https://www.r-project.org/posting-guide.html)

- [How to provide a Minimum Working Example](https://stackoverflow.com/help/minimal-reproducible-example)







