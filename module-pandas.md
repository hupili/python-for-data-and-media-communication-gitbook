# Pandas

## Rename csv header

We can use `rename` function to change the header.

For example, I want to change column A to B, column C to D.

Syntax:

```python
df.rename(columns={'A':'B','C':'D'}, inplace=True)
```

For more explanation, you can refer [here](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.rename.html)

## Wordcloud

When you did word-clouds project in python, you may see the key error as below:

command'/usr/bin/clang' failed with exit status 1

You can add one line of code showed here `xcode-select --install`, then you can solve the problem.
