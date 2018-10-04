# pip

<!-- TOC -->

- [pip](#pip)
    - [pip2 and pip3](#pip2-and-pip3)
    - [Install pip3](#install-pip3)
    - [pip3 install modules](#pip3-install-modules)

<!-- /TOC -->

`pip` is the default package manager in Python. It is like the `npm` and `gem` in Javascript and Ruby.

## pip2 and pip3

Depending on when and how your system is installed, you may end up with `pip`, `pip3`, `pip`. Double check who is who from the version information:

```bash
%pip2 --version
pip 18.0 from /usr/local/lib/python2.7/site-packages/pip (python 2.7)
%pip3 --version
pip 18.0 from /usr/local/lib/python3.7/site-packages/pip (python 3.7)
%pip --version
pip 18.0 from /usr/local/lib/python2.7/site-packages/pip (python 2.7)
```

In my current system, `pip` refers to `pip2` which is used in combination with Python 2. Different from them, `pip3` is used in combination with Python 3.

## Install pip3

pip is already installed if you are using Python 2 >=2.7.9 or Python 3 >=3.4. You can type python --version to check out current version. If you are the older versions, please check out [here](https://pip.pypa.io/en/stable/installing/) to install and upgrade pip.

If you install pip in anaconda environment, try to use `!conda install pip3` in Jupyter.

## pip3 install modules

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-02.md#step-1-pip-install-modules). If you install in Jupyter, add `!` ahead of the command.
