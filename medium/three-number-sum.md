---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Three Number Sum

{% hint style="info" %}
### Three Number Sum

Write a function that takes in a non-empty array of distinct integers and an integer representing a target sum. The function should find all triplets in the array that sum up to the target sum and return a two-dimensional array of all these triplets. The numbers in each triplet should be ordered in ascending order, and the triplets themselves should be ordered in ascending order with respect to the numbers they hold.

If no three numbers sum up to the target sum, the function should return an empty array.

#### Sample Input

```
array = [12, 3, 1, 2, -6, 5, -8, 6]
targetSum = 0
```

#### Sample Output

```
[[-8, 2, 6], [-8, 3, 5], [-6, 1, 5]]
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n^2) time | O(n) space
function threeNumberSum(array, targetSum) {
  array.sort((a, b) => a - b);
  const triplets = [];
  for (let i = 0; i < array.length - 2; i++) {
    let left = i + 1;
    let right = array.length - 1;
    while (left < right) {
      const currentSum = array[i] + array[left] + array[right];
      if (currentSum === targetSum) {
        triplets.push([array[i], array[left], array[right]])
        left++;
        right--;
      } else if (currentSum < targetSum) {
        left++;
      } else if (currentSum > targetSum) {
        right--;
      }
    }
  }
  console.log(triplets)
  return triplets
}

// Do not edit the line below.
exports.threeNumberSum = threeNumberSum;

```
{% endcode %}
{% endtab %}
{% endtabs %}

