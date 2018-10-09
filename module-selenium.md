# Selenium

Selenium module can be used in dynamic page web scraping on Windows Systems. It supports Firefox, IE, Chrome and Remote.

## Basic steps

### Step 1 install selenium

pip install selenium

### Step 2 install webdriver and put it in the project's working directory

For example, I use Chrome, so I need download a ChromeDriver. Download link：
https://sites.google.com/a/chromium.org/chromedriver/home

### Step 3 start from opening a dynamic page web url

```python
browser = webdriver.Chrome()
browser.get('http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war')
time.sleep(10)
```

For detailed use, refer to the Selenium documentation:
https://selenium-python-zh.readthedocs.io/en/latest/index.html

For more selenium examples, you can refer [here](https://github.com/hupili/python-for-data-and-media-communication/tree/master/scraper-selenium).

## Chrome driver not found in path error

This is common error. You can download [Chrome Driver](https://sites.google.com/a/chromium.org/chromedriver/home) and put it in your [Current Working Folder](shell.md#verify-your-current-working-folder). Note, for venv and jupyter user, this is not your project root folder, or the venv folder. It is the path at which you issued the `jupyter notebook` command -- a.k.a. "current working folder".

MAC user has a shortcut to install chromedriver in the path.

```shell
brew cask install chromedriver
```
