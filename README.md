Research Assistant Training
================

## Getting Started with GitHub

GitHub is a powerful collaboration and version control tool. We will be
using it for *project management*, *writing*, and *coding*.

### Project Management

By project management I primarily mean keeping track of assigned tasks
using the **Issues** tab on GitHub. We can have an ongoing conversation
here about each specific issue and close it out when its completed or
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

GitHub supports **markdown** syntax, which you’re probably more familiar
with than you might expect from time spent with **R Markdown**. Here are
some [markdown
basics](https://rmarkdown.rstudio.com/authoring_basics.html). We will be
writing using *parameterized* R Markdown so we can easily reference
model output instead of including it manually.

### Coding

GitHub was created for software development. While we may not actually
be developing software, we will be importing, wrangling, visualizing,
and modeling data, and it’s going to be essential for everyone to be on
the same page. Even if you were just working solo, you will be
collaborating with your past self and you should do yourself a favor and
impose good version controls on your code.

### Set-Up

To get started, complete Jenny Bryan’s [pre-workshop
set-up](https://happygitwithr.com/workshops.html?mkt_tok=eyJpIjoiT1RVelptVTNZams0T0dZMiIsInQiOiJlR0orVlVpaHZsRlwveWh5QUJPN2U1Q3BcL0pHVHo5RXJ5UkhabFlwVXM4NlEwcHhRTENQZmVxaEEyNnVLSkRFTTdVa0hyNjk4MkFHYUU1Nkt5VXNtRm9heFM3N3dnUFplZ1V5anpRTWdnWDVscE1lOUR6VzBHaGFQOUFhOGd1QkN3In0=#pre-workshop-set-up).
This can take up to a few hours, so plan accordingly. Note that the
following Git and GitHub training draws heavily from Jenny Bryan’s
training on using Git and GitHub from rstudio::conf(2019).

## GitHub Basics

Now that you’re set up, let’s get started.

### Just Once: Clone

First **clone** one of your repos, or a repo that you’re a collaborator
on. This is simply creating a local copy of the repo. You do this inside
RStudio by creating a new project and selecting `Version Control > Git`.

![](Figures/clone.png)

### Daily Work: Commit, Push, Pull

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
other collaborators have pushed, so you’re synced.

![](Figures/daily-work.png)

### Collaborating: Branches and Pull Requests

Because GitHub is very systematic in the way it manages commits, we will
run into commit errors when multiple people have changed the same thing
at the same time. To largely avoid this problem, among other things, we
will be using **branches**. Each branch is a separate version of the
repo that exists in parallel, one where you can make changes or
experiment without it affecting the working or **main** branch. In fact,
the main branch is protected so that you can’t accidentally push changes
to it.

To do your work as a collaborator, create a new branch on GitHub with a
short, descriptive name specific to the issue you’re working on (e.g.,
`paper-revision`). When you start a work session, make sure you select
the branch you want to work on from the dropdown in the Git pane in
RStudio. You can commit, push, and pull as usual to the branch you’re
working on. This will largely avoid commit errors because each
collaborator on a project should be working on a different issue and,
therefore, a different branch. When you’ve completed work on the issue
associated with the branch, create a **pull request** on GitHub and tag
me (i.e., `@marcdotson`). This allows me to review what you’ve done,
have a conversation with you about it, and eventually pull what you’ve
done into the main branch. I’ll then delete the branch specific to that
issue. Rinse and repeat.

## Project Organization

Each project has a similar organization. There are certain limitations
on the size and type of files that can be pushed to GitHub. There are
also certain things that shouldn’t be accessible by the public (e.g.,
data we have a license to access). For these reasons, we have folders
and files that are pushed to GitHub and those that are not.

### Pushed to GitHub

  - `/Code` Each script should do something specific (like tidyverse
    functions), have a descriptive name, and include number prefixes if
    they are meant to be run in a certain order (e.g.,
    `01_import_data.R`, `02_clean_data.R`).
  - `/Data` While all data live here, only data that are small enough
    and can be shared publicly will be pushed.
  - `/Figures` Figures live here, including images (saved as PNG files)
    and data referenced or used for tables, for use in the `README`,
    writing, and presentation.
  - `/Presentation` Slides for presentations (without any PDF knits).
  - `/Writing` The paper (using the paper template but without any PDF
    knits) and case studies on specific aspects related to the project
    (with the output set to `github_document`).
  - `README` The abstract and project organization details.

### Not Pushed to GitHub

  - `/Output` Output from model runs. These files tend to be too large.
    They are also something each user can create on their own.
  - `/Private` A catch-all folder for additional files specific to a
    project that might not have anywhere else to live.
  - `/Readings` Loose papers that you want to keep track of reading
    locally. GitHub is not a paper management system.

Note that you can create `Output`, `Private`, and `Readings` folders in
your local clone without worrying about them being pushed. We can
further modify the `.gitignore` file to add other folders and files that
aren’t pushed to GitHub.

## Miscellaneous Details

  - Use RStudio projects.
  - Use branches (never work on the main branch).
  - Use `here::here()` to specify files paths within R scripts.
  - Use tidyverse functions where possible.

## Links

  - [Tidyverse Style Guide](https://style.tidyverse.org)
  - [R Markdown: The Definitive
    Guide](https://bookdown.org/yihui/rmarkdown/)
  - [R Markdown
    Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/)
  - [Happy Git and GitHub for the useR](https://happygitwithr.com)
  - [What They Forgot to Teach You About R](https://whattheyforgot.org)