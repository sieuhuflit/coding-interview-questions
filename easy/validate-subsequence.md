---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Validate Subsequence

{% hint style="info" %}
### Validate Subsequence

Given two non-empty arrays of integers, write a function that determines whether the second array is a subsequence of the first one.

A subsequence of an array is a set of numbers that aren't necessarily adjacent in the array but that are in the same order as they appear in the array. For instance, the numbers \[1, 3, 4] form a subsequence of the array \[1, 2, 3, 4], and so do the numbers \[2, 4]. Note that a single number in an array and the array itself are both valid subsequences of the array.

#### Sample Input

```
array = [5, 1, 22, 25, 6, -1, 8, 10]
sequence = [1, 6, -1, 10]
```

#### Sample Output

```
true
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

