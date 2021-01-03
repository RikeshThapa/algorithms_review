

Author: @misterrpink1 /rikehsthapa
title: Divide And Conquer
Sources: Coursera "Divide and Conquer, Sorting and Searching" Stanford Course

#### Contents
##### 1) counting number of inversions in an array
##### 2) Strassen's recursive algorithm for matrix multiplication
##### 3) computing the closest pair of points in the plane
##### 4) The Master method

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

## Solution: 
What is the largest number of inversions that a 6-element array can have?
- nC2 = n(n-1)/2 = 15

## :clap: Clapping myself on the back here as I got this correct conceptyally
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

### Attempted Implementation
~~~

def countInversions( arr ):
    count = 0
    if(len(arr) == 1):
        return count
    else:
        merge(arr)

def merge(arr1, arr2):
    count = 0
    mergedArr = []
    for (i = 0; i < max(len(arr1),len(arr2)); i++):
        if arr1[i] < i :
            count += 1
            mergedArr.push(j).push(i)
        else:
            mergedArr.push(i).push(j)
                
                
        

~~~

