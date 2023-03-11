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
// O(n) time | O(1) space
function isValidSubsequence(array, sequence) {
  let index = 0;
  let seqIndex = 0;
  while (index < array.length && seqIndex < sequence.length) {
    if (array[index] === sequence[seqIndex]) seqIndex++;
    index++;
  }
  return seqIndex === sequence.length;
}

```
{% endcode %}
{% endtab %}

{% tab title="Solution 2" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(1) space
function isValidSubsequence(array, sequence) {
  let seqIndex = 0;
  for (const value of array) {
    if (seqIndex === sequence.length) break;
    if (sequence[seqIndex] === value) seqIndex++;
  }
  return seqIndex === sequence.length;
}

```
{% endcode %}
{% endtab %}
{% endtabs %}

