# Wordcloud

## Display Chinese characters when plotting tag cloud

```python
wc = wordcloud.WordCloud(background_color="white",font_path='/Library/Fonts/Songti.ttc', max_words=3000,max_font_size=60, random_state=40)
```

When generate tag cloud, we need give a `font path`  which support Chinese characters.

Usually we use `SimHei` and `Songti` to display Chinese characters. There are two ways to get the font path.

1. `command + blank` to open spotlight, search `font book`,select one font that support support Chinese characters. The font path will be like this: `/Library/Fonts/Songti.ttc` or `/Library/Fonts/SimHei.ttf`.

2. If there is no font that can support Chinese character, you need to download the font, and install, then get the font path by step 1. Or you can put the font in the current folder where your jupyter notebook are. The font path will be like this `"./simhei.ttf"`.
