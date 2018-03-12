# Jupyter notebook

It is suggested to enter virtual environment before using Jupyter notebook.

## Virtual environment

Create virtual environment:

```
pyvenv venv
```



Enter virtual environment:

```
source venv/bin/activate
```

When you see `(venv)` appear in front of your command line prompt, that means the you are in the virtual environment. Always check this prefix to make sure you are working in the right environment. You can use `deactive` command to exit current virtual environment.

If you want to quit the virtual environment, you can use "Control+C".

## Jupyter notebook

Now you can install and enter Jupyter notebook.

Install Jupyter notebook: \(you only need to do this once for every virtual environment\)

```
pip3 install jupyter
```

Run Jupyter notebook as:

```
jupyter notebook
```

By default the notebook will be available at [http://localhost:8888/tree](http://localhost:8888/tree)

## Runtime troubleshooting guide

* Rerun all the cells
* Restart the kernel
* Clear the output cells

