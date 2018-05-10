## Problem

Maria plays college basketball and wants to go pro. Each season she maintains a record of her play. She tabulates the number of times she breaks her season record for most points and least points in a game. Points scored in the first game establish her record for the season, and she begins counting from there.

For example, assume her scores for the season are represented in the array . Scores are in the same order as the games played. She would tabulate her results as follows:

            Count
Game  Score  Minimum  Maximum   Min Max
 0      12     12       12       0   0
 1      24     12       24       0   1
 2      10     10       24       1   1
 3      24     10       24       1   1
Given Maria's array of  for a season of  games, find and print the number of times she breaks her records for most and least points scored during the season.

Input Format

The first line contains an integer , the number of games. 
The second line contains  space-separated integers describing the respective values of .

Constraints

Output Format

Print two space-seperated integers describing the respective numbers of times her best (highest) score increased and her worst (lowest) score decreased.

Sample Input 0

9
10 5 20 20 4 5 2 25 1
Sample Output 0

2 4
Explanation 0

The diagram below depicts the number of times Maria broke her best and worst records throughout the season:

image

She broke her best record twice (after games  and ) and her worst record four times (after games , , , and ), so we print 2 4 as our answer. Note that she did not break her record for best score during game , as her score during that game was not strictly greater than her best record at the time.

Problem Link - https://www.hackerrank.com/challenges/breaking-best-and-worst-records/problem

## Solution 
Language - Python

```python
def breakingRecords(score):
    #
    # Write your code here.
    #
    global highestScore
    global lowestScore
    global scoreIncreasedTimes
    global scoreDecreasedTimes
    highestScore = 0
    lowestScore = 0
    scoreIncreasedTimes = 0
    scoreDecreasedTimes = 0

    for i in range(0, len(score)):

        # if first element, then set highest score and lowest score now for the first element
        if (i == 0):
            highestScore = score[i]
            lowestScore = score[i]
        else:
            if score[i] > highestScore:
                highestScore = score[i]
                scoreIncreasedTimes += 1
            elif score[i] < lowestScore:
                lowestScore = score[i]
                scoreDecreasedTimes += 1
            else:
                print

        # if the length of the array is 1, then there is only possibility that it's highest and lowest counter is only 1
        if (len(score) == 1):
            scoreIncreasedTimes += 1
            scoreDecreasedTimes += 1

    return scoreIncreasedTimes,scoreDecreasedTimes

breakingRecords([10, 5, 20, 20, 4, 5, 2, 25, 1])


```
