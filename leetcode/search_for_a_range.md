
# Leetcode Challenge
Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return `[-1, -1]`.

For example,
Given `[5, 7, 7, 8, 8, 10]` and target value 8,
return `[3, 4]`.

```js
var searchRange = function(nums, target) {
    var takeIndices = [];
    nums.forEach((item,index) => {
        console.log('Item',item);
        if(target === item){
            console.log('Matched');
            takeIndices.push(index);
        }
        
    })
    console.log('Take Indices',takeIndices);
    if(takeIndices.length < 1){
            return [-1,-1];
    }
    else{
        return [takeIndices[0],takeIndices[takeIndices.length - 1 ]];
    }
    

    
};
```
