## Install pyproj error

`pyproj` is the dependene of `geopandas`, which is further dependence for some of `plotly`'s mapping functions. When installing the library in Python 3.7, part of the error messages look like:

```text
    /usr/local/Cellar/python/3.7.0/Frameworks/Python.framework/Versions/3.7/include/python3.7m/pystate.h:238:15: note: 'curexc_traceback' declared here
        PyObject *curexc_traceback;
                  ^
    15 warnings and 15 errors generated.
    error: command 'clang' failed with exit status 1
```

[#137@pyproj](https://github.com/jswhit/pyproj/issues/136) shows that this is compatibility issue with Python 3.7. This is already fixed on the latest `pyproj` library, so one can install from code/ compile from code to solve the issue. And another error appears at this stage:

```text
    _proj.c does not exist in a repository copy.
    ImportError: Cython must be installed in order to generate _proj.c
    	to install Cython run `pip install cython`
```

Installing `Cython` can solve the problem. So the complete solution for this issue is:

```shell
pip install cython
pip install git+https://github.com/jswhit/pyproj.git
pip install geopandas
```

More discussion and further questions can go to [#87](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/87).