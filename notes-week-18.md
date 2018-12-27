# Week 18: Python Engineering and Data Engineering

Best practices collected for your reference.

## Python Engineering

*This section is under development and it is optional*. Interested readers can do some self study based the following pointers.

### Write code in professional style

"Style Guide" is a kind of popular documentation in programming world. There are usually multiple ways to do one thing in programming world but some ways are apparently better. Writing code in a common style helps the readers to quickly understand the content and is less error prone. Python's traditional philosophy is that *there is one and only one way to do the right thing*.

Python community has this famous style guide called [PEP8](https://www.python.org/dev/peps/pep-0008/). You can automate this process by using the `pep8` executable (can be installed via `pip`). Another common reference is the [Google Python style guide](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)

### A word on syntactical sugar

Avoid syntactical sugars like

```python
b = a if a > 0 else 0
```

The full and "stupid" format is favoured for beginners. Consider the following style:

```python
if a > 0:
    b = a
else:
    b = 0
```

The readability of code is very important. It is a good practice to create less barrier for future readers, of which one may be yourself.

### File structure for a project

**TODO**

<!-- modules, __init__, requirements.txt, venv, .gitignore; if __name__ == "__main__" -->

### Object Oriented Programming

**TODO**

### Top-down or Bottom-up?

As a beginner, you are suggested to adopt a bottom-up approach and Python's flexibility/ simplicity is well suited for this approach.

When you become more senior and when you gradually take up architectural roles, you will more likely to work using a top-down approach. Common tools are like concept design, flow chart, sequence diagram, Object Oriented Design (OOD) and E-R graph.

### Inside a Python module

**TODO**

### Efficiency/ complexity

The computer science language of talking "efficiency" is "complexity". It usually refers to how the time needed to execute a program increase with the scale of problem size. It is a grand topic in algorithm design to talk about complexity. In our discussion, you may want to notice that the choice of data structure matters because their complexity is different. You don't have to master this from very beginning. Having this concept in mind allows you to sense the problem when it comes. Then you can more effectively ask for help.

Here is [one example](https://github.com/hupili/python-for-data-and-media-communication/blob/master/jupyter-notebook/timeit.ipynb) to show you that `set` and `list` have drastically different efficiency on solving one problem. (You will learn jupyter notebook in [notes-week-01.md](notes-week-01.md))

## Data Engineering

### Data pipelining

**TODO**: The fish bone structure in organising data pipeline

### Data versioning

**TODO**:

- Keep data, code and article at one place.

### Data wrangling journal

**TODO**:

- automate as many as you can
- take note of manual processing part

### From backend to frontend

**TODO**: Data is the interface
