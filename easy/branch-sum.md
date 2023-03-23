---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Branch sum

{% hint style="info" %}
### Find Closest Value in BTS

Write a function that takes in a Binary Search Tree (BST) and a target integer value and returns the closest value to that target value contained in the BST.

You can assume that there will only be one closest value.

Each BST node has an integer value, a left child node, and a right child node. A node is said to be a valid BST node if and only if it satisfies the BST property: its value is strictly greater than the values of every node to its left; its value is less than or equal to the values of every node to its right; and its children nodes are either valid BST nodes themselves or None / null.

#### Sample Input

```
tree =   10
       /     \
      5      15
    /   \   /   \
   2     5 13   22
 /           \
1            14
target = 12
```

#### Sample Output

```
13
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// This is the class of the input root.
// Do not edit it.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

// O(n) time | O(n) space - where n is number of node
function branchSums(root) {
  const sums = [];
  branchSumHelper(root, 0, sums);
  return sums;
}

function branchSumHelper(node, runningSum, sums) {
  if (!node) return;
  const newRunningSum = runningSum + node.value;
  // No more left or right node
  if (!node.left && !node.right) {
    sums.push(newRunningSum);
    return;
  }
  branchSumHelper(node.left, newRunningSum, sums);
  branchSumHelper(node.right, newRunningSum, sums);
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.branchSums = branchSums;

```
{% endcode %}
{% endtab %}
{% endtabs %}

