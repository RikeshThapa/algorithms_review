
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
- Idea:
    > if:
    - take a large nxn matrix
    - nxn matrix A can be divided into 4 quadrants A,B,C,D 
    - nxn matrix B can be divided into 4 quadrants E,F,G,H
    > then:
    - x*y = --                 --
            | AE + BG , AF + BH |
            | CE + DG , CF + DH |
            --                 --
    - this is the Atomic Property of matrix dot products
    - note: if you were to look at KaratSuba's divide and conquer algo, you may notice some similarities in how the following is calculated:
 - Solution 1:
    - Recursive algorithms 1:
         - step 1: involves 8 different products: AE, BG, AF, BH, CE, DG, CF, DH
         - step 2: sum AE+BG, AF+BH, CE+DG, CF+DH
         - O(n^3) time; although not obvious still cubic
         
    - Recursive Algorithm 2: Strassen's Subcubic Matrix:
         - Similar to Karatsuba using Gausses's trick
         - Somehow we are able to only do 7 calculations
         - Step 1: recursively compute 7 products using cleer pics
         - Step 2: Do the necessary additions
         - reult: O(n^2)    


#### Implementation:
    To be clear, the concept is a little weird so lets work through the theroreticals and then figure out how Strassen's solution works
    - p1 = A(F-H)
    - p2 = (A+B)H
    - p3 = (C+D)E
    - p4 = A(G-E)
    - p5 = (A+D)(E+H)
    - p6 = (B-D)(G+H)
    - p7 = (A-C)(E+F)
                   --                --        --                                     --
    Claim: x * y = | AE + BG  AF + BH |    =  | P5 + P4 - P2 + P6         P1 + P2      |
                   | CE + DG  CF + DH |       |      P3 + P4         P1 + P5 - P3 - P7 |
                   --                --        --                                     --
                   
    - well thats it. 
    - The proof is to calculate the procicts and prove that they equate. This is trivial so I will not be doing it.
    - Also anti climactic, there is no explanation of how Strassen cam up with this solution. Pure intuition I guess.
## :mag: Solution

### Analysis
