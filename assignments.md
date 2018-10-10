# Assignments

Following are the **individual** assignments. You are welcome to discuss and work in groups. In the end, everyone should do the assignment and submit an original version from oneself. Make reference where needed, if you used other's solution.

## Way to hand in assignments

- Create a repo called `python-data-assignments`. (Please copy and paste to ensure the exact repo name, or we may not find your assignment)
- Create one folder for each assignment, with names `assignment0`, `assignment1` and `assignment2`.
- Put all the relevant files, including codes, docs and data (where applicable) into the per assignment folder. Refer to [notes-week-00.md](notes-week-00.md) for GitHub operations.

**Note**: You need to ensure the work is on GitHub before the deadline. Although we don't grade immediately after submission close, we can always check back the status at that time from version history.

## Assignment 0 -- Bridging assignment for language efficiency

Deadline: **Oct 24, 2018 (Wed)**

There are several news articles in the [assets/assignment0](assets/assignment0) folder. Please make a simple keyword frequency analyzer script called `keywords.py`. Once we run `python3 keywords.py`, your script works as follows:

- Read all the `.txt` files in folder `assignment0/`. (consider `open().read()`; You can use a `list` to store the relative paths of the files first)
- For every file, extract the English words from the file content. (consider `str.split()`)
- For every word extracted above, count how many times each one appears. (consider to use `dict`; keys are keywords; values are word count)
- Rank the keywords from higher frequency to lower frequency. Only `print` the top 15 keywords on Terminal. (consider `sorted()` and list slicing)
- Output the full keyword frequency list into a CSV file. The table headers are `keyword,frequency`. (consider to use `csv`)

### Bonus: Handle the stop words

Your first result may contain a lot "stop words" -- the words that do not carry much meaning in our context. For example, "a" and "the" appear quite frequently in English but they do not give much information about the content. Having those high-frequency words in our list is a distraction for further analysis. We can remove those stop words.

Suppose you are given the stop words list:

`stop_words = ["the", "and", "of", "a", "in"]`

Here are the questions:

1. Can you remove the stop words from above Terminal output, as well as the CSV file?
2. Can you further enrich this `stop_words` list to make the output more meaningful?

## Bonus: Discussion or demo

To address following questions, you can choose to simply discuss the solution in your `README.md` file or give a working demo using codes:

- If you spotted one interesting keyword from the top list, how do you locate this keyword in articles? i.e. Find which article and which paragraph contains the keyword.
- Can you further organise your code for future reuse? One example of reusable piece is the keyword extraction from one string. Another example is the keyword extraction from one file. You can consider to put those in functions.
- There are two ways to approach the above problem: 1) assemble the content of all 5 files and extract keyword list for one string; 2) extract keyword-frequency list for all 5 files first and then merge the keyword-frequency (may need to sum the count for the same keyword). Which did you use? Which way is better? And Why?

## Assignment 1 -- Data collection

## Assignment 2 -- Data analysis, visualisation and presentation


## Notes on Bonus Question

Note: Solution to bonus questions will not contribute to regular grade and will not affect class wise curving. They will be used in the end as tie breaker or promote significant outperformers to next level of letter grade. In other words, working on bonus questions will not harm other's grade. It may help some continuous outperformers to gain one more layer of security, just in case they have bad luck with project or quiz. You are encouraged to take more bonus if you can.