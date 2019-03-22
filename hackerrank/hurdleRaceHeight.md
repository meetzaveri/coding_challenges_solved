## Source 
https://www.hackerrank.com/challenges/the-hurdle-race/problem

Sample Input 0
```
5 4
1 6 3 5 2
```

Sample Output 0
```
2
```


## Solution (in javascript)

```js

function hurdleRace(k, height) {
    let minNoOfDose = 0;
    if (height.length > 0) {
        height.forEach((ht, i) => { 
            if (ht > k) { 
                if (minNoOfDose < ht) {
                    minNoOfDose = ht;
                 }
            }
        })
        console.log('minNoOfDose', minNoOfDose);
        if (minNoOfDose == 0) { 
            return 0
         }
        const requiredDose = minNoOfDose - k;
        return requiredDose
    } else { 
        return 0
    }
}
```
