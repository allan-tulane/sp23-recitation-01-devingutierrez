# CMPS 2200  Recitation 01

**Name (Team Member 1):** Devin Gutierrez ______________  
**Name (Team Member 2):**Griffin Olimpio________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

The worst case input value for key of linear_search would be
an integer that is contained at the final index of the list (n-1). This would cause the function to iterate through and search the entire rest of the list before finding the correct value at the last index. The worst case runtime would be O(n). 

The worst case input value for key of binary_search would also be an integer that is at index 0 or index n-1 (at the very beginning or very end of the list). This would cause the function to search and split the list until the list is equal to one, making the maximum number of comparisons before finding the search value. The worst case runtime would be O(log n).

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**
The best case input value of `key` for `linear_search` would be the first element of the list. If this is the case,the function does not need to loop and finishes after searching the first index.
The best case input value of `key` for `binary_search` would be the middle element of the list. In this case, no resursion is needed as the function checks the middle element in the base case.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**
|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.004 |    0.005 |
|      100 |    0.011 |    0.005 |
|     1000 |    0.104 |    0.009 |
|    10000 |    1.084 |    0.020 |
|   100000 |   43.619 |    0.030 |
|  1000000 |  202.132 |    0.046 |
| 10000000 | 2007.977 |    0.041 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**

Yes, these worst-case running times match our compare_search results. You can see as n increases, that the binary search becomes much faster relative to the linear search. When n is smaller, such as n=10, the linear search and binary search runtimes are comparable. However, as n reaches infinity, the linear search time before exponentially larger than binary search.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**
      + The worst-case complexity of searching a list of $n$ elements $k$ times using linear search is O(kn).
    
  + For binary search? **TODO: your answer goes here**
      + The worst-case complexity of searching a list of $n$ elements $k$ times using binary search is O(klog_2(n)).
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**

k*n is the runtime of using linear search without sorting. klog(base 2)*n + n^2 is the runtime of using binary search after sorting the list. It is more efficient to first sort and then use binary search when: k * n > k * log(base2) + n^2. 

Simplifying this would yield log(base2)*n < k/(log(base2) * n), therefore the crossover value in terms of n when binary search and sorting would become more time efficient would be: k = log(base2) * n + log(base2)
