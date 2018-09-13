# Rod cutting problem

Dynamic Programming Approach (The Bottom Up strategy which eliminates recursion)
- No memoization
- Time complexity - O(n<sup>2</sup>)

```python

# A Naive recursive solution
# for Rod cutting problem 
import sys


# A utility function to get the
# maximum of two integers 
def max(a, b):
    return a if (a > b) else b


# Returns the best obtainable price for a rod of length n
# and price[] as prices of different pieces 
def cutRod(price, n):
    val = [0 for x in range(n + 1)]
    val[0] = 0
    max_val = -sys.maxsize - 1

    # Recursively cut the rod in different pieces   
    # and compare different configurations 
    for i in range(1, n + 1):
        print('i',i)
        for j in range(0,i):
            max_val = max(max_val, price[j] +
                          val[i-j-1])
            val[i] = max_val

    print('val',val)
    return val[n]


# Driver code
arr = [1, 6, 8, 11]
size = len(arr)
print("Maximum Obtainable Value is", cutRod(arr, size))

```
