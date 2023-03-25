---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Move Element To End

{% hint style="info" %}
### Move Element To End

You're given an array of integers and an integer. Write a function that moves all instances of that integer in the array to the end of the array and returns the array.

The function should perform this in place (i.e., it should mutate the input array) and doesn't need to maintain the order of the other integers.

#### Sample Input

```
array = [2, 1, 2, 2, 2, 3, 4, 2]
toMove = 2
```

#### Sample Output

```
[1, 3, 4, 2, 2, 2, 2, 2] // the numbers 1, 3, and 4 could be ordered differently
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(1) space
function moveElementToEnd(array, toMove) {
  let i = 0;
  let j = array.length - 1;
  while (i < j) {
    while (i < j && array[j] === toMove) j--;
    if (array[i] === toMove) swap(i, j, array);
    i++;
  }
  return array;
}

function swap(i, j, array) {
  const temp = array[j];
  array[j] = array[i];
  array[i] = temp;
}

// Do not edit the line below.
exports.moveElementToEnd = moveElementToEnd;

```
{% endcode %}
{% endtab %}
{% endtabs %}

