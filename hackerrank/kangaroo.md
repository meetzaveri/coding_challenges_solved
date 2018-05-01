

## Problem Set - Kangaroo


You are choreograhing a circus show with various animals. For one act, you are given two kangaroos on a number line ready to jump in the positive direction (i.e, toward positive infinity).

The first kangaroo starts at location  and moves at a rate of  meters per jump.
The second kangaroo starts at location  and moves at a rate of  meters per jump.
You have to figure out a way to get both kangaroos at the same location as part of the show.

Complete the function kangaroo which takes starting location and speed of both kangaroos as input, and return  or appropriately. Can you determine if the kangaroos will ever land at the same location at the same time? The two kangaroos must land at the same location after making the same number of jumps.

Input Format

A single line of four space-separated integers denoting the respective values of , , , and .


Output Format

Print YES if they can land on the same location at the same time; otherwise, print NO.

Note: The two kangaroos must land at the same location after making the same number of jumps.

Explanation:
The two kangaroos jump through the following sequence of locations:
![kangaroo](https://s3.amazonaws.com/hr-assets/0/1516005283-e74e76ff0c-kangaroo.png)

From the image, it is clear that the kangaroos meet at the same location (number  on the number line) after same number of jumps ( jumps), and we print YES.

#### Sample Input 0

```0 3 4 2```
<br></br>
#### Sample Output 0

```YES```

#### Sample Input 1

```0 2 5 3```
<br></br>
#### Sample Output 1

```NO```

## Solution:
### Language : Python
```python
#!/bin/python3

import sys

def kangaroo(x1, v1, x2, v2):
    # Complete this function
    global x1StPos
    x1StPos = x1
    global x2StPos
    x2StPos = x2
    x1AfterJump = 0
    x2AfterJump = 0
    v1Rate = v1
    v2Rate = v2
    global gotcha
    gotcha = None

    def jumps(x1Jump, x2Jump):
        global gotcha
        x1AfterJump = x1Jump + v1Rate
        x2AfterJump = x2Jump + v2Rate
        if x1AfterJump == x2AfterJump:
            # if the same co-ordinate is found
            gotcha = 'YES'
            return

        else:
            # If the starting location of first kangaroo is less than second's and
            # also the rate of the first's one is less than second one, than
            # its second one is never gonna catch up. Same as vice versa 
            # for the first one.
            if x1Jump < x2Jump and v1Rate < v2Rate:
                gotcha = 'NO'
                return
            elif x1Jump > x2Jump and v1Rate > v2Rate:
                gotcha = 'NO'
                return
            else:
                jumps(x1AfterJump, x2AfterJump)

    jumps(x1StPos, x2StPos)
    return gotcha


x1, v1, x2, v2 = input().strip().split(' ')
x1, v1, x2, v2 = [int(x1), int(v1), int(x2), int(v2)]
result = kangaroo(x1, v1, x2, v2)
print(result)
```
