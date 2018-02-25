# GitHub

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