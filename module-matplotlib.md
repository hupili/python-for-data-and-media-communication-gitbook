# matplotlib

## Troubleshooting Chinese characters on MAC

[This noteboko](https://github.com/hupili/python-for-data-and-media-communication/blob/master/matplotlib-examples/Chinese%20Font.ipynb) gives detailed steps in troubleshooting the Chinese characters on MAC. You will learn:

- Where are the fonts stored on your system
- How to filter out the font files that include CJK characters
- How to load a font file into matplotlib. Note that `ttc` does not work for some version of matplotlib. `ttf` works.

## How to display Chinese characters when using matplotlib

Step 1: Download the SimHei font [here](https://www.fontpalace.com/font-details/SimHei/)

Step 2: Find font folder in `mpl-data` folder

```python
import matplotlib
print(matplotlib.matplotlib_fname())
#/Users/xuyucan/Desktop/Chicoxyc/venv/lib/python3.6/site-packages/matplotlib/mpl-data/matplotlibrc

!open /Users/xuyucan/Desktop/Chicoxyc/venv/lib/python3.6/site-packages/matplotlib/mpl-data
```

Step 3: Enter the font folder, put the font you just download into the folder,then click to install

![font folder](assets/matplotlib-font-folder.png)

Step 4: Back to `mpl-data` folder, click `matplotlibrc`
`command+f` search font family, delete `#`;
search font.sans-serif,delete `#`, and add `SimHei,`;
search axes.unicode_minus, replace `True` to `False`.

![Matplotlib add font](assets/matplotlib-add-font.png)

Step 5: Delete the cache

```python
import matplotlib as mpl
mpl.get_cachedir() #dind the path of cache
!open /Users/xuyucan/.matplotlib
#delete files in this folder
```

Step 6: Restart the Jupyter notebook

1. `comman+c` in terminal, enter `y`
2. type `jupyter notebook` again

Step 7: add following two lines into your codes

```python
plt.rcParams['font.sans-serif']=['SimHei'] #用来正常显示中文标签
plt.rcParams['axes.unicode_minus']=False #用来正常显示负号
```

## Display Chinese characters when plotting tag cloud

```python
wc = wordcloud.WordCloud(background_color="white",font_path='/Library/Fonts/Songti.ttc', max_words=3000,max_font_size=60, random_state=40)
```

When generate tag cloud, we need give a `font path`  which support Chinese characters.

Usually we use `SimHei` and `Songti` to display Chinese characters. There are two ways to get the font path.

1. `command + blank` to open spotlight, search `font book`,select one font that support support Chinese characters. The font path will be like this: `/Library/Fonts/Songti.ttc` or `/Library/Fonts/SimHei.ttf`.

2. If there is no font that can support Chinese character, you need to download the font, and install, then get the font path by step 1. Or you can put the font in the current folder where your jupyter notebook are. The font path will be like this `"./simhei.ttf"`.
