
Author: @misterrpink1 /rikehsthapa \
title: Divide And Conquer~ Counting Inversions \
Sources: Coursera "Divide and Conquer, Sorting and Searching" Stanford Course \


#### Contents
##### 1) counting number of inversions in an array

### Overview

1) Counting the number of inversions in an array:

- lets tackle using divide and conquer
- STEP1: conceptually/ literally DIVIDE the problem into subproblems
- STEP2: CONQUER usign recursive calls
naturally this is easier said than done
- STEP3: COMBINE solutions of subproblems into one for the original problem

## PROBLEM
Input: array A containing the numbers 1, 2, ... n in some arbitrary order
OUPUT: number of inversions in the array 
WHERE: inversions = numnber of pairs (i, j) of array indices with i < j and A[i] > A[j]

## :heavy_check_mark: Personal Thoughts:
I think we can use Merge Sort modified in order to solve this:
Seeing as a merge where right half (j) is smaller than left hald (i) there fore i < j and A[i] > A[j] 
<Note I am committing this change as my "Skin to the game" attempt at thinking through the problem before blindly seeing the solution>

> Why bother with inversion count after all? \
> inversion count can be used as a similarity measure on ranked lists. \
> For example: collaborative filtering. Being able to recommend similar purchases to you. \
> :bread: :doughnut: :watermelon:

## :heavy_check_mark: Solution: 
What is the largest number of inversions that a 6-element array can have?
- nC2 = n(n-1)/2 = 15

## :clap: Clapping myself on the back here as I got this correct conceptually
#### Implementation:

Since I am rusty on the old scripting machine (I think :thinking:) \
no harm in practicing implementation of this.
~~~
lets start with pseudo code:
def inversionCount(arr):
    if(len(arr) <= 2):
        if( left(arr) > right(arr)):
            return [ right(arr) , left(arr) ], 1  # the 1 represents count += 1
    left, leftCount = inversionCount(left(arr))
    right, rightCount = inversionCount(right(arr))
    sortedArray, totalCount = merge(left, right, count)

def merge(left, right, count):
    mergedArr = []
    for i in range (0, len(left)):
        for j in range (0, len(right)):
            if left(i) > right(j):
                count++
                j++
                mergedArr.push(right(j))
            else:
                mergedArr.push(left(i))
                i++
    return mergedArr, count
~~~

## :mag: Solution

~~~

count(array A, length n):
    # Base Case
    if: n=1 return 0
    else:
        x = count( array A[1st half], n/2)
        y = count( array A[2nd half], n/2)
        z = countSplitInv(A, n)
    return x + y + z
    
    # If we implement this correctly we should be able to get linear (o(n)) time.

~~~

> When you merge two of the sub arrays using merge sort Merge function, we are essentially calling it to count inversions every time we rearrange right and left vs left first then right. \
> When you copy over an element from the right array to left array, we have an inversion

### Analysis
- Merge Step passes through all elements in the array once: so O(n)
- InversionCount: Also does one pass through n elements: O(n)
- O(n) + O(n) = O(n)
- Sort and count recursion : O(nlog(n))
- Same as Merge Sort
