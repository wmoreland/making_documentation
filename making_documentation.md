---
title: Making Documentation with Markdown, Pandoc, and LaTeX
author: [William M. Moreland]
date: 2022-06-22
lang: en-GB
papersize: a4
titlepage: true
titlepage-rule-color: 10099F
colorlinks: true
subject: "Documentation"
keywords: [Documentation, Markdown, Pandoc, LaTeX]
---
## Introduction

Markdown is a simple markup language which allows you to quickly write material using minimal technical formatting and yet produce a more complex and aesthetically-pleasing document for your intended audience. The advantage of this is that you can:

- concentrate on content rather than formatting
- consistently apply the same format to a series of documents
- easily track changes using version control software such as Git

Pandoc is a program for converting from one markup language to another but this case we are using Pandoc to convert from Markdown to PDF while applying formatting supplied by a LaTeX template.

LaTeX is a typesetting language developed for technical or scientific documents. It is extremely customisable but also pretty complicated. By using Markdown together with Pandoc and LaTeX we can write with ease and yet produce professional-looking documentation.

This document is a guide to producing a document just like this one! This document is heavily based on a guide by Dave Johnson found [here](https://thisdavej.com/build-an-amazing-markdown-editor-using-visual-studio-code-and-pandoc/).

## Setting Up

First you need a text editor. It can be as simple as Windows Notepad but in my case I am using Microsoft Visual Studio Code which enables automatic correction of formatting and inserting of snippets. See the documentation from Microsoft [here](https://code.visualstudio.com/Docs/languages/markdown) for more information on setting up VS Code.

Next you need to install Pandoc, the documentation and install files you can get from [here](https://pandoc.org/installing.html). To run Pandoc from within VS Code you will need an extension. I am using [vscode-pandoc](https://marketplace.visualstudio.com/items?itemName=DougFinke.vscode-pandoc) by Doug Finke.

Other valuable extensions for VS Code are:

- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) by David Anson which checks for formatting and syntax errors in Markdown.
- [Markdown helper](https://marketplace.visualstudio.com/items?itemName=joshbax.mdhelper) by Joshua Baxter which applies Markdown formatting to text
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) which checks spelling

You will also need to install a LaTeX distribution. On Windows the simplest way is to install MiKTeX, the instructions for which can be found [here](https://miktex.org/download).

Finally, in order to produce a PDF which looks like this one, you will need to install the Eisvogel Pandoc theme by Pascal Wagler which can be found [here](https://github.com/Wandmalfarbe/pandoc-latex-template). This needs to be installed in your LaTeX templates directory which on Windows is usually located at

`C:\Users\yourusername\AppData\Roaming\pandoc\templates\`

You can find your Pandoc user data directory by typing `pandoc --version` into a terminal.

## Usage

Create a directory somewhere to house the necessary files for the documentation you want to write (e.g., "Making Documentation"). Inside that directory make a blank file with the name of the documentation and the .md file extension for Markdown (e.g., "making_documentation.md"). In VS Code, open the root directory (e.g., "Making Documentation") and then the Markdown file (e.g., "making_documentation.md"). Now you can start to write.

Start by entering the following into the Markdown file:

```markdown
---
title: Making Documentation
author: Your Name
date: 2021-03-19
---
## My first heading

Here is a line of text that will be converted by Pandoc into PDF.

```

In VS Code, save the file and then to render the PDF with Pandoc, press `Ctrl + k` and then `p` which brings up a selection box where you can pick PDF. The PDF should open automatically once it is finished rendering.

You will see that whilst it looks pretty good, it's not got the Eisvogel theme applied. To fix this, in the root directory (e.g., "Making Documentation") create another directory called ".vscode" and inside that create a file called "settings.json". Type the following into that file:

```json
{
    "pandoc.pdfOptString": "--from markdown --template eisvogel",
}
```

Save the settings file and try rendering your PDF again. Much better! If you want to get fancier, you could add a title page to the document by adding `titlepage: true` to the so-called front matter at the start of your Markdown file (in between the two lines of dashes where title, author, date, etc., are defined).

This is as far as this documentation will go but there is a lot more information out there on how to add further complexity to your document such as tables and references. For now though I will end with an image (Fig. \ref{fimm}), inserted by adding the following line to your text in the Markdown file (remove the trailing ellipses):

```markdown
![caption](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37...
/Fimmvorduhals_2010_03_27_dawn.jpg...
/640px-Fimmvorduhals_2010_03_27_dawn.jpg)
```

![Fimmvörðuháls at dusk on 27 March 2010 by Henrik Thorburn\label{fimm}](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Fimmvorduhals_2010_03_27_dawn.jpg/640px-Fimmvorduhals_2010_03_27_dawn.jpg)

## Links

- [Dave Johnson's guide](https://thisdavej.com/build-an-amazing-markdown-editor-using-visual-studio-code-and-pandoc/)
- [VS Code and Markdown](https://code.visualstudio.com/Docs/languages/markdown)
- [Eisvogel pandoc template](https://github.com/Wandmalfarbe/pandoc-latex-template)
- [Markdown cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Pandoc user guide](https://pandoc.org/MANUAL.html)
