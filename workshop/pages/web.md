---
title: Writing Reports and Publishing Websites
author: Wyoming IBC
date: October 7, 2019
---

[Return to Main Page](../index.html)



In this section, we will look at a simple text formatting program to write reports and convert it into a number of different formats.  Later, we will write a simple website and publish it on GitHub pages.  If you adopt these tools, they could provide you with a simple to maintain and fast workflow for writing reproducible, and beautiful looking reports/manuscripts and for publishing website that don't look like they were written in 1990.


## Table of Contents

[1. Markdown - A Markup Language](#markdown-a-markup-language)

[2. Publish A Website](#publish-a-website)

[3. Multiformat Document Conversion](#multiformat-document-conversion)


<br><br><br><br><br>
<br><br><br><br><br>
<br><br><br><br><br>

## 1. Markdown - A Markup Language

In the simplest form, Markdown allows you to write documents that could be easily converted into elegant publishable formats such as html or pdf.  It is a set of easy-to-understand and write instructions that can be interpreted and rendered into downstream products. 

Let's do a small demonstration of the capabilities of Markdown.  There are many editors available online that allow you to write Markdown code and instantly convert that to html. 


### [Visit StackEdit.io](https://stackedit.io)


Follow onscreen instructions to write markdown code and watch it get translated to html.



<br><br>

## 2. Publish A Website

Let's go back to the original repository we created in the first part of this workshop.  It should be on your computer inside a folder called ``gitproject``.  Currently there is only one file in that directory:


```bash

cd /Users/wyoibc/gitproject

ls -lh

-rw-r--r--  1 wyoibc  inbre   112B Oct  3 21:20 README.md


```

Let's imagine we are creating a website for a course you teach.  As you probably already know, websites are served through a markup language called ``HTML`` (short for **H**yper **T**ext **M**arkup **L**anguage.  But we are not going to teach you to write HTML.  Instead you are going to make use of the markdown skills you have just developed. Usually, the default page on any website (e.g. www.google.com) is a HTML file called ``index.html``.  Since we are working with markdown, we will create a file called ``index.md`` (md for markdown).


```bash

touch index.md

ls -lh

-rw-r--r--  1 wyoibc  inbre     0B Oct  7 07:57 index.md

vim index.md  ## Or use your favorite text editor

```

Build the page content as follows:

```bash

---
title: BIOINFO-101 Bioinformatics for Beginners
author: YOUR NAME
date: October 7, 2019
---

```

- This first section is called the header of the markdown document.  It's contents are used not only for creating the title of the page, but also as meta data to be inserted into the html.

Next, we will prepare a clickable menu.




<br><br>

## 3. Multiformat Document Conversion





