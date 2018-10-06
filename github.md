# GitHub

<!-- TOC -->

- [GitHub](#github)
    - [Host open data sets on GitHub](#host-open-data-sets-on-github)
    - [why we should preview Jupyter notebook on NBview? Are there any relationship with Github?](#why-we-should-preview-jupyter-notebook-on-nbview-are-there-any-relationship-with-github)
    - [How to change default branch for GitHub pages?](#how-to-change-default-branch-for-github-pages)
        - [gh-pages](#gh-pages)
    - [What is index.html](#what-is-indexhtml)
    - [Any real world example of using GitHub issue tracker?](#any-real-world-example-of-using-github-issue-tracker)

<!-- /TOC -->

## Host open data sets on GitHub

Open datasets contains three parts:

1. The dataset, in format of `.csv`, `.json`, or a directory of those files.
2. The scripts involved for generating the dataset, e.g. scraper, data cleaning logics, data transformations. See [Dataprep](dataprep.md) for more information.
3. A `README.md` to show the basic information of this dataset.

Create a new file called `README.md`:

![](/assets/Screen Shot 2018-02-24 at 10.11.30 PM.png)

Write the description file which usually contains introduction of data source, the background of research, data fields, and data size, limitation and license. If you do not know what licenses are available, we suggest you to use [CC 4.0](https://creativecommons.org/licenses/by/4.0/). The file is written in [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) language, which has simple syntax that is legible in either plaintext format or rendered HTML format.

![](/assets/Screen Shot 2018-02-24 at 10.15.37 PM.png)

The overall shape of an open dataset looks like this: (you are looking at the rendered version of the markdown file)

![](/assets/Screen Shot 2018-02-24 at 10.15.56 PM.png)

See [homework2](https://github.com/hupilidemo/hkbu-big-data-media/tree/master/homework2) for a complete example.

> Note: The "limitation" is an important section in your README file. For example, you may only be able to crawl 95% of the original dataset due to technical problems. Highlighting that in your description file is crucial for other people to base their analysis on your dataset. No dataset is ideal. Incomplete dataset is also valuable. The principle is **full reporting**. 

## why we should preview Jupyter notebook on NBview? Are there any relationship with Github?

One can directly preview a Python notebook on GitHub. However, GitHub prohibits Javascript execution for security reasons. If you have interactive chart, e.g. from `echart`, `plotly`, those will not render on GitHub. NBViewer supports javascript and it is the first free online tool to preview Python notebook, so we recommend it. For concrete examples of dynamic charts, @ChicoXYC can find one notebook from our project archive: https://github.com/data-projects-archive .

## How to change default branch for GitHub pages?

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/23)

### gh-pages

## What is index.html

Basically, index.html is the default file served by the web server. So it is equivalent to visit example.com and example.com/index.html. Naming your file as index.html can lead to this more concise notation in browser's address bar and in communication campaigns -- the naming in the world of web is usually the shorter the better. More explanations are [here](https://en.wikipedia.org/wiki/Webserver_directory_index) .

## Any real world example of using GitHub issue tracker?

Use issue tracker as Q/A forum:

- [Builder Book](https://github.com/builderbook/builderbook/issues)

Use issue tracker as blog post backend:

- [@fouber's blog](https://github.com/fouber/blog/issues), written in Chinese, from a senior frontend engineer.

Use issue tracker as web comment store:

- [gitalk](https://gitalk.github.io/). See the comment thread [here](https://github.com/gitalk/gitalk/issues/1)
