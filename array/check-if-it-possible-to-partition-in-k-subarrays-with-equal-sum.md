Given an array A of size N, and a number K. Task is to find out if it is possible to partition the array A into K contiguous subarrays such that the sum of elements within each of these subarrays is the same.

Prerequisite : Count the number of ways to divide an array into three contiguous parts having equal sum

Examples :
```python
Input : arr[] = { 1, 4, 2, 3, 5 } K = 3
Output : Yes
Explanation :
Three possible partitions which have equal sum : 
(1 + 4), (2 + 3) and (5)

Input : arr[] = { 1, 1, 2, 2 } K = 2
Output : No
```
Approach :
Can be solved by using Prefix Sums. Firstly, note that total sum of all elements in the array should be divisible by K to create K partitions each having equal sum. If it is divisible then, check each partition have an equal sum by doing :
1. For a particular K, each subarray should have a required sum = total_sum / K.

2. Starting from the 0th index, start comparing prefix sum, as soon as
it is equal to the sum, it implies the end of one subarray (let’s say at index j).

3. From (j + 1)th index, find another suitable i whose sum (prefix_sum[i] –
prefix_sum[j]) gets equal to the required sum. And the process goes until
required number of contiguous subarrays i.e. K is found.

4. If at any index, any subarray sum becomes greater than required sum, break out
from loop since each subarray should contain that an equal sum.

Solution(In python):
```python
def splitInto(arr,n):
    subArraySum = sum(arr[:n])
    if(len(arr) % 2 == 0):
        for i in range(n, len(arr), n):
            if (arr[i] + arr[i + 1] != subArraySum):
                return False
    else:
        for i in range(n, len(arr), n):
            if (i  == (len(arr) - 1)):
                if (arr[i] != subArraySum):
                    return False
            else:
                if (arr[i] + arr[i + 1] != subArraySum):
                    return False


if(splitInto([0,0,-1,1,5,-5],2) == False):
    print('Test failed')
else:
    print('Test passed')

```
