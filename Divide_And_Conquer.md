

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

PROBLEM
Input: array A containing the numbers 1, 2, ... n in some arbitrary order
OUPUT: number of inversions in the array 
WHERE: inversions = numnber of pairs (i, j) of array indices with i < j and A[i] > A[j]

I think we can use Merge Sort modified in order to solve this:
Seeing as a merge where right half (j) is smaller than left hald (i) there fore i < j and A[i] > A[j] 
<Note I am committing this change as my "Skin to the game" attempt at thinking through the problem before blindly seeing the solytion>


