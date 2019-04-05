## Create a game interface

Noy you have two buttons: one button picks three random fruit, tells you if you won or lost, and updates the score. The second button starts the game again by resetting the score back to 100.

Design a game interface so that the two buttons are next to each other.

--- task ---
Put the `Button`s into a list, `{}`, so they are separated by a `,`. Then put the list inside the `Row` function. `Row` takes a list of items and puts them on one line.

At the moment, the three `Dynamic` variables (`roll`, `result`, `score`) are in three separate output cells. Put `roll`, `result`, and `score` into another list, so they are separated by `,`. Put that list inside the `Column` function. `Column` takes a list of items and puts them in a column. Doing this puts all three results into the same output cell.

```
roll = RandomChoice[fruits, 3];
result = Text["Click Roll Again to Start"];
score = 100;
Row[{
Button["Roll Again",
roll = RandomChoice[fruits, 3];
result =
Which[
Max[Counts[roll]] == 3, score += 10; Text[ "Winner!"],
 Max[Counts[roll]] == 2, Text[ "So Close!"],
 Max[Counts[roll]] == 1, score -= 10; Text[ "Loser!"]]
 ],
 Button["Start Again", score = 100]
 }]
Column[{Dynamic[Grid[{roll}, Frame -> All, FrameStyle -> Thick]],
Dynamic[result],
Dynamic[score]}]
```
--- /task ---

Notice that the column is inside the row, which means the column of three items is treated as one item to put in the row.
