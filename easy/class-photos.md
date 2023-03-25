---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Class Photos

{% hint style="info" %}
### Class Photos

It's photo day at the local school, and you're the photographer assigned to take class photos. The class that you'll be photographing has an even number of students, and all these students are wearing red or blue shirts. In fact, exactly half of the class is wearing red shirts, and the other half is wearing blue shirts. You're responsible for arranging the students in two rows before taking the photo. Each row should contain the same number of the students and should adhere to the following guidelines:

* All students wearing red shirts must be in the same row.
* All students wearing blue shirts must be in the same row.
* Each student in the back row must be strictly taller than the student directly in front of them in the front row.

You're given two input arrays: one containing the heights of all the students with red shirts and another one containing the heights of all the students with blue shirts. These arrays will always have the same length, and each height will be a positive integer. Write a function that returns whether or not a class photo that follows the stated guidelines can be taken.

Note: you can assume that each class has at least 2 students.

#### Sample Input

```
redShirtHeights = [5, 8, 1, 3, 4]
blueShirtHeights = [6, 9, 2, 4, 5]
```

#### Sample Output

```
true // Place all students with blue shirts in the back row.
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(nlog(n)) time | O(1) space
function classPhotos(redShirtHeights, blueShirtHeights) {
  redShirtHeights.sort((a, b) => b - a);
  blueShirtHeights.sort((a, b) => b - a);

  const shirtColorFirstRow = redShirtHeights[0] < blueShirtHeights[0] ? "RED" : "BLUE";
  for (let i = 0; i < redShirtHeights.length; i++) {
    const redHeight = redShirtHeights[i]
    const blueHeight = blueShirtHeights[i];
    if (shirtColorFirstRow === 'RED') {
      if (redHeight >= blueHeight) return false;
    } else if (blueHeight >= redHeight) return false
  }
  return true;
}

// Do not edit the line below.
exports.classPhotos = classPhotos;

```
{% endcode %}
{% endtab %}
{% endtabs %}

