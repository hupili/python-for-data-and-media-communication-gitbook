# Assignments

Following are the **individual** assignments. You are welcome to discuss and work in groups. In the end, everyone should do the assignment and submit an original version from oneself. Make reference where needed, if you used other's solution.

## Way to hand in assignments

- Create an repo called `python-data-assignments`. (Pleas copy and paste to ensure the exact repo name; or we may not find your assignment)
- Create one folder for each assignment, with names `assignment0`, `assignment1` and `assignment2`.
- Put all the relevant files, including codes, docs and data (where applicable) into the per assignment folder. Refer to [notes-week-00.md](notes-week-00.md) for GitHub operations.

**Note**: You need to ensure the work is on GitHub before the deadline. Although we don't grade immediately after submission close, we can always check back the status at that time from version history.

## Assignment 0 -- Bridging assignment for language efficiency

Deadline: **Oct 24, 2018 (Wed)**

There are several news articles in the [assets/assignment0](assets/assignment0) folder. Please make a simple keyword frequency analyzer script called `keywords.py`. Once we run `python3 keywords.py`, your script works as follows:

- Read all the `.txt` files in folder `assignment0/`. (consider `open()`)
- For every file, extract the English words from the file content. (consider `str.split()`)
- For every word extracted above, count how many times each one appears. (consider to use `dict`; keys are keywords; values are word count)
- Rank the keywords from higher frequency to lower frequency. Only `print` the top 15 keywords on Terminal. (consider `sorted()` and list slicing)
- Output the full keyword frequency list into a CSV file. The table headers are `keyword,frequency`. (consider to use `csv`)

### Bonus: Handle the stop words

Your first result may containt a lot "stop words" -- the words that do not carry much meaning in our context. For example, "a" and "the" appear quite frequently in English but they do not give much information about the content. Having those high frequency words in our list is a distraction for further analysis. We can remove those stop words.

Suppose you are given the stop words list:

`stop_words = ["the", "and", "of", "a", "in"]`

Here are the questions:

1. Can you remove the stop words from above Terminal output, as well as the CSV file?
2. Can you further enrish this `stop_words` list to make the output more meaningful?

## Assignment 1 -- Data collection

## Assignment 2 -- Data analysis, visualisation and presentation

