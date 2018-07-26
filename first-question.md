# Setup Python Environment on Windows and MAC

## MAC

Modern Mac OS versions come with Python 2.7.x installed (or Python 2.6.1 if an older Mac OS X version), but with several reasons, many Python users may need to update Python in Mac OS to a newer version like Python 3.  
* You can type`python --version` to check out the version on your computer.

### How to Install the Updated Python 3 in Mac OS  
1. by using the Python package installer from python.org
    * Go to Python.org and download the [latest Python installer package](https://www.python.org/downloads/)  
    * Run the Python installer package and install Python 3 onto the Mac   

    Once Python 3 is installed you will find a Python3 folder within the /Applications directory of your Mac. 
2. Install Python 3 with Homebrew
    * [Homebrew](https://brew.sh/) is a commonly used package manager for MAC software. The usual way to install package by homebrew is `brew install {package}`
    * Reference: [MAC OSX 正確地同時安裝 PYTHON 2.7 和 PYTHON3](https://stringpiggy.hpd.io/mac-osx-python3-dual-install/#step1)

## Windows

The Unix/ Linux world has a collection tools that nicely work together. However, you will need to troubleshoot environment frequently on Windows. I suggest you to use MAC or rely on our lab for this semester, to reduce such hussle. Once you master the essence, it is easier to move to other environments later.I have not used Windows for a long time. There are problems stitching things together. For those who have tried/ are trying Windows, please share your experience, no matter it is successful case or not. Here are some pointers to get started.

* Windows 10 users can check out [https://www.windowscentral.com/how-install-bash-shell-command-line-windows-10](https://www.windowscentral.com/how-install-bash-shell-command-line-windows-10)  . The system has native support but in beta stage. 
* Users of other versions can checkout  [https://www.cygwin.com/](https://www.cygwin.com/)  . Cygwin is a classical project to emulate Linux environment on Windows. It should still work on most versions. 
* Some students who learned Python before told me the Python installer on Windows is shipped with a shell by default. You may try this route.
* [http://gitforwindows.org/](http://gitforwindows.org/)  Git for Windows ships with a shell by default. You can key in most Linux-like commands there.
* [https://pythonhosted.org/spyder/](https://pythonhosted.org/spyder/)   and  [https://conda.io/docs/user-guide/install/windows.html](https://conda.io/docs/user-guide/install/windows.html)  . Those are two integrated Python environments. It saves time installing dependencies.
* Another shell like environment you can try on Windows: [https://github.com/bmatzelle/gow/wiki](https://github.com/bmatzelle/gow/wiki) . GOW is the rising star alternative to Cygwin 



## Other integrated environments

* Anaconda: https://conda.io/docs/user-guide/install/download.html
* Spyder: https://pythonhosted.org/spyder/installation.html


