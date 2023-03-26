---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Reconstruct BST

{% hint style="info" %}
### Reconstruct BST

The pre-order traversal of a Binary Tree is a traversal technique that starts at the tree's root node and visits nodes in the following order:

1. Current node
2. Left subtree
3. Right subtree

Given a non-empty array of integers representing the pre-order traversal of a Binary Search Tree (BST), write a function that creates the relevant BST and returns its root node.

The input array will contain the values of BST nodes in the order in which these nodes would be visited with a pre-order traversal.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

#### Sample Input

```
preOrderTraversalValues = [10, 4, 2, 1, 5, 17, 19, 18]
```

#### Sample Output

```
        10 
      /    \
     4      17
   /   \      \
  2     5     19
 /           /
1           18 
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// This is an input class. Do not edit.
class BST {
  constructor(value, left = null, right = null) {
    this.value = value;
    this.left = left;
    this.right = right;
  }
}

// O(n^2) time | O(n) space
function reconstructBst(preOrderTraversalValues) {
  if(preOrderTraversalValues.length === 0) return null;
  
  const currentValue = preOrderTraversalValues[0];
  let rightSubtreeRootIndex = preOrderTraversalValues.length;

  for (let i = 1; i < preOrderTraversalValues.length; i++) {
    const value = preOrderTraversalValues[i];
    if (value >= currentValue) {
      rightSubtreeRootIndex = i;
      break;
    }
  }
  const leftSubtree = reconstructBst(preOrderTraversalValues.slice(1, rightSubtreeRootIndex));
  const rightSubtree = reconstructBst(preOrderTraversalValues.slice(rightSubtreeRootIndex));
  return new BST(currentValue, leftSubtree, rightSubtree);
}

// Do not edit the lines below.
exports.BST = BST;
exports.reconstructBst = reconstructBst;

```
{% endcode %}
{% endtab %}

{% tab title="Solution 2" %}
```javascript
// This is an input class. Do not edit.
class BST {
  constructor(value, left = null, right = null) {
    this.value = value;
    this.left = left;
    this.right = right;
  }
}

class TreeInfo {
  constructor(rootIndex) {
    this.rootIndex = rootIndex;
  }
}

// O(n) time | O(n) space
function reconstructBst(preOrderTraversalValues) {
  const treeInfo = new TreeInfo(0);
  return reconstructBstHelper(-Infinity, Infinity, preOrderTraversalValues, treeInfo);
}

function reconstructBstHelper(lowerBound, upperBound, preOrderTraversalValues, currentSubtreeInfo) {
  if (currentSubtreeInfo.rootIndex === preOrderTraversalValues.length) return null;

  const rootValue = preOrderTraversalValues[currentSubtreeInfo.rootIndex];
  if (rootValue < lowerBound || rootValue >= upperBound) return null;

  currentSubtreeInfo.rootIndex++;
  const leftSubtree = reconstructBstHelper(lowerBound, rootValue, preOrderTraversalValues, currentSubtreeInfo);
  const rightSubtree = reconstructBstHelper(rootValue, upperBound, preOrderTraversalValues, currentSubtreeInfo);
  return new BST(rootValue, leftSubtree, rightSubtree)
}

// Do not edit the lines below.
exports.BST = BST;
exports.reconstructBst = reconstructBst;

```
{% endtab %}
{% endtabs %}

