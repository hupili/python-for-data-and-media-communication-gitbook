# Jupyter notebook

It is suggested to enter virtual environment before using Jupyter notebook. Because in the following study, we may need to install some packages and modules in Jupyter notebook. It's necessary to keep those files in the same path, so Jupyter can source the modules when you want to use.

## Virtual environment

Create virtual environment:

```bash
$ pyvenv venv
```

Enter virtual environment:

```bash
$ source venv/bin/activate
```

When you see `(venv)` appear in front of your command line prompt, that means the you are in the virtual environment. Always check this prefix to make sure you are working in the right environment. You can use `deactivate` command to exit current virtual environment.

## Jupyter notebook

Now you can install and enter Jupyter notebook.

Install Jupyter notebook: **(you only need to do this once for every virtual environment)**

```bash
$ pip3 install jupyter
```

Run Jupyter notebook as:

```bash
$ jupyter notebook
```

By default the notebook will be available at [http://localhost:8888/tree](http://localhost:8888/tree)

So, next time when you use your jupyter notebook, you just need to type following commands in your terminal

```bash
$ source venv/bin/activate
$ jupyter notebook
```

## Runtime troubleshooting guide

* Rerun all the cells
* Restart the kernel
* Clear the output cells

## Install frequently used dependencies

You do not want to install and re-install dependencies every time. It is more convenient to setup a virtual environment and install common dependencies/ modules for data analysis.

You can download this [requirement.txt](https://github.com/hupili/python-for-data-and-media-communication/blob/master/requirements.txt) and then run the following command (inside virtual environment)

```
pip install -r requirements.txt
```