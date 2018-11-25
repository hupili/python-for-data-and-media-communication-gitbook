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

## Check column type and convert column type to numeric

A very typical example when performing numeric compuations in pands, e.g. calculating correlation:

```python
df['Price'].corr(df['Num of equipment'])
```

One may encounter the following error:

```text
     76     if isinstance(ret, mu.ndarray):
     77         ret = um.true_divide(
---> 78                 ret, rcount, out=ret, casting='unsafe', subok=False)
     79         if is_float16_result and out is None:
     80             ret = arr.dtype.type(ret)

TypeError: unsupported operand type(s) for /: 'str' and 'int'
```

This hints that the data type is incorrect. We can check the type as follows:

```python
df_sort['Price'].dtype
# dtype('O')
```

Convert the column to numeric in following way:

```python
df_sort['p'] = pd.to_numeric(df_sort['Price'])
df_sort['p'].dtype
# dtype('int64')
```

The `dtype('int64')` means that this columns is good for numeric computation now.
