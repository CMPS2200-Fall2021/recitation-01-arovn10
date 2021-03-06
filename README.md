# CMPS 2200  Recitation 01

**Name (Team Member 1):**Alec Rovner


In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Login to Github.
- Click on the assignment link sent through canvas and accept the assignment.
- Click on your personal github repository for the assignment (e.g., https://github.com/tulane-cmps2200/recitation-01-your_username).
- [Clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository) the repository to your local device
- Complete the lab task 
- [Add, commit, and push](https://docs.github.com/en/github/managing-files-in-a-repository/managing-files-using-the-command-line/adding-a-file-to-a-repository-using-the-command-line) your completed lab back up to GitHub. 
  - You will need to issue `git add` for all files that you have modified, e.g., `main.py`, `README.md`, and any others that you modify as well.
  - For example, on the command line, in the same directory as your cloned lab:
```
$ git add main.py
$ git commit -m "Implement Required Functions"
$ git push origin main
```

You'll work with a partner to complete this recitation. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.

## Turning in your work
- Only one team member needs to push your completed lab to github. 
- In the README.md file, include the name of the team members.


## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 
   1. The worst case input value for linear search is when the key is either at the end of the list or not in the list at all. This gives us the worst case time complexity of O(n)
   2. The worst case input value for binary search is when the key is at the very end of the list and it is narrowed to a single item or not in the list at all. This gives us he worst case time  complexity of  O(logn)



5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 
   1. Linear Search: The key element has to be the first element in the list for the best case. This achieves O(1)
   2. Binary Search: The key element has to be the middle index for the best case input value. This will give us a time complexity of O(1)




- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.002 |    0.003 |
|      100 |    0.005 |    0.003 |
|     1000 |    0.053 |    0.006 |
|    10000 |    0.562 |    0.006 |
|   100000 |    5.328 |    0.018 |
|  1000000 |   67.534 |    0.063 |
| 10000000 |  479.245 |    0.024 |



9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

     2. The worst-case running time for linear search proves true as the O(n) runtime is not exceeded with all sample sizes
     3. The worst-case running time for binary search proves true as well because the worst case runtime does not exceed O(log2(n))
     4. These theoretical runtimes do abide to my results found


10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
    + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**
      + The worst case time complexity is O(n) * k as it searches each element in the list once, it does not need to be sorted
    + For binary search? **TODO: your answer goes here**
      + For binary search, the worst case involves sorting the list and then using binary search and because sorting takes O(n^2)  and the worst case for binary is O(log2(n)), the worst case is O(log2(n)) * k + O(n^2)
    + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting?
      + O(log2(n)) * k + O(n^2) < O(n) * k is the inequality to solve in order to get the values of k in which it is more efficient to first sort then use binary search. Through solving this inequality, we find that for all values where k > (n^2/(n-log2(n))), it is more efficient. 
