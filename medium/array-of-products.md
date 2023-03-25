---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Array Of Products

{% hint style="info" %}
### Array Of Products

Write a function that takes in a non-empty array of integers and returns an array of the same length, where each element in the output array is equal to the product of every other number in the input array.

In other words, the value at output\[i] is equal to the product of every number in the input array other than input\[i].

Note that you're expected to solve this problem without using division.

#### Sample Input

```
array = [5, 1, 4, 2]
```

#### Sample Output

```
[8, 40, 10, 20]
// 8 is equal to 1 x 4 x 2
// 40 is equal to 5 x 4 x 2
// 10 is equal to 5 x 1 x 2
// 20 is equal to 5 x 1 x 4
```

\

{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n^2) time | O(n) space
function arrayOfProducts(array) {
  const result = [];
  for (let i = 0; i < array.length; i++) {
    let value = 1;
    for (let j = 0; j < array.length; j++) {
      if (i === j) continue;
      value *= array[j]
    }
    result.push(value)
  }
  return result;
}

// Do not edit the line below.
exports.arrayOfProducts = arrayOfProducts;

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

