---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Sorted Squared Array

{% hint style="info" %}
### Sorted Squared Array

Write a function that takes in a non-empty array of integers that are sorted in ascending order and returns a new array of the same length with the squares of the original integers also sorted in ascending order.

#### Sample Input

```
array = [1, 2, 3, 5, 6, 8, 9]
```

#### Sample Output

```
[1, 4, 9, 25, 36, 64, 81]
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(nlogn) time | O(n) space
function sortedSquaredArray(array) {
  const sortedSquares = new Array(array.length).fill(0);

  for (let i = 0; i < array.length; i++) {
    const element = array[i];
    sortedSquares[i] = element * element;
  }
  sortedSquaredArray.sort((a, b) => a - b)
  return sortedSquares;
}

```
{% endcode %}
{% endtab %}

{% tab title="Solution 2" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(n) space
function sortedSquaredArray(array) {
  const sortedSquared = new Array(array.length).fill(0);
  let start = 0;
  let end = array.length - 1;
  for (let i = array.length - 1; i >= 0; i--) {
    const startValue = array[start];
    const endValue = array[end];
    if (Math.abs(startValue) < Math.abs(endValue)) {
      sortedSquared[i] = endValue * endValue
      end--;
    } else {
      sortedSquared[i] = startValue * startValue
      start++;
    }
  }
  return sortedSquared;
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

