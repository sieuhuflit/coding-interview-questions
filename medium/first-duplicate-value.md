---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# First Duplicate Value

{% hint style="info" %}
### First Duplicate Value

First Duplicate Value

Given an array of integers between 1 and n, inclusive, where n is the length of the array, write a function that returns the first integer that appears more than once (when the array is read from left to right).

In other words, out of all the integers that might occur more than once in the input array, your function should return the one whose first duplicate value has the minimum index.

If no integer appears more than once, your function should return -1.

Note that you're allowed to mutate the input array.

#### Sample Input #1

```
array = [2, 1, 5, 2, 3, 3, 4]
```

#### Sample Output #1

```
2 // 2 is the first integer that appears more than once.
// 3 also appears more than once, but the second 3 appears after the second 2.

```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(1) space - where n is the length of the input array
function firstDuplicateValue(array) {
  for (const value of array) {
    const absValue = Math.abs(value);
    if (array[absValue - 1] < 0) return absValue;
    array[absValue - 1] *= -1;
  }
  return -1;
}

// Do not edit the line below.
exports.firstDuplicateValue = firstDuplicateValue;

```
{% endcode %}
{% endtab %}

{% tab title="Solution 2" %}
```javascript
// O(n) time | O(n) space
function arrayOfProducts(array) {
  const products = new Array(array.length).fill(1); 
  const leftProducts = new Array(array.length).fill(1);
  const rightProducts = new Array(array.length).fill(1);

  let leftRunningProduct = 1;
  for (let i = 0; i < array.length; i++) {
    leftProducts[i] = leftRunningProduct;
    leftRunningProduct *= array[i];
  }

  let rightRunningProduct = 1;
  for (let i = array.length - 1; i > -1; i--) {
    rightProducts[i] = rightRunningProduct;
    rightRunningProduct *= array[i];
  }

  for (let i = 0; i < array.length; i++) {
    products[i] = leftProducts[i] * rightProducts[i]
  }
  return products;
}

// Do not edit the line below.
exports.arrayOfProducts = arrayOfProducts;

```
{% endtab %}

{% tab title="Solution 3" %}
```javascript
// O(n) time | O(n) space
function arrayOfProducts(array) {
  const products = new Array(array.length).fill(1);

  let leftRunningProduct = 1;
  for (let i = 0; i < array.length; i++) {
    products[i] = leftRunningProduct;
    leftRunningProduct *= array[i];
  }
  let rightRunningProduct = 1;
  for (let i = array.length - 1; i > -1; i--) {
    products[i] *= rightRunningProduct;
    rightRunningProduct *= array[i];
  }
  return products;
}

// Do not edit the line below.
exports.arrayOfProducts = arrayOfProducts;

```
{% endtab %}
{% endtabs %}

