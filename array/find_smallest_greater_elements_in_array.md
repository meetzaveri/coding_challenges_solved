Smallest greater elements in whole array
An array is given of n length, and we need to calculate the next greater element for each element in given array. If next greater element is not available in given array then we need to fill ‘_’ at that index place.

Examples:

```
Input :  6 3 9 8 10 2 1 15 7 
Output : 7 6 10 9 15 3 2 _ 8
Here every element of array has next greater 
element but at index 7,
15 is the greatest element of given array
and no other element is greater from 15 
so at the index of 15 we fill with '_' .

Input  : 13 6 7 12
Output : _ 7 12 13
Here, at index 0, 13 is the greatest 
value in given array and no other 
array element is greater from 13 so
at index 0 we fill '_'.
```

How I solved this in -

### Language - Javascript

```js
var arr = [6, 3, 9, 8, 10, 2, 1, 15, 7 ];
var finalArray = [];

function takeOutNextLargest(arr){
  var temp = [];
  for (var i = 0; i < arr.length; i++) {
    for (var j = 0; j < arr.length; j++) {
      if(arr[i] < arr[j]){
        temp.push(arr[j]);
      }
      if(j == 8){
        if(Math.max.apply(Math,arr) === arr[i]){
          finalArray.push('_');
        }
        else {
          var smallest = Math.min.apply(Math,temp);
          finalArray.push(smallest);
          temp = [];
        }
      }
    }
  }
  return finalArray;
}

takeOutNextLargest(arr);

```
