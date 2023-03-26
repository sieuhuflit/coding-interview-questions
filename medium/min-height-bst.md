---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Min Height BST

{% hint style="info" %}
### Min Height BST

Write a function that takes in a non-empty sorted array of distinct integers, constructs a BST from the integers, and returns the root of the BST.

The function should minimize the height of the BST.

You've been provided with a BST class that you'll have to use to construct the BST.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

A BST is valid if and only if all of its nodes are valid BST nodes.

Note that the BST class already has an insert method which you can use if you want.

#### Sample Input

```
array = [1, 2, 5, 7, 10, 13, 14, 15, 22]
```

#### Sample Output

```
         10
       /     \
      2      14
    /   \   /   \
   1     5 13   15
          \       \
           7      22
// This is one example of a BST with min height
// that you could create from the input array.
// You could create other BSTs with min height
// from the same array; for example:
         10
       /     \
      5      15
    /   \   /   \
   2     7 13   22
 /           \
1            14
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(nlog(n)) time | O(n) space
function minHeightBst(array) {
  return minHeightBstHelper(array, null, 0, array.length - 1);
}

function minHeightBstHelper(array, bst, startIndex, endIndex) {
  if (endIndex < startIndex) return;
  const midIndex = Math.floor((startIndex + endIndex) / 2);
  const valueToAdd = array[midIndex];
  if(bst === null) {
    bst = new Bst(valueToAdd);
  } else {
    bst.insert(valueToAdd)
  }
  minHeightBstHelper(array, bst, startIndex, midIndex - 1);
  minHeightBstHelper(array, bst, startIndex + 1, endIndex);
  return bst;
}

class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    if (value < this.value) {
      if (this.left === null) {
        this.left = new BST(value);
      } else {
        this.left.insert(value);
      }
    } else {
      if (this.right === null) {
        this.right = new BST(value);
      } else {
        this.right.insert(value);
      }
    }
  }
}

// Do not edit the line below.
exports.minHeightBst = minHeightBst;

```
{% endcode %}
{% endtab %}

{% tab title="Solution 2" %}
```javascript
// O(nlog(n)) time | O(n) space
function minHeightBst(array) {
  return minHeightBstHelper(array, null, 0, array.length - 1);
}

function minHeightBstHelper(array, bst, startIndex, endIndex) {
  if (endIndex < startIndex) return;
  const midIndex = Math.floor((startIndex + endIndex) / 2);
  const newBstNode = new BST(array[midIndex]);
  if (bst === null) {
    bst = newBstNode;
  } else {
    if (array[midIndex] < bst.value) {
      bst.left = newBstNode;
      bst = bst.left;
    } else {
      bst.right = newBstNode;
      bst = bst.right;
    }
  }
  minHeightBstHelper(array, bst, startIndex, midIndex - 1);
  minHeightBstHelper(array, bst, midIndex + 1, endIndex);
  return bst;
}

class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    if (value < this.value) {
      if (this.left === null) {
        this.left = new BST(value);
      } else {
        this.left.insert(value);
      }
    } else {
      if (this.right === null) {
        this.right = new BST(value);
      } else {
        this.right.insert(value);
      }
    }
  }
}

// Do not edit the line below.
exports.minHeightBst = minHeightBst;

```
{% endtab %}

{% tab title="Solution 3" %}
```javascript
// O(nlog(n)) time | O(n) space
function minHeightBst(array) {
  return minHeightBstHelper(array, 0, array.length - 1);
}

function minHeightBstHelper(array, startIndex, endIndex) {
  if (endIndex < startIndex) return null;
  const midIndex = Math.floor((startIndex + endIndex) / 2);
  const bst = new BST(array[midIndex]);
  bst.left = minHeightBstHelper(array, startIndex, midIndex - 1);
  bst.right = minHeightBstHelper(array, midIndex + 1, endIndex);
  return bst;
}

class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    if (value < this.value) {
      if (this.left === null) {
        this.left = new BST(value);
      } else {
        this.left.insert(value);
      }
    } else {
      if (this.right === null) {
        this.right = new BST(value);
      } else {
        this.right.insert(value);
      }
    }
  }
}

// Do not edit the line below.
exports.minHeightBst = minHeightBst;

```
{% endtab %}
{% endtabs %}

