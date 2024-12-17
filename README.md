# ASC Training


This repo is a collection of training resources for students working on
projects at the [Analytics Solutions
Center](https://huntsman.usu.edu/asc/) (ASC). The ASC collaborates with
sponsor organizations to provide students at the [Jon M. Huntsman School
of Business](https://huntsman.usu.edu), and [Utah State
University](https://www.usu.edu) generally, with real-world experiences
working on data-related projects. Each ASC project is mentored by a
faculty member from the [Data Analytics and Information Systems
Department](https://huntsman.usu.edu/dais/). The following training is
provided for students on projects that I mentor, in conjunction with
repositories using my
[asc-template](https://github.com/marcdotson/asc-template).

## Python

Installing Python locally (i.e., on your computer), along with
maintaining a reproducible environment, can be challenging for even
advanced users. As immortalized by XKCD:

<p align="center">
<img src="figures/xkcd_python-env.png" width="400">
</p>

An environment is composed of the Python, libraries, and library
dependencies used for a given project. What makes an environment
reproducible is keeping track of *which* version of the Python,
libraries, and library dependencies we’re using for a given project.
While “keeping track” could happen in many different ways, ideally we
want to keep track of our environment such that it can be easily
*reproduced* on another machine, by you (including future you) or
someone else. For our purposes, we need to be sure that everyone working
on our ASC project, including anyone at the sponsor organization, can
easily reproduce our environment and run the associated code.

Python is a big tent, and there are many ways to manage an environment.
I recommend using [pyenv](https://github.com/pyenv/pyenv) to install and
maintain Python versions and
[venv](https://docs.python.org/3/library/venv.html) to keep track of the
version of the libraries and library dependencies within our project’s
reproducible environment.

### pyenv

We need to keep track of which version of Python we’re using for a
number of reasons. Here’s two:

- Not all Python versions are (or were) backwards compatible (i.e., if
  someone runs our code with a different version of Python, it might not
  work).
- Python comes pre-installed on many operating systems since some of the
  actual operating system uses that specific version of Python. This is
  a version *should not be used* for any project work.

For these and other reasons (if not the last one alone), we need the
ability to maintain multiple versions of Python on the same computer.
[pyenv](https://github.com/pyenv/pyenv) is a Python version management
tool that is designed to be as *simple* as possible. Though what
constitutes “simple” is a matter of experience and your mileage may
vary.

> [!TIP]
>
> ### Using the Command Line
>
> While pyenv is simple, it will require you to use the command line
> (i.e., terminal or shell). Be patient and *take your time* walking
> carefully through the [installation
> instructions](https://github.com/pyenv/pyenv?tab=readme-ov-file#installation).
> Daniel Chen, who introduced me to pyenv, also has a [great
> write-up](https://chendaniely.github.io/python_setup/210-python_install.html)
> of the installation instructions that may be a bit easier to follow. A
> few things to help as you install:
>
> - The command line is the programming interface into your operating
>   system itself. You don’t have to know everything about it to follow
>   instructions.
> - When you get to the section [Set up your shell environment for
>   pyenv](https://github.com/pyenv/pyenv?tab=readme-ov-file#b-set-up-your-shell-environment-for-pyenv),
>   the instructions are different based on the *type* of command line.
>   If you’re on a Mac that’s running macOS Catalina 10.15.7 or later,
>   the terminal is Zsh. If you’re using Linux, the shell is Bash (and
>   you probably already know that). And if you’re using Windows, you’ll
>   be using the [pyenv-win](https://github.com/pyenv-win/pyenv-win)
>   fork with PowerShell.

Now that you have pyenv installed, you can install and manage all the
versions of Python on your computer. To see what versions you already
have installed, on the command line, run `pyenv versions`. At first this
is probably just the system version. Note that if you’ve installed
Python before pyenv, it won’t be listed: `pyenv versions` will only list
the system version and any additional versions you install using pyenv.
To see all the available versions of Python that you can install, run
`pyenv install --list`. This can be overwhelming, but a good place to
start is the latest version of Python that has a stable release (i.e.,
doesn’t have a `-dev` tag). For example, to install Python 3.12.4, run
`pyenv install 3.12.4`.

Remember how you shouldn’t use the operating system version of Python?
You can set the default version of Python that you’ll use (leaving the
operating system to do it’s own thing). For example, to set Python
3.12.4 as the default global version, run `pyenv global 3.12.4`. If you
run `pyenv versions` again you should see an asterisk by the global
default you specified.

There’s a lot more that [pyenv can
do](https://realpython.com/intro-to-pyenv/), but now you should at least
be set to safely manage and use Python.

### venv

Why do we need to track the versions of the libraries and library
dependencies we use?

- Libraries change. Functions, methods, and parameters get modified or
  deprecated.
- Just because our project code works now doesn’t mean that it will work
  for someone else or in the future.

Ensuring our project environment is reproducible enables collaboration,
future-proofing, and open science.

By default, all libraries are installed in a single, global library
known as the *system library*. What we need is a *project library*. This
helps highlight an important feature of reproducible environments: Each
project will have its own project library and thus be *isolated*. If two
projects use different versions of the same package, they won’t conflict
with each other because they’ll each have their own project library.
Well, not *exactly*. Python employs a global cache to avoid having to
install the version of a given library more than once. (Note that if
you’ve installed Python prior to using pyenv, you may have a global
cache that is borked. You can run `pip cache purge` in the command line
to start fresh.)

The [venv](https://docs.python.org/3/library/venv.html) library comes
pre-installed with Python as the default reproducible (or *virtual*,
hence the v in venv) environment management tool. It works in two steps.
First, we must create a project library. Second, we keep track of the
versions of the libraries and library dependencies that we use. However,
the easiest way to implement our reproducible environment will require
two additional tools: an IDE and version control.

## Positron

A reliable integrated development environment (IDE) is arguably your
most important tool as a data analyst or data engineer. There are many
options, but I recommend [Positron](https://positron.posit.co), a
next-generation data science IDE. Built on VS Code’s [open source
core](https://github.com/microsoft/vscode), Positron combines the
multilingual extensibility of [VS Code](https://code.visualstudio.com/)
with essential data tools common to language-specific IDEs.

<img src="figures/positron-logo.png" style="width:40.0%"
data-fig-align="right" />

- Why do I have to save a file before I can open another? Is it the same
  file type? Some preference I can overwrite?
- What about rainbow parentheses and indentations? Is that an extension?

### Console

### Data Explorer

Open CSV and Parquet files to preview without even importing first.

### Variables Pane

### Plots Pane

Dedicated space for visualizations.

### Help Pane

Question mark after command.

Copy examples.

### Viewer Pane

Communication. View locally hosted URL and rendered documents from
Quarto. Dashboards.

## Using GitHub

> [!CAUTION]
>
> Some of the following GitHub details include instructions that are
> RStudio-specific. I am working on generalizing this to
> [Positron](https://positron.posit.co) for use with both R and Python.

GitHub is a powerful collaboration and version control tool. We will be
using it for *project management*, *writing*, and *coding*.

### Project Management

By project management I primarily mean keeping track of assigned tasks
using GitHub’s **Issues**. We can have an ongoing conversation there
about each specific issue and close it out when its completed or
resolved. Be sure to tag collaborators you want to see the conversation
(e.g., `@marcdotson`). Think of this as an email thread or Slack channel
except all of the conversations are in one place, easily searchable, and
automatically archived.

### Writing

Think of using GitHub to collaborate on writing as using something like
Google Docs. It is essential that we document what we’re doing in each
project as we do it. This is true for a number of reasons.

1.  Writing forces you to think clearly about what you’re doing.
2.  If you’re coding, think of the associated writing as long-form
    comments.
3.  The final product of any project is going to be a paper, so start
    writing it now.

GitHub supports **Markdown** syntax, which you’re probably more familiar
with than you might expect from time spent with **Quarto**. We will be
writing using *parameterized* Quarto documents so we can easily
reference model output instead of including it manually. See below for
more on using Quarto.

### Coding

GitHub was created for software development. While we may not actually
be developing software, we will be importing, wrangling, visualizing,
and modeling data using code, and it’s going to be essential for
everyone to be on the same page. Even if you were just working solo, you
will be collaborating with your past self and you should do yourself a
favor and impose good version controls on your code.

### Set-Up

To get started, complete Jenny Bryan’s [pre-workshop
set-up](https://happygitwithr.com/workshops.html?mkt_tok=eyJpIjoiT1RVelptVTNZams0T0dZMiIsInQiOiJlR0orVlVpaHZsRlwveWh5QUJPN2U1Q3BcL0pHVHo5RXJ5UkhabFlwVXM4NlEwcHhRTENQZmVxaEEyNnVLSkRFTTdVa0hyNjk4MkFHYUU1Nkt5VXNtRm9heFM3N3dnUFplZ1V5anpRTWdnWDVscE1lOUR6VzBHaGFQOUFhOGd1QkN3In0=#pre-workshop-set-up).
This can take up to a few hours, so plan accordingly. Note that the
following Git and GitHub training draws heavily from Jenny Bryan’s
training on using Git and GitHub from rstudio::conf(2019).

### GitHub Basics

Now that you’re set up, let’s get started.

#### Just Once: Clone

First **clone** one of your repos, or a repo that you’re a collaborator
on. This is simply creating a local copy of the repo. You do this inside
RStudio by creating a new project and selecting `Version Control > Git`.

![](figures/clone.png)

> [!NOTE]
>
> ### `.python-version`, `/.venv`, and `requirements.txt`
>
> Just like we can specify a global default version of Python using
> pyenv, we can also specify a *local* default version of Python using
> pyenv as part of our reproducible environment. Note that this has
> already been done if the project repository was generated using my
> [asc-template](https://github.com/marcdotson/asc-template).
>
> To create this on your own, or modify an existing `.python-version`
> file, after navigating to the project’s working directory in the
> command line, you would run `pyenv local 3.12.4`, assuming you want
> Python 3.12.4 to be set as the default. This would create (or modify)
> a `.python-version` file in that directory that specifies the version
> of Python to use for that project.
>
> First, it creates a project library (see `/.venv` below). Second, it
> maintains a file called `requirements.txt` listing all of the versions
> of the libaries and library dependencies you’ve installed in your
> project library. Here’s how it works:
>
> - To add all of these same libraries on a new machine, once you have
>   the project working directory, simply run
>   `pip install -r requirements.txt`.
> - Whenever you install new libraries or decide to update the versions
>   of libraries you use, run `pip freeze > requirements.txt` to update
>   `requirements.txt`.
>
> The `requirements.txt` from venv file, along with the hidden
> `.python-version` file from pyenv, ensure that we have and can
> maintain a reproducible environment for our project.
>
> Before the `requirements.txt` file can be created and updated, the
> project library itself needs to be generated. It is a hidden folder
> called `/.venv` that is not pushed to GitHub. Note that this has
> already been done if the project repository was generated using my
> [asc-template](https://github.com/marcdotson/asc-template).
>
> To create this on your own, after navigating to your project’s working
> directory in the command line, you would create the project library
> for your project by running `python -m venv .venv`. This would create
> a `/.venv` folder in the working directory.

#### Daily Work: Commit, Push, Pull

Now you can open up the RStudio Project in the local, cloned repo and
work on the project. You have a new Git pane in RStudio that notifies
you that changes you’ve made means you are out-of-sync with the
**remote** repo (i.e., the one on GitHub). Once you’ve made a number of
changes, you click on the files you want to **commit** and click commit.
Think of a commit as saving a snapshot of all of the changes you’ve made
across these files all at once. Include a clear commit message. You’ll
do this fairly frequently for your local repo.

Eventually you’ll be ready for other people to have access to your
changes on the remote repo. To do this, you’ll click on the green up
arrow to **push** your changes to the remote repo. You push far less
often than you commit, maybe once a work session, since this means you
think it’s ready for others to have access to. Each time you push, all
of your commits are archived on the remote repo, including the **diff**
or the side-by-side comparison of what changes you made to the previous
version.

When you start a new work session, you’ll want to click on the blue down
arrow to **pull** the latest changes from the repo, possibly the work
other collaborators have pushed, so you’re synced. Note that hidden
files (i.e., `.gitignore` and `.Rprofile`) may try to change on their
own. When you open the commit dialog, you can click on these modified
files and hit **revert** to undo these changes.

![](figures/daily-work.png)

#### Collaborating: Branches and Pull Requests

Because GitHub is very systematic in the way it manages commits, we will
run into commit errors when multiple people have changed the same thing
at the same time. To largely avoid this problem, among other things, we
will be using **branches**. Each branch is a separate version of the
repo that exists in parallel, one where you can make changes or
experiment without it affecting the working or **main** branch. You
should *never* push changes to the main branch directly.

To do your work as a collaborator, create a new branch on GitHub with a
short, descriptive name specific to the issue you’re working on (e.g.,
`paper-revision`). When you start a work session, make sure you select
the branch you want to work on from the dropdown in the Git pane in
RStudio. You can commit, push, and pull as usual to the branch you’re
working on. This will largely avoid commit errors because each
collaborator on a project should be working on a different issue and
likely a different branch. When you’ve completed work on the issue
associated with the branch, create a **pull request** on GitHub and tag
me (i.e., `@marcdotson`). This allows me to review what you’ve done,
have a conversation with you about it, and eventually pull what you’ve
done into the main branch. I’ll then delete the branch specific to that
issue. Rinse and repeat.

### Cleaning Up Branches

While your daily work won’t require you to write any Git code,
*eventually* you’ll need to clean up the branches you have on your local
clone. You’ll need to do this from the command line Terminal. I
recommend you use the one available in RStudio once you’ve opened the
project you want to clean up.

- In the Terminal, type `git branch --merged` to see which branches have
  been merged into **main** and can be deleted from your local clone.
- Then type `git branch -d <branch>` where `<branch>` is replaced with
  the name of the merged branch that you’d like to remove from your
  clone.
- Finally, use `git fetch -p` to prune remote-tracking branches that are
  no longer on remote (i.e., on GitHub).

Voila! A cleaned up branch drop down in your Git pane makes things
easier to navigate.

### Links

- [Happy Git and GitHub for the useR](https://happygitwithr.com)
- [What They Forgot to Teach You About R](https://rstats.wtf)

## Using Quarto

> [!CAUTION]
>
> The following Quarto details are written primarily for R users. I am
> working to generalize this for Pythonistas as well, including how
> Quarto differs from Jupyter Notebooks. See:
>
> - [Quarto Gallery](https://quarto.org/docs/gallery/)
> - [Introduction to
>   Quarto](https://posit-conf-2024.github.io/quarto-intro/)
> - [Build-a-Dashboard
>   Workshop](https://posit-conf-2024.github.io/quarto-dashboards/)
>
> Notes from the [Quarto Crash
> Course](https://www.youtube.com/watch?app=desktop&v=_VKxTPWDhA4)
> series:
>
> - Bridge the gap between coding environments that you might enjoy and
>   output formats that you need to produce results in to inform
>   decision-making.
> - Does Positron’s base install now include Quarto or does it need to
>   be added as an extension?
> - Include a project format file in \_quarto.yml to specify project:
>   output-dir: folder-name. Also needed to set the working directory
>   project: execute-dir: project.
> - Note the Visual Editor as an option, especially for markdown syntax
>   (hello tables and citations).
> - quarto convert doc.qmd to convert a Quarto document into a Jupyter
>   notebook and the render with quarto render doc.ipynb.
> - Formatting with CSS-like divs and spans.
> - Fenced div with layout?
> - Parameters specified inside of a cell using \#\| or still in the
>   YAML header itself? May be different for Python with “\#\| tags:
>   [parameters](#parameters)”
> - Is there something as simple as requirements.txt for R packages?
> - Pathlib or OS libraries?
> - Reference Gallery.
> - What about GitHub pages as a format for creating a source website
>   that’s hosted entirely on GitHub?

Quarto is a powerful typesetting tool and the multilingual replacement
for R Markdown. Instead of writing in Word or a Google Doc, by using
Quarto we can include code blocks, parameterize the document to easily
replicate reports, and output our work as Word documents, PDFs,
PowerPoint presentations, HTML slide decks, GitHub pages, etc.

### Markdown

Markdown is a simple, generic typesetting syntax. Here are some
[Markdown
Basics](https://quarto.org/docs/authoring/markdown-basics.html). GitHub
recognizes this syntax, including in Issues and pull requests.

### Code

Quarto allows us to include code blocks and output as part of the
document. In other words, this is what we need to create reproducible
reports. You can also include R, Python, C++, Stan, and other code
blocks and output.

### Pandoc

Pandoc is the typesetting software behind the scenes that allows us to
take a Quarto document and output it as nearly anything.

### Quarto Basics

#### YAML

The header at the top of any Quarto document is coded in **YAML** (i.e.,
Yet Another Markup Language), which follows a simple `key: value`
syntax. For most Quarto documents in a project repo, you should set
`format: gfm`. When you knit changes to your Quarto document, it will
create a separate markdown document using “GitHub Flavored Markdown”
that GitHub can parse. For example, the header for this document is:

    ---
    title: "Research Assistant Training"
    format: gfm
    ---

#### Parameters

Ever have to go through and manually change any data or model output
referenced in a report? Not only is this costly and error prone, but it
is the definition of non-reproducible. Parameters in Quarto help solve
part of this problem.

Parameters are included as part of the header:

    ---
    title: "Research Assistant Training"
    format: gfm
    params:
      name: "Analytics"
      data: "analytics_data.rds"
    ---

Parameter values can then be referenced in the report (including code
blocks) using the parameter name as a list. For example, reference
`params$name` within an R code block to print the year specified as a
parameter or load the data specified as a parameter by referencing
`data <- read_rds(params$data)` within an R code block.

Much like the rule-of-thumb regarding functions (i.e., if you have to
copy and paste more than twice, create a function), if you find yourself
copying and pasting a value that you may need to update (or change to
create a report for a different audience), add it as a parameter.

#### References

We can specify a bibliography in the header:

    ---
    title: "Research Assistant Training"
    format: gfm
    bibliography: references.bib
    params:
      name: "Analytics"
      data: "analytics_data.rds"
    ---

We can can use the bibliography `references.bib` to include regular
single-paper citations using `[@citation]` or multiple-paper citations
using `[@citation; @citation]`, in-line citations using `@citation`, or
citations without the Author using `[-@citation]`.

Additionally, each section and sub-section can be referenced by adding a
`#sec` identifier to any heading and referencing `@sec`. For example,
`## Introduction {#sec-intro}` would be referenced as `@sec-intro`.

#### Code Blocks

There are a variety of options for each code block. In addition to
specifying the language used within the code block, the code block can
be given an identifier, can have warnings suppressed, can run without
producing output, etc. These options are specified using YAML syntax
following the hashpipe operator `#|` within the body of the code block.
Any code block option that should apply to the document in its entirety
can simply be moved into the header.

#### Tables and Figures

Using Quarto means we can use Markdown, R, and LaTeX (along with other
languages) interchangeably. While we can create a table using LaTeX or
Markdown, we can also just print a data frame using `knitr::kable()` and
the `{kableExtra}` package. The name of the code block is the given
label that can be referenced, for example `#| label: tbl-planets`
referenced with `@tbl-planets` (note that the `tbl-` prefix is
required). For more table options, see the [kableExtra
vignette](https://haozhu233.github.io/kableExtra/awesome_table_in_pdf.pdf).

Similarly, we can include a figure using LaTeX, Markdown, or `knitr`. If
`knitr::include_graphics()` is used, the name of the code block is the
label that can be referenced, for example `#| label: fig-elephant`. If
Markdown `![]()` syntax is used, the same label would be
`{#fig-elephant}`. In either case, the figure would be referenced with
`@fig-elephant` (note that the `fig-` prefix is required).

When Quarto creates a plot and other figures, by default they are stored
in a badly named folder in the same directory as the Quarto document.
Instead, we can modify the header to direct where created figures should
be saved.

    ---
    title: "Research Assistant Training"
    format: gfm
    bibliography: references.bib
    params:
      name: "Analytics"
      data: "analytics_data.rds"
    knitr:
      opts_chunk:
        fig.path: "../figures/"
    ---

The name of the figures will match the label of the code block in which
it was created.

#### Equations

Equations are now supported when producing a GitHub document. Use `$`
around any in-line LaTeX notation or `$$` around equations specified as
a separate line. For example, we can reference $y^2$ as well as:

$$
y^2.
$$

### Links

- [Quarto](https://quarto.org)
- [Quarto for
  Academics](https://quarto.org/docs/blog/posts/2023-05-22-quarto-for-academics/)
- [Quarto
  questions](https://occasionaldivergences.com/posts/quarto-questions/)
- [The YAML
  Fieldguide](http://ymlthis.r-lib.org/articles/yaml-fieldguide.html)
- [LaTeX Paper
  Template](https://github.com/marcdotson/repo-template/blob/main/Writing/paper-template.Rmd)

## Project Organization

Each project has a similar organization. There are certain limitations
on the size and type of files that can be pushed to GitHub. There are
also certain things that shouldn’t be accessible by the public (e.g.,
data we have a license to access). For these reasons, we have folders
and files that are pushed to GitHub and those that are not. If you are
starting a new project, please set up the repo using the
[repo-template](https://github.com/marcdotson/repo-template).

### Pushed to GitHub

- `/code` Each script should do something specific (like tidyverse
  functions), have a descriptive name, and include number prefixes if
  they are meant to be run in a certain order (e.g., `01_import-data.R`,
  `02_clean-data.R`) and functions in `/code/src`.
- `/data` While all data live here, only data that are small enough and
  can be shared publicly will be pushed.
- `/figures` Figures live here, including images (saved as PNG files)
  and data referenced or used for tables, for use in the `README`,
  writing, and presentation.
- `/presentations` Slides for presentations (without any PDF knits).
- `/renv` Information on the reproducible environment (see below).
- `/writing` The paper (using the paper template but without any PDF
  knits) and case studies on specific aspects related to the project
  (with the output set to `gfm`).
- `.Rprofile` Information on the reproducible environment (see below).
- `README` The abstract and project organization details.
- `renv.lock` Information on the reproducible environment (see below).

### Not Pushed to GitHub

- `/output` Output from model runs. These files tend to be too large.
  They are also something each user can create on their own.
- `/private` A catch-all folder for additional files specific to a
  project that might not have anywhere else to live.

Note that you can create `/output` and `/private` folders in your local
clone without worrying about them being pushed. We can further modify
the `.gitignore` file to add other folders and files that aren’t pushed
to GitHub.

## Reproducible Environment

> [!CAUTION]
>
> The Reproducible Environment section is being worked on to also
> include Python-only virtual environments.

Every package you install lives in your system library, accessible to
all projects. However, packages change. Add a reproducible environment
by creating a project library using the `{renv}` package.

- Initialize the project library once using `renv::init()`. This will
  create the `renv` folder (with its own `.gitignore`), a lockfile
  `renv.lock`, and an `.Rprofile` file.
- Once you’ve installed packages, add them to the project library using
  `renv::snapshot()`.
- To install the specific packages of an already-existing project
  library, use `renv::restore()`.
- To update all packages in the project library, call `renv::update()`.
  Make sure code is working with the updated packages before calling
  `renv::snapshot()` to update the lockfile.

> [!TIP]
>
> ### Non-Standard Repositories
>
> If a package you’re using has a non-standard repository (i.e., not on
> CRAN or another supported repository network), you’ll need to update
> the `renv.lock` file to ensure the environment remains reproducible.
> When `renv::status()` runs it will tell you if a repository you
> downloaded a package from is non-standard and has difficulty tracking.
>
> For example, for Stan packages, the R entry in the json `renv.lock`
> file will need to include:
>
>     {
>       "R": {
>         "Version": "4.3.1",
>         "Repositories": [
>           {
>             "Name": "CRAN",
>             "URL": "https://packagemanager.posit.co/cran/latest"
>           },
>           {
>             "Name": "Stan",
>             "URL": "https://mc-stan.org/r-packages"
>           }
>         ]
>       }
>     }

Read [here](https://rstudio.github.io/renv/index.html) for more on using
`{renv}`, including creating and maintaining Python environments.

## Miscellaneous Details

- Use branches (never work on the main branch).
- Use `here::here()` to specify files paths within R scripts.
- Use tidyverse functions and the [tidyverse
  style](https://style.tidyverse.org) where possible.
