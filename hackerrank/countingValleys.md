### Counting valleys
Description - https://www.hackerrank.com/challenges/counting-valleys/problem

```js
function countingValleys(n, s) {
  console.log("His hike", s);

  function getUnitChange(stepDir) {
    switch (stepDir) {
      case "U":
        return 1;
      case "D":
        return -1;
      default:
        break;
    }
  }

  const stepsTraversed = [];
  let valleysToCount = 0;
  let pointToReach = 0;
  const splitArr = s.split("");
  console.log("Splitted Arr", splitArr);

  splitArr.forEach((item, index) => {
    pointToReach = pointToReach + getUnitChange(item);
    if (pointToReach === 0 && item === "U") {
      valleysToCount = valleysToCount + 1;
    }
  });

  console.log("valleysToCount", valleysToCount);
  return valleysToCount;
}

```
