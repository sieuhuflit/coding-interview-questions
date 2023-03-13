---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Tournament Winner

{% hint style="info" %}
### Tournament Winner

There's an algorithms tournament taking place in which teams of programmers compete against each other to solve algorithmic problems as fast as possible. Teams compete in a round robin, where each team faces off against all other teams. Only two teams compete against each other at a time, and for each competition, one team is designated the home team, while the other team is the away team. In each competition there's always one winner and one loser; there are no ties. A team receives 3 points if it wins and 0 points if it loses. The winner of the tournament is the team that receives the most amount of points.

Given an array of pairs representing the teams that have competed against each other and an array containing the results of each competition, write a function that returns the winner of the tournament. The input arrays are named competitions and results, respectively. The competitions array has elements in the form of \[homeTeam, awayTeam], where each team is a string of at most 30 characters representing the name of the team. The results array contains information about the winner of each corresponding competition in the competitions array. Specifically, results\[i] denotes the winner of competitions\[i], where a 1 in the results array means that the home team in the corresponding competition won and a 0 means that the away team won.

It's guaranteed that exactly one team will win the tournament and that each team will compete against all other teams exactly once. It's also guaranteed that the tournament will always have at least two teams.

#### Sample Input

```
competitions = [
  ["HTML", "C#"],
  ["C#", "Python"],
  ["Python", "HTML"],
]
results = [0, 0, 1]
```

#### Sample Output

```
"Python"
// C# beats HTML, Python Beats C#, and Python Beats HTML.
// HTML - 0 points 
// C# -  3 points
// Python -  6 points
```
{% endhint %}

{% tabs %}
{% tab title="Solution 1" %}
{% code lineNumbers="true" %}
```javascript
// O(n) time | O(k) space
// where n is number of competitions
// k is number of teams
function tournamentWinner(competitions, results) {
  let currentBestTeam = '';
  const scores = { [currentBestTeam]: 0 };
  for (let i = 0; i < competitions.length; i++) {
    const result = results[i];
    const [homeTeam, awayTeam] = competitions[i];
    const winningTeam = result === 1 ? homeTeam : awayTeam;
    updateScores(winningTeam, 3, scores);
    if (scores[winningTeam] > scores[currentBestTeam]) {
      currentBestTeam = winningTeam
    }
  }
  return currentBestTeam;
}

function updateScores(team, points, scores) {
  if (!(team in scores)) scores[team] = 0;
  scores[team] += points;
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

