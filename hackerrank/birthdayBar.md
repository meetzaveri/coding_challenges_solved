# Birthday Bar

Problem Link - https://www.hackerrank.com/challenges/the-birthday-bar/problem

## Solution
Language - Python

```python
def birthdayBar(n,s,d,m):
    global storePairs
    storePairs = []
    global sumStorage
    sumStorage = 0
    global tempPairStorage
    tempPairStorage = []
    sumStorage = 0

    for i in range(0,n):
        # print(' s[i+1]', s[i+1])
        if (i < n - 1):
            if(m == 1):
                if(s[i] == d):
                    storePairs.append(s[i])

            elif(m == 2):
                if(s[i] + s[i+1] == d):
                    temp = [s[i] , s[i+1]]
                    storePairs.append(temp)
            elif(m == 3):
                if (s[i] + s[i + 1] + s[i + 2] == d):
                    temp = [s[i], s[i + 1],s[i + 2]]
                    storePairs.append(temp)
        else:
            if(i == n - 1):
                if(len(storePairs) == 0):
                    storePairs.append(0)

        # for j in range(0,m):
        #     if(j == m - 1):
        #         print('sumStorage ',sumStorage)
        #         sumStorage = sumStorage + s[i]
        #         tempPairStorage.append(s[i])
        #         if(sumStorage == d):
        #             print('Here???')
        #             storePairs.append(tempPairStorage)
        #
        #     else:
        #         sumStorage = sumStorage + s[i]
        #         tempPairStorage.append(s[i])

    print('storePair ',storePairs)


birthdayBar(5 ,[1, 1, 1, 1, 1], 3, 3)
```
