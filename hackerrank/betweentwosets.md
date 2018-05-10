## Between Two Sets

Problem Link - https://www.hackerrank.com/challenges/between-two-sets/problem

You will be given two arrays of integers. You will be asked to determine all integers that satisfy the following two conditions:

The elements of the first array are all factors of the integer being considered
The integer being considered is a factor of all elements of the second array
These numbers are referred to as being between the two arrays. You must determine how many such numbers exist.

Input Format

The first line contains two space-separated integers describing the respective values of , the number of elements in array , and , the number of elements in array . 
The second line contains  distinct space-separated integers describing . 
The third line contains  distinct space-separated integers describing .

Constraints

Output Format

Print the number of integers that are considered to be between  and .

Sample Input

2 3
2 4
16 32 96
Sample Output

3
Explanation

2 and 4 divide evenly into 4, 8, 12 and 16. 
4, 8 and 16 divide evenly into 16, 32, 96.

4, 8 and 16 are the only three numbers for which each element of A is a factor and each is a factor of all elements of B.

### Solution:
Language - Python

```python
def getTotalX(a, b):
    #
    # Write your code here.
    #
    global factorsOfA
    factorsOfA = []
    for i in range(0,len(a)):
        # print('I', i, a[i])
        for j in range(0,len(a)):
            # print('J', j)
            factorsOfA.append(a[i]*a[j])
    global finalFactorsToCompare
    finalFactorsToCompare = list(set(factorsOfA))

    # Time to iterate into second array
    global factorsOfB
    factorsOfB = []
    for i in range(0, len(b)):
        for j in range(0, len(finalFactorsToCompare)):
            if b[i] % finalFactorsToCompare[j] == 0:
                factorsOfB.append(finalFactorsToCompare[j])

    finalFactors = list(set(factorsOfB))

    print(len(finalFactors))


getTotalX([2,4],[16,32,96])
```
