# Pandas

<!-- TOC -->

- [Pandas](#pandas)
  - [Rename csv header](#rename-csv-header)
  - [Wordcloud](#wordcloud)
  - [Check column type and convert column type to numeric](#check-column-type-and-convert-column-type-to-numeric)
  - [Shortcut to select a range from pandas.DataFrame](#shortcut-to-select-a-range-from-pandasdataframe)
  - [Convert pandas.DataFrame to dict presentation](#convert-pandasdataframe-to-dict-presentation)
  - [Use .loc to batch assignment](#use-loc-to-batch-assignment)
  - [Turn a long format table into wide format (unpivot)](#turn-a-long-format-table-into-wide-format-unpivot)

<!-- /TOC -->

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

## Shortcut to select a range from pandas.DataFrame

Normally, you can do the following:

```python
df[
     (df[column] > min_value)
     &
     (df[column] < max_value)
]
```

A simpler version using `Series.between` is:

```python
df[
     df[column].between(min_value, max_value)
]
```

## Convert pandas.DataFrame to dict presentation

* list-of-dict representation: `DataFrame.to_dict('records')`
* dict-of-series representation: `DataFrame.to_dict()`

## Use .loc to batch assignment

Sometimes, we need to perform batch assignment from one data frame to another. The batch assignment involves multiple rows and columns. `DataFrame.loc` comes handy in retrieving (writable) multi-row and multi-column subset of the original data frame. However, note the following caveats:

Suppose `row` and `column1`/ `column2` are both single string, following code updates the new data:

```
df1.loc[row, column1] = df2.loc[row, column2]
```

However, following one does not work:

```
df1.loc[row, [column1]] = df2.loc[row, [column2]]
```

The latter one will try to match column names. If `column1` and `column2` are different, the update fails and **no error is raised**. The behaviour for pandas to update DataFrame is to match columns and then update.

## Turn a long format table into wide format (unpivot)

`.melt()` is the "unpivot" operation.

In simpler applications, `.stack()` could come handy. It turns the data frame into the "record" format, where records are indexed by composite index of `(original indexes, original columns)`.

