---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# BST Traversal

{% hint style="info" %}
### BST Traversal

Write three functions that take in a Binary Search Tree (BST) and an empty array, traverse the BST, add its nodes' values to the input array, and return that array. The three functions should traverse the BST using the in-order, pre-order, and post-order tree-traversal techniques, respectively.

If you're unfamiliar with tree-traversal techniques, we recommend watching the Conceptual Overview section of this question's video explanation before starting to code.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

#### Sample Input

```
tree =   10
       /     \
      5      15
    /   \       \
   2     5       22
 /
1
array = []
```

#### Sample Output

```
inOrderTraverse: [1, 2, 5, 5, 10, 15, 22] // where the array is the input array
preOrderTraverse: [10, 5, 2, 1, 5, 15, 22] // where the array is the input array
postOrderTraverse: [1, 2, 5, 5, 22, 15, 10] // where the array is the input array
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(n) space
function inOrderTraverse(tree, array) {
  if (tree !== null) {
    inOrderTraverse(tree.left, array);
    array.push(tree.value);
    inOrderTraverse(tree.right, array);
  }
  return array;
}

// O(n) time | O(n) space
function preOrderTraverse(tree, array) {
  if (tree !== null) {
    array.push(tree.value);
    preOrderTraverse(tree.left, array);
    preOrderTraverse(tree.right, array);
  }
  return array;
}

// O(n) time | O(n) space
function postOrderTraverse(tree, array) {
  if (tree !== null) {
    postOrderTraverse(tree.left, array);
    postOrderTraverse(tree.right, array);
    array.push(tree.value);
  }
  return array;
}

exports.inOrderTraverse = inOrderTraverse;
exports.preOrderTraverse = preOrderTraverse;
exports.postOrderTraverse = postOrderTraverse;

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

