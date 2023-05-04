# 649. Dota2 Senate

## Approach:
 - We will use a two queue approach.
 - Recall, each senator has a position to exercise their right.
 - The ones to the left have an earlier turn than the ones to the right.
 - rad is queue that holds all positions of active senators in "Radiant"
 - dir is queue that holds all positions of active senators in "Dire".
 - Active being that they still have the right to vote.
 - Our queue will be ordered so that the senators with earlier voting power come first (to the left of the queue).
 - To goal is to have the earliest senator of each queue fight each other to see who gets to eliminate the other depending on their position.
 - Obviously, the one with the earlier position will win.
 - The loser is removed from the queue since they are no longer active.
 - The winner will go to the end of the queue for the next round.
 - We keep doing this until one queue is empty which means there are no more senators on the team.

## Python code:
```shell

```
