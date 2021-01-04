
Author: @misterrpink1 /rikehsthapa \
title: Divide And Conquer~ Counting Inversions \
Sources: Coursera "Divide and Conquer, Sorting and Searching" Stanford Course \

### Strassen's Recursive Matrix Multiplication

### THE HIGH LEVEL

 - How do we multiply two matrices x and y where:
     - all matrices are n X n dimensions
     - so input size is O(n^2)

### PROBLEM

#### Example:
    -- -- -- --        --          --
    |a b| |e f|   >>\  | ae+bg af+bh |
    |c d| |g h|   >>/  | ce+dg cf+dh |
    -- -- -- --        --          --


### MY TAKE
> This section is my personal attempt at thinking through the problem. I will leave my solution even if I end up being wrong. \
> Selfishly, this will allow me to revisit my mental checkpoints in the future. \
> After all revisiting a difficult past problem is the true way to ensure mastry. 
> ** For you **, however, this is also beneficial. You will be able to see my mental roadblocks. \
> One of the reasons I am posting my review, learnings, coding processes, etc is to allow anyone to see the trye guts to mastry <If I ever reach such a status> \
> :pill::basketball::pill::hammer:

- What would the brute force solution be?

~~~
def brutish_martix_multiplication(matrixA, matrixB):
    resuntant = [][] #initialize an nxn matrix
    for i in (0, n):
        for j in (0, n):
            resultant[i][j] = matrixA[i]*matrixB[i] + matrixA[j
~~~

If you think about it, matrix multiplication function involves the following steps:
- compute all products of subi  X subj. --> nXn
- sum all the products together. --> Xn
resulting in O(n^3)

## :heavy_check_mark: Solution: 
- How do we improve on O(n^3) 


#### Implementation:

## :mag: Solution

### Analysis
