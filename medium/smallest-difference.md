---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Smallest Difference

{% hint style="info" %}
### Smallest Difference

Write a function that takes in two non-empty arrays of integers, finds the pair of numbers (one from each array) whose absolute difference is closest to zero, and returns an array containing these two numbers, with the number from the first array in the first position.

Note that the absolute difference of two integers is the distance between them on the real number line. For example, the absolute difference of -5 and 5 is 10, and the absolute difference of -5 and -4 is 1.

You can assume that there will only be one pair of numbers with the smallest difference.

#### Sample Input

```
arrayOne = [-1, 5, 10, 20, 28, 3]
arrayTwo = [26, 134, 135, 15, 17]
```

#### Sample Output

```
[28, 26]
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(nlog(n) + mlog(m)) time | O(1) space
function smallestDifference(arrayOne, arrayTwo) {
  arrayOne.sort((a, b) => a - b);
  arrayTwo.sort((a, b) => a - b);
  let indexOne = 0;
  let indexTwo = 0;
  let smallest = Infinity;
  let current = Infinity;
  let smallestPair = [];
  while (indexOne < arrayOne.length && indexTwo < arrayTwo.length) {
    let firstNum = arrayOne[indexOne];
    let secondNum = arrayTwo[indexTwo];
    if (firstNum < secondNum) {
      current = secondNum - firstNum;
      indexOne++;
    } else if (firstNum > secondNum) {
      current = firstNum - secondNum;
      indexTwo++;
    } else {
      return  [firstNum, secondNum]
    }
    if (smallest > current) {
      smallest = current;
      smallestPair = [firstNum, secondNum]
    }
  }
  return smallestPair
}

// Do not edit the line below.
exports.smallestDifference = smallestDifference;

```
{% endcode %}
{% endtab %}
{% endtabs %}

