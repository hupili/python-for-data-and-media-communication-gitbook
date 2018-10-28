# Leetcode

<!-- TOC -->

- [Leetcode](#leetcode)
    - [Getting started](#getting-started)
    - [Control flow](#control-flow)
    - [List](#list)
    - [String](#string)
    - [Set](#set)
    - [Algorithms](#algorithms)
        - [Problem comprehension and simulation](#problem-comprehension-and-simulation)
        - [Cummulative summation](#cummulative-summation)
        - [Search, recursion, backtacking](#search-recursion-backtacking)
        - [Dynamic programming](#dynamic-programming)

<!-- /TOC -->

Leetcode is a programming training website specially designed for Internet companies. The target audience is generally computer science background students. The problems on leetcode may involve some advanced data structure (more than `list`, `dict` stuffs you learn here) and advanced algorithms. A common heuristic is that, once you can finish first 200 random leedcode, you have very good chance to get into tier one Internet companies in the world. We do not require our students to be as proficient as that. However, this is the place to get you started with "computational thinking". We curate the following list with annotations for those curious minds. You can use the following list to test your basic Python knowledge.

Most of the those problems below are labelled "Easy" on leetcode. We re-estimate their difficulty using 5-stars taking our student background into consideration. The 1-star and 2-star problems are meant to be tractable by an average students from the class. The 3-star and 4-star problem require extra efforts but within your reach most of the time. You are suggested to strike to 4-star problems in order to gain good efficiency. That helps in the long run, if you want to pursue a data analyst career after graduation. 5-star problems touch the surface of "algorithm design". It is an advanced topic that even some computer science students do not feel comfortable with. You are **strongly** suggested to find a mentor who can give you some general directions before you start, or it is highly like to be a waste of time (no meaninful results after hours/ days)...

## Getting started

We use [reverse-string](https://leetcode.com/problems/reverse-string/) as an example to get you started:

```python
class Solution:
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        return s[::-1]
```

You can win points by copy and pasting the above one-line solution to the input text box (select `Python3` as the language). As a matter of ethics, do not direclty copy and paste other's code in the future. Try to comprehend the solution and make your own. We use this example to help you quickly get an idea of what is an Online Juedge (OJ) and how it works. Leetcode problems follow the same format. There is a class called `Solution` and an entry point method/ function, in this case `reverseString`, to be called when the OJ evaluates your code. Your task is to fill in the body of this function. The function takes input data from argument list and gives answer using the `return` statement. You can use "Run Code" button and "Customise Testcase" to try different input values. Once you "Submit", the OJ will test different input dataset with your method and give evaluation results. Once you see "Accepted", you are successful.

## Control flow

- ★★☆☆☆ [lemonade-change](https://leetcode.com/problems/lemonade-change/) - involves `for`, `if` and variables. A very realistic problem in our life. Good to exercise logical thinking.

## List

- ★★★☆☆ [rotate-array](https://leetcode.com/problems/rotate-array/) - basic solution involves list slicing. Need to take care when `k` is larger than the list length. There are many alternative solutions that may require some logical thinking.
- ★★★★☆ [pascals-triangle](https://leetcode.com/problems/pascals-triangle/) - Exercise the list-of-list structure. Try to find the pattern between each two rows.

## String

- ★★★★☆ [license-key-formatting](https://leetcode.com/problems/license-key-formatting/) - involves `str` functions, integer division's quotient and remainder. Requires a bit sense of math.

## Set

- ★★★☆☆ [unique-email-addresses](https://leetcode.com/problems/unique-email-addresses/) - mainly str processing. Use `set()` to efficiently deduplicate and count. This question is also good for people to learn the alternative email address you can use, by adding `.` and `+`. You can try one alternative address with your friend.

## Algorithms

Algorithm problems are usually integrated practice of all the above. We do not label the Python basics involved in the problems anymore.

### Problem comprehension and simulation

Those problems are "straightforward" in the view of algorithm engineers. They do not involve much algorithmic ideas. Once you fully understand the problem, you can use computer program to simulate the process as described by the problem. The simulation will get you the answer directly.

- ★★★★★ [degree-of-an-array](https://leetcode.com/problems/degree-of-an-array) - requires good problem comprehension and problem conversion. Design staged solution once you can re-interpret the problem as: _among the most common numbers, find the one whose minimum index and maximum index are closest_.
- ★★★★★ [long-pressed-name](https://leetcode.com/problems/long-pressed-name) - a very practical problem. First think how you compare two strings and then adapt the basic algorithm to this problem. Watch out for corner cases (boundary conditions).

### Cummulative summation

Cummulative summation (cumsum) is a common technique to save computation on a sequence of elements. Suppose we have a list of numbers in `A`. Let's denote cumsum of `A` as `C`, where `C[i] = sum(A[: i])`. After this pre processing, a range sum query can be answered by `sum(A[i: j]) = C[j - 1] - C[i - 1]`. The LHS (original sum) involves summation over a series of elements. The RHS (cumsum) involves only **a single subtraction**, thus more efficient.

- ★★★★★★ [flip-string-to-monotone-increasing](https://leetcode.com/problems/flip-string-to-monotone-increasing) -- The key step is to find an index `i` such that `S[: i]` will be flipped into `0` and `S[i: ]` will be flipped into `1`. To efficiently compute how many flips are needed, we need to get cumsum of: 1) number of 1's on the left and 2) number of 0's on the right.

### Search, recursion, backtacking

Search problem usually involves exponential problem space. For example, playing Go is a search problem in essence. Every step, there are up to 400 potential moves. If you consider `n` steps, the space is exponentially large -- `400 ** n`.

The method to explore such large space is called recursion/ backtracking. The implementation usually looks like some function calling itself with different parmeters. When recursion/ backtracking hits boundary condition, simple and straight solution exists (e.g. when problem size is 0 or 1).

```python
def search_n_step(n):
    if n == 0:
        return a_simple_solution
    solution_to_sub_problem = search_n_step(n - 1)
    solution = integrate_current_step_into_sub_problem(step, solution_to_sub_problem)
    return solution
```

### Dynamic programming

Dynamic Programming (DP) is closely related with search problem. DP problem seems to be solvable by search at first glance. However, due to the large search space, the naive algorithm is not efficient enough. DP utilizes the problem structure, that *state could be memoryless* -- that is:

- how we reach this state is not important
- our future optimal decision is purely based on the current state

The concept is abstract, and can be explained via following exercises:

- ★★★★★★ [minimum-falling-path-sum](https://leetcode.com/problems/minimum-falling-path-sum/) -- We can handle the matrix row by row. For `A[i][j]`, `F[i][j] = min(F[i - 1][j - 1], F[i - 1][j], f[i - 1][j + 1])`. We calculate all `F` by increasing `i`, i.e. row by row. How we reach the minimum at `i-1`th row is not important. The only thing that matters is what is the value at `F[i - 1][:]`.
